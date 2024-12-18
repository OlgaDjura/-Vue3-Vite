<template>
  <dialog v-if="isVisible" class="mobile-overlay visible-mobile" :class="{ visible: isVisible}" id="mobileOverLay">
    <form class="mobile-overlay__close-button-wrapper" method="dialog">
      <button class="mobile-overlay__close-button cross-button" type="button" title="close navigation" @click="closeDialog"></button>
    </form>
    <div class="mobile-overlay__body">
      <ul class="mobile-overlay__list">
        <li class="mobile-overlay__item" v-for="item in menuItems" :key="item.text">
          <a :href="item.link" class="mobile-over__link">{{ item.text }}</a>
        </li>
      </ul>
    </div>
  </dialog>
</template>

<script>
export default {
  props: {
    isVisible: {
      type: Boolean,
      required: true,
    },
    menuItems: {
      type: Array,
      required: true,
    },
  },
  methods: {
    closeDialog() {
      this.$emit('update:isVisible', false);
    },
  },
};
</script>

<style scoped lang="scss">
.mobile-overlay {
  display: block;
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 14px 20px;
    border: none;
    z-index: 1000;

    &:modal {
        max-width: 100%;
        max-height: 100%;
    }

    &__close-button-wrapper {
        display: flex;
        justify-content: end;
    }

    &__list {
        @include flex-center;

        flex-direction: column;
        row-gap: 30px;
        min-height: 80vh;
    }
}
.cross-button {
    @include reset-button;
    @include square(48px);


    position: relative;
    border-radius: var(--border-radius-small);

    @include hover {
        background-color: var(--color-accent);
    }

    &::before, &::after {
        content: '';
        position: absolute;
        top: 50%;
        left: 7px;
        width: 70%;
        height: 2px;
        background-color: var(--color-dark);
        border-radius: 5px;
    }

    &::before {
        rotate: 45deg;
    }

    &::after {
        rotate: -45deg;
    }
}
</style>
