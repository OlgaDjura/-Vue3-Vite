<template>
  <section class="section container">
    <SectionHeader title="Testimonials" content="Hear from Our Satisfied Clients: Read Our Testimonials to Learn More about Our Digital Marketing
                        Services"></SectionHeader>
    <div class="section__body">
      <div class="reviews">
        <div class="reviews__slider">
          <ul class="reviews__slider-list">
            <li v-for="(review, index) in visibleReviews" :key="index" class="reviews__slider-item">
              <blockquote class="review-card">
                <div class="review-card__body">
                  <p>{{ review.text }}</p>
                </div>
                <footer class="review-card__footer">
                  <cite class="review-card__name">{{ review.name }}</cite>
                  <cite class="review-card__company">{{ review.company }}</cite>
                </footer>
              </blockquote>
            </li>
          </ul>
        </div>
          <div class="reviews__actions">
            <button @click="prevSlide" :disabled="currentSlide === 0" class="reviews__arrow-button left" type="button">
              <span class="visually-hidden">Previous slide</span>
              <svg width="23.005859" height="19.982422" viewBox="0 0 23.0059 19.9824" fill="none"
                xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                <defs />
                <path
                  d="M5.12 11.49L11.05 17.41C11.64 18 11.64 18.94 11.05 19.53C10.45 20.13 9.52 20.13 8.92 19.53L0.44 11.05C-0.15 10.45 -0.15 9.52 0.44 8.93L8.92 0.44C9.52 -0.15 10.45 -0.15 11.05 0.44C11.64 1.03 11.64 1.97 11.05 2.56L5.12 8.49L21.5 8.49C22.34 8.49 23 9.15 23 9.99C23 10.83 22.34 11.49 21.5 11.49L5.12 11.49Z"
                  fill="#FFFFFF" fill-opacity="1" fill-rule="evenodd" />
              </svg>
            </button>

            <div class="pagination__list">
                  <button v-for="(index) in maxSlides"
                        :key="index"
                        :class="['pagination__button', { active: currentSlide === index - 1}]"
                        @click="goToSlide(index - 1)" class="pagination__button" type="button">
                    <span class="visually-hidden">First slide</span>
                    <svg width="14.000000" height="14.000000" viewBox="0 0 14 14" fill="none"
                      xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                      <defs />
                      <g>
                        <path d="M7 2.05L14 0L11.96 7L14 14L7 11.96L0 14L2.05 7L0 0L7 2.05Z" fill="#FFFFFF"
                          fill-opacity="1.000000" fill-rule="nonzero" />
                      </g>
                    </svg>
                  </button>
                </div>

            <button @click="nextSlide" :disabled="currentSlide >= maxSlides - 1" class="reviews__arrow-button right" type="button">
              <span class="visually-hidden">Next slide</span>
              <svg width="23.005859" height="19.982422" viewBox="0 0 23.0059 19.9824" fill="none"
                xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                <defs />
                <path id="Arrow 3"
                  d="M17.87 8.49L11.95 2.56C11.35 1.97 11.35 1.03 11.95 0.44C12.54 -0.15 13.48 -0.15 14.07 0.44L22.56 8.93C23.15 9.52 23.15 10.45 22.56 11.05L14.07 19.53C13.48 20.13 12.54 20.13 11.95 19.53C11.35 18.94 11.35 18 11.95 17.41L17.87 11.49L1.5 11.49C0.66 11.49 0 10.83 0 9.99C0 9.15 0.66 8.49 1.5 8.49L17.87 8.49Z"
                  fill="#FFFFFF" fill-opacity="1.000000" fill-rule="evenodd" />
              </svg>
            </button>
          </div>
        </div>
      </div>
  </section>
</template>

<script>
import SectionHeader from './SectionHeader.vue';
export default {
  components: {
    SectionHeader,
  },
  data() {
    return {
      currentSlide: 0,
      reviews: [
        {
          text: "We have been working with Positivus for the past year and have seen a significant increase in website traffic and leads as a result of their efforts. The team is professional, responsive, and truly cares about the success of our business. We highly recommend Positivus to any company looking to grow their online presence.",
          name: "John Smith",
          company: "Marketing Director at XYZ Corp",
        },
        {
          text: "We have been working with Positivus for the past year and have seen a significant increase in website traffic and leads as a result of their efforts. The team is professional, responsive, and truly cares about the success of our business. We highly recommend Positivus to any company looking to grow their online presence.",
          name: "John Smith",
          company: "Marketing Director at XYZ Corp",
        },
        {
          text: "We have been working with Positivus for the past year and have seen a significant increase in website traffic and leads as a result of their efforts. The team is professional, responsive, and truly cares about the success of our business. We highly recommend Positivus to any company looking to grow their online presence.",
          name: "John Smith",
          company: "Marketing Director at XYZ Corp",
        },
        {
          text: "The results we achieved with Positivus have truly exceeded our expectations. Their insights and strategies have transformed our approach to digital marketing.",
          name: "Jane Doe",
          company: "CEO at ABC Ltd",
        },
        {
          text: "We have been working with Positivus for the past year and have seen a significant increase in website traffic and leads as a result of their efforts. The team is professional, responsive, and truly cares about the success of our business. We highly recommend Positivus to any company looking to grow their online presence.",
          name: "John Smith",
          company: "Marketing Director at XYZ Corp",
        },
      ],

    };
  },
  computed: {
    maxSlides() {
      return Math.ceil(this.reviews.length / 1); // 1 - количество отзывов на слайд
    },
    visibleReviews() {
      const start = this.currentSlide * 1; // 1 - количество отзывов на слайд
      return this.reviews.slice(start, start + 1);
    },
  },
  methods: {
    prevSlide() {
      if (this.currentSlide > 0) {
        this.currentSlide -= 1;
      }
    },
    nextSlide() {
      if (this.currentSlide < this.maxSlides - 1) {
        this.currentSlide += 1;
      }
    },
    goToSlide(index) {
      this.currentSlide = index;
    },
  },
  mounted() {
    this.currentSlide = 0;
  },

}
</script>

<style scoped lang="scss">
.reviews {
 // --color-dark: #191A23;
 // --border-radius-large: 45px;
 // --color-light: #FFFFFF;
 // --color-accent: #B9FF66;
 // --color-gray-alt: #898989;

  padding-top: 84px;
  padding-bottom: 54px;
  display: flex;
  flex-direction: column;
  row-gap: 110px;
  color: var(--color-light);
  background-color: var(--color-dark);
  border-radius: var(--border-radius-large);
  overflow-x: hidden;

  @include tablet {
    padding: 30px 30px 46px;
    row-gap: 46px;
  }

  &__slider {
    --reviewsSliderSlideWidth: 606px;
    position: relative;
    max-width: var(--reviewsSliderSlideWidth);
    margin: auto;
    overflow: hidden;

    @include tablet {
      --reviewsSliderSlideWidth: 330px;
    }
  }

  &__actions {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    max-width: 564px;
    margin-inline: auto;
  }

  &__arrow-button {
    @include reset-button;
    @include flex-center;
    @include square(48px);

    color: var(--color-light);

    @include hover {
      color: var(--color-accent);
    }


    svg {
      @include square(20px);
    }
  }

}

.reviews__slider-item.show {
  display: block;
}

.reviews__arrow-button.disabled {
  color: var(--color-gray-alt);
  cursor: not-allowed;
}

.review-card {
    --reviewCardCornerWidth: 40px;
    --reviewCardCornerOffsetLeft: 52px;



    display: flex;
    flex-direction: column;
    row-gap: 48px;

    @include mobile {
        --reviewCardCornerWidth: 32px;
        --reviewCardCornerOffsetLeft: 46px;
        --color-accent: #B9FF66;
        --border-radius-large: 45px;
        --color-dark: #191A23;

        row-gap: 44px;
    }

    &__body {
        position: relative;
        padding: 48px var(--reviewCardCornerOffsetLeft) 52px;
        border: 1px solid var(--color-accent);
        border-radius: var(--border-radius-large);

        @include mobile {
            padding: 30px;
        }

        &::after {
            @include square(var(--reviewCardCornerWidth));

            content: '';
            position: absolute;
            top: 100%;
            left: var(--reviewCardCornerOffsetLeft);
            background-color: var(--color-dark);
            border: inherit;
            rotate: 45deg;
            clip-path: polygon(100% 0, 0% 100%, 100% 100%);
            translate: 0 -50%;

        }

    }

    &__footer {
        display: flex;
        flex-direction: column;
        padding-left: calc(var(--reviewCardCornerOffsetLeft) + var(--reviewCardCornerWidth) / 2);
    }

    &__name, &__company {
        font-style: normal;
    }

    &__name {
        color: var(--color-accent);
    }
}

.pagination {
  --color-light: #FFFFFF;
  --color-accent: #B9FF66;
    &__list {
        display: flex;
    }

    &__button {
        @include reset-button;
        @include flex-center;
        @include square(24px);
        color: var(--color-light);
        @include hover {
            color: var(--color-accent);
        }

        &.active {
            color: var(--color-accent);
        }
    }
}
</style>
