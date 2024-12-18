<template>
  <header class="header">
    <div class="header__inner container">
      <a href="/" class="header__logo logo">
        <img src="../assets/images/Logo.svg" alt="positivus" width="220" height="36" loading="lazy">
      </a>
      <nav v-if="!isMobileMenuVisible" class="header__menu hidden-mobile">
        <ul class="header__menu-list">
          <li class="header__menu-item" v-for="item in menuItems" :key="item.text">
            <a :href="item.link" class="header__menu-link">{{ item.text }}</a>
          </li>
        </ul>
      </nav>
      <ButtonMy @click="handleClick" variant="transparent hidden-mobile">Request a
        quote</ButtonMy>
      <button class="header__burger-button burger-button visible-mobile" type="button" title="open navigation" @click="toggleMobileMenu"></button>
    </div>

    <MobileMenu :isVisible="isMobileMenuVisible" :menuItems="menuItems" @update:isVisible="isMobileMenuVisible = $event" />
  </header>
</template>

<script>
import ButtonMy from './ButtonMy.vue';
import MobileMenu from './MobileMenu.vue';
export default {
  components: {
    ButtonMy,
    MobileMenu,
  },
  data() {
    return {
      isMobileMenuVisible: false,
      menuItems: [
        { text: 'About us', link: '/' },
        { text: 'Services', link: '/' },
        { text: 'Use Cases', link: '/' },
        { text: 'Pricing', link: '/' },
        { text: 'Blog', link: '/' },
      ],
    };
  },
  methods: {
    toggleMobileMenu() {
      this.isMobileMenuVisible = !this.isMobileMenuVisible;
      console.log('вызвано', this.isMobileMenuVisible);
    },
  handleClick() {
    console.lof('clicked');
  },
}
}

</script>

<style scoped lang="scss">
.header {
    font-family: 'Space Grotesk', sans-serif;
    font-weight: 400;
    line-height: 1.28;
    color: #191A23;;
    background-color: #FFFFFF;
    padding-top: 60px;

    @include desktop {
        padding-top: 30px;
    }

    @include mobile {
        padding-top: 15px;
    }

    &__inner {
        display: flex;
        justify-content: space-between;
        align-items: center;
        column-gap: 40px;

        @include tablet {
            column-gap: 30px;
        }
    }

    &__logo {
        @include tablet {
            max-width: 120px;
        }

        @include mobile {
            max-width: 144px;
        }
    }

    &__menu {
        margin-left: auto;
        font-size: 20px;

        @include desktop {
            font-size: 18px;
        }

        @include tablet {
            font-size: 16px;
        }


        &-list {
            display: flex;
            align-items: center;
            column-gap: 40px;

            @include desktop {
                column-gap: 20px;
            }
        }

        &-link {
            position: relative;
            display: inline-flex;
            align-items: center;
            height: 48px;

            @include hover {
                &::after {
                    width: 100%;
                }
            }

            &::after {
                content: '';
                position: absolute;
                top: 100%;
                left: 50%;
                translate: -50%;
                width: 0;
                height: 2px;
                background-color: currentColor;
                transition-duration: inherit;
            }
        }
    }

    &__button {
        @include tablet {
        height: 48px;
        padding-inline: 18px;
        font-size: 16px;
    }
    }
  }
  .burger-button {
    @include reset-button;
    @include square(48px);


    position: relative;
    border-radius: var(--border-radius-small);

    @include hover {
        background-color: var(--color-accent);
    }

    &::after {
        @include abs-center;

        content: '';
        width: 50%;
        height: 2px;
        background-color: var(--color-dark);
        border-radius: 5px;
        box-shadow: 0 -8px, 0 8px;
    }
}

</style>
