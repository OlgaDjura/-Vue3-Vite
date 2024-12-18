<template>
  <footer class="footer container">
        <div class="footer__inner">
        <FooterNavigation></FooterNavigation>
            <div class="footer__body">
                <div class="footer__contact">
                    <h2 class="footer__contact-title h4 puddle-bg">Contact us:</h2>
                    <address class="footer__contacts-body">
                        <p>Email: <a href="mailto:info@positivus.com">info@positivus.com</a></p>
                        <p>Phone: <a href="tel:5555678901"> 555-567-8901</a></p>
                        <p>Address: 1234 Main St <br>
                            Moonstone City, Stardust State 12345</p>
                    </address>
                </div>
                <form class="footer__subscribe-form subscribe-form">
                    <h2 class="visually-hidden"></h2>
                    <div class="subscribe-form__field field field--big-height field--dark-bg">
                        <label for="" class="field__label visually-hidden" name="subscribe-email">Email</label>
                        <input class="field__input"
                        id="subscribe-email"
                        name="email"
                        placeholder="Email"
                        type="email"
                        required
                        >
                        <span class="error" v-if="error">{{ error }}</span>
                    </div>
                    <ButtonMy variant="accent" @submit.prevent="validateForm" >Subscribe to news</ButtonMy>
                    <div v-if="successMessage" class="success-message">{{ successMessage }}</div>
                </form>
            </div>
            <div class="footer__extra">
                <p class="footer__copyright">
                    © <time datetime="2023">2023</time> Positivus. All Rights Reserved.
                </p>
                <a href="/" class="footer__privacy-policy-link">Privacy Policy</a>
            </div>

        </div>
    </footer>
</template>

<script>
import FooterNavigation from './FooterNavigation.vue';
import ButtonMy from './ButtonMy.vue';


export default {
  components: {
    FooterNavigation,
    ButtonMy,
  },
  data() {
    return {
      email: '',
      error: '',
      successMessage: ''
    };
  },
  methods: {
    validateForm() {
      this.error = '';
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

      if (!this.email) {
        this.error = 'Пожалуйста, укажите ваш email.';
        return;
      }

      if (!emailPattern.test(this.email)) {
        this.error = 'Пожалуйста, введите действительный адрес электронной почты.';
        return;
      }

      this.sendEmailToServer(this.email);
    },
    async sendEmailToServer(email) {
      try {
        const response = await fetch('https://example.com/subscribe', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
          },
          body: JSON.stringify({ email }),
        });

        if (response.ok) {
          this.successMessage = 'Вы успешно подписались!';
          this.email = '';
        } else {
          this.error = 'Произошла ошибка при подписке. Пожалуйста, попробуйте еще раз.';
        }
      } catch {
        this.error = 'Ошибка сети. Пожалуйста, попробуйте позже.';
      }
    }
  }
}
</script>

<style scoped lang="scss">
.footer {
    @include mobile {
        padding-inline: 0;
    }

    &__inner {
        padding: 55px 60px 50px;
        color: var(--color-light);
        background-color: var(--color-dark);

        @include mobile-above {
            border-radius: var(--border-radius-large) var(--border-radius-large) 0 0;;
        }

        @include mobile {
            display: flex;
            flex-direction: column;
            align-items: center;
            row-gap: 37px;
            padding: 50px var(--container-padding-x) 30px;
        }
    }

    &__navigation {
        display: flex;
        justify-content: space-between;
        align-items: center;
        column-gap: 30px;

        &:not(:last-child) {
            margin-bottom: 66px;
        }

        @include mobile {
            display: contents;

        }

        @include tablet {
            flex-direction: column;
            align-items: center;
            row-gap: 37px;
        }


    }

    &__menu {
        &-list {
            display: flex;
            align-items: center;
            column-gap: 40px;

            @include mobile {
                flex-direction: column;
                row-gap: 15px;
            }
        }


        &-link {
            display: inline-flex;
            align-items: center;
            height: 30px;
            text-decoration: underline;

            @include hover {
                color: var(--color-accent);
            }
        }
    }

    &__soc1als {
        @include mobile {
            order: 1;
        }
    }

    &__body {
        display: flex;
        justify-content: space-between;
        column-gap: 50px;

        @include mobile {
            flex-direction: column;
            align-items: center;
            row-gap: inherit;
        }

        @include mobile-above {
            &:not(:last-child) {
                margin-bottom: 50px;
                padding-bottom: 50px;
                border-bottom: 1px solid currentColor;
            }
        }

        @include mobile-s {
            width: 100%;
        }

    }

    &__contact-title {
        font-size: 20px;
        color: var(--color-dark);
        width: 130px;
    }

    &__contacts {
        display: flex;
        flex-direction: column;
        align-items: start;
        row-gap: 27px;

        @include mobile {
            align-items: center;
            text-align: center;
        }

        &-body {
            font-style: normal;

            p {
                --paragraphMarginBottom: 20px;
            }

            a {
                @include hover {
                    color: var(--color-accent);
                }
            }
        }
    }

    &__extra {
        display: flex;
        column-gap: 40px;

        @include mobile {
            order: 2;
            flex-direction: column;
            align-items: center;
            row-gap: 15px;
            width: 100%;
            padding-top: 37px;
            border-top: 1px solid currentColor;
        }
    }
    &__privacy-policy-link {
        text-decoration: underline;

        @include hover {
            color: var(--color-accent);
        }
    }

}
.soc1als {
    --color-dark: #191A23;
    --color-light: #FFFFFF;
    --color-accent: #B9FF66;
    &__list {
        display: flex;
        column-gap: 20px;
    }

    &__link {
        @include flex-center(true);
        @include square(30px);

        color: var(--color-dark);
        background-color: var(--color-light);
        border-radius: 50%;
        @include hover {
            background-color: var(--color-accent);
        }

        svg {
            width: 50%;
            height: 50%;
        }
    }
}
.subscribe-form {
  --color-dark-alt: #292A32;
  --border-radius: 14px;

    display: flex;
    column-gap: 20px;
    padding: 58px 40px;
    background-color: var(--color-dark-alt);
    border-radius: var(--border-radius);

    @include desktop {
        flex-direction: column;
        row-gap: 22px;
        width: 100%;
        max-width: 450px;
        padding: 30px;
    }
}
</style>
