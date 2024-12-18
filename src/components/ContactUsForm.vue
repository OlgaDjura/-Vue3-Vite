<template>
  <section class="section container">
            <SectionHeader title="Contact Us" content="Connect with Us: Let's Discuss Your Digital Marketing Needs"></SectionHeader>
            <div class="section__body">
                <div class="contact-us">
                    <form action="" class="contact-us__form">
                        <fieldset class="contact-us__request-types radios">
                            <legend class="radios__title visually-hidden">Request type</legend>
                            <label class="radios__item radio">
                                <input type="radio" class="radio__input visually-hidden" name="request-type"
                                    value="Say Hi" checked>
                                <span class="radio__emulator"></span>
                                <span class="radio__label">Say Hi</span>
                            </label>

                            <label class="radios__item radio">
                                <input type="radio" class="radio__input visually-hidden" name="request-type"
                                    value="Get a Quote">
                                <span class="radio__emulator"></span>
                                <span class="radio__label">Get a Quote</span>
                            </label>
                        </fieldset>
                        <div class="contact-us__body">
                            <div class="contact-us__field field">
                                <label for="name" class="field__label">Name</label>
                                <input type="text" class="field__input" id="name" name="name" placeholder="Name">
                                <span class="error-message" id="name-error" v-if="errors.name">{{ errors.name }}</span>
                            </div>
                            <div class="contact-us__field field">
                                <label for="email" class="field__label">Email*</label>
                                <input type="email" class="field__input" id="email" name="email" placeholder="Email"
                                    required>
                                <span class="error-message" id="email-error" v-if="errors.email">{{ errors.email }}</span>
                            </div>
                            <div class="contact-us__field field">
                                <label for="message" class="field__label ">Message*</label>
                                <textarea type="text" class="field__input field__input--textarea" id="message"
                                    name="message" placeholder="Message" required>
                                </textarea>
                                <span class="error-message" id="message-error" v-if="errors.message">{{ errors.message }}</span>
                            </div>
                        </div>
                        <ButtonMy @click="submitForm">Send Message</ButtonMy>
                    </form>
                </div>
            </div>
        </section>
</template>

<script>
import SectionHeader from './SectionHeader.vue';
import ButtonMy from './ButtonMy.vue';
export default {
  components: {
    SectionHeader,
    ButtonMy,
  },
  data() {
    return {
      name: '',
      email: '',
      message: '',
      errors: {},
    };
  },
  methods: {
    validateForm() {
      this.errors = {};
      let isValid = true;

      if (!this.name) {
        this.errors.name = 'Имя обязательно!';
        isValid = false;
      }

      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if (!this.email) {
        this.errors.email = 'Email обязателен';
        isValid = false;
      } else if (!emailPattern.test(this.email)) {
        this.errors.email = 'Некорректный Email!';
        isValid = false;
      }

      if (!this.message) {
        this.errors.message = 'Сообщение обязательно!';
        isValid = false;
      }

      return isValid;
    },
    async submitForm() {
      if (!this.validateForm()) {
        return;
      }

      const formData = {
        name: this.name,
        email: this.email,
        message: this.message,
      };

      try {
        const response = await fetch('https:///api/contact', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify(formData),
        });

        if (!response.ok) {
          throw new Error('Серверная ошибка при отправке формы.');
        }
        this.name = '';
        this.email = '';
        this.message = '';
        alert('Сообщение отправлено успешно!');
      } catch (error) {
        console.error('Ошибка:', error);
        alert('Ошибка при отправке сообщения. Попробуйте еще раз.');
      }
    },
  },
}
</script>

<style scoped lang="scss">
.contact-us {
    position: relative;
    overflow-x: hidden;

    @include mobile-above {
        padding: 60px 100px 80px;
        background-color: var(--color-gray);
        border-radius: var(--border-radius);
    }

    &::after {
        --contactUsImageOffsetY: 62px;

        content: '';
        position: absolute;
        top: 50%;
        left: 100%;
        translate: -50% -50%;
        height: calc(100% - var(--contactUsImageOffsetY) * 2);
        aspect-ratio: 1;
        background: url(../assets/images/contact-us.svg) center/contain no-repeat;

        @include tablet {
            display: none;
        }
    }

    &__request-types,
    &__body {
        @include mobile {
            background-color: var(--color-gray);
        }
    }

    &__request-types {
        @include mobile {
            padding: 40px 52px 36px;
            border-radius: var(--border-radius-large) var(--border-radius-large) 0 0;
        }
    }

    &__form {
        display: flex;
        flex-direction: column;



        @include tablet-above {
            max-width: 556px;
        }

        @include mobile-above {
            row-gap: 40px;
        }
    }

    &__body {
        display: flex;
        flex-direction: column;
        row-gap: 25px;

        @include mobile {
            row-gap: 20px;
            margin-bottom: 30px;
            padding: 10px 30px 50px;
            border-radius: 0 0 var(--border-radius-large) var(--border-radius-large);
        }

    }
}

.radio {
    display: flex;
    align-items: center;
    column-gap: 14px;
    transition-duration: var(--transition-duration);

    @include hover {
        opacity: 0.6;
    }

    &__input {
        &:not(:checked) + .radio__emulator::after {
            opacity: 0;
            transition-duration: var(--transition-duration);
        }
    }

    &__emulator {
        @include flex-center;
        @include square(28px);

        position: relative;
        background-color: var(--color-light);
        border: var(--border);
        border-radius: 50%;

        &::after {
            @include abs-center;
            @include square(60%);

            content: '';
            background-color: var(--color-accent);
            border-radius: inherit;
        }
    }
}

.radios {
    display: flex;
    column-gap: 35px;
}
</style>
