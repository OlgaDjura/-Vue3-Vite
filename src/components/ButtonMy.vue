<template>
    <button :class="computedClass" @click="$emit('click')">
      <slot></slot>
      </button>
</template>

<script>
export default {
  props: {
    type: {
    type:  String,
    default: 'button'
    },
  variant: {
    type: String,
    default: 'primary'
  },
  },
  computed: {
      computedClass() {
        return `button button--${this.variant}`;
      },
  },
  methods: {
        handleClick(event) {
      if (!this.disabled) {
        this.$emit('click', event);
      }
  }
  }
}
</script>

<style scoped lang="scss">
.button {
    @include flex-center(true);

    height: 68px;

    padding-inline: 35px;
    font-size: 20px;
    color: #FFFFFF;
    background-color: #191A23;
    border: 1px solid rgb(25, 26, 35);
    border-radius: 14px;
    font-family: 'Space Grotesk', sans-serif;
    font-weight: 400px;

    @include hover {
        color: #191A23;
        background-color: #B9FF66;
    }

    &--transparent {
        color: #191A23;
        background-color: transparent;
    }

    &--accent {
        color: #191A23;
        background-color: #B9FF66;

        @include hover {
            color: #B9FF66;
            background-color: #191A23;
        }
    }

    &--hero {
      @include mobile {
            width: 100%;
            max-width: 390px;
            margin-inline: auto;
        }
    }

    &__burger-button {
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
}
</style>
