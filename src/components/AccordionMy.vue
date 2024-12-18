<template>
  <div :class="['process__accordion', { open: isOpen }]" @click="toggleAccordion">
    <summary class="process__accordion-header">
      <h3 class="process__accordion-title">{{ title }}</h3>
      <span class="process__accordion-indication" :style="{ transform: isOpen ? 'rotate(var(--indicatorVerticalRotate))' : 'rotate(90deg)' }"></span>
    </summary>
    <div class="process__accordion-body" v-show="isOpen">
      <p>{{ content }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
    content: {
      type: String,
      required: true,
    },
    open: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      isOpen: this.open,
    };
  },
  methods: {
    toggleAccordion() {
      this.isOpen = !this.isOpen;
    },
  },
};
</script>

<style scope lang="scss">
.process {
    --color-dark: #191A23;
    --color-accent: #B9FF66;
    --color-gray: #F3F3F3;
    --shadow: 0 5px 0 0 var(--color-dark);
    --border-radius-large: 45px;
    --transition-duration: 0.2s;
    --border: 1px solid rgb(25, 26, 35);

  &__accordion {
        --indicatorVerticalRotate: 90deg;
        padding: 40px;
        background-color: var(--color-gray);
        border: var(--border);
        border-radius: var(--border-radius-large);
        box-shadow: var(--shadow);
        transition-duration: var(--transition-duration) ;

        @include hover {
            background-color: var(--color-accent);
        }

        @include mobile {
            padding: 30px;

        }

        &.open {
            --indicatorVerticalRotate: 0deg;
            background-color: var(--color-accent);
        }

        &-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            column-gap: 50px;
            cursor: pointer;
            //user-select: none;

            @include mobile {
                column-gap: 28px;
            }
        }

        &-title {
            @include fluid-text(30, 18);
            display: flex;
            align-items: center;
            column-gap: 25px;
            column-gap: 33px;

            &::before {
                content: var(--counterContent);
                font-size: 2em;

                @include mobile {
                    font-size: 30px;
                }
            }
        }
        &-body {
            margin-top: 30px;
            padding-top: 30px;
            border-top: 1px solid black;

        }

        &-indication {
            @include flex-center;
            @include square(58px);

            flex-shrink: 0;
            position: relative;
            background-color: var(--color-gray);
            border: var(--border);
            border-radius: 50%;

            @include mobile {
                width: 30px;
            }

            &::before, &::after {
                @include abs-center;

                content: '';
                width: 45%;
                height: 10%;
                background-color: var(--color-dark);
            }
            &::after {
                rotate: var(--indicatorVerticalRotate);
                transition-duration: var(--transition-duration);
            }
        }
}
}
</style>
