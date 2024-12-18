<template>
<section class="section section--hidden-x container">
            <div class="section__body">
                <div class="hero">
                    <div class="hero__main">
                        <div class="hero__body">
                            <h1 class="hero__title">Navigating the digital landscape for success</h1>
                            <div class="hero__description">
                                <p>Our digital marketing agency helps businesses grow and succeed online through a range
                                    of services including SEO, PPC, social media marketing, and content creation.</p>
                            </div>
                            <ButtonMy @click="handleClick" variant="hero">Book a consultation</ButtonMy>
                        </div>
                        <img src="../assets/images/Illustration.svg" alt="" class="hero__image" loading="lazy" width="600"
                            height="515">
                    </div>
                    <div class="hero__partners">
                        <h2 class="visually-hidden">Our partners</h2>
                        <ul class="hero__partners-list">

                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (6).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (1).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (2).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (3).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (4).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                            <li class="hero__partners-item">
                                <img src="../assets/images/Company logo (5).svg" alt="" width="130" height="48" loading="lazy"
                                    class="hero__partners-image">
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>
</template>

<script>
import ButtonMy from './ButtonMy.vue';
export default {
  components: {
    ButtonMy,
  },
  methods: {
    handleClick() {
      console.log('Button clicked!');
    },
  },

}
</script>

<style scoped lang="scss">
.hero {
    --section-padding-y: 20px;
    display: flex;
    flex-direction: column;
    row-gap: var(--section-padding-y);

    @include desktop {
        row-gap: 60px;
    }

    &__main {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        column-gap: 30px;

        @include mobile {
            flex-direction: column;
        }
    }

    &__body {
        max-width: 530px;
        display: flex;
        flex-direction: column;
        align-items: start;
        row-gap: 35px;

        @include mobile {
            display: contents;
        }
    }

    &__description {
        font-size: 20px;
        line-height: 1.4;

        @include mobile {
            margin-bottom: 40px;
        }
    }

    &__title {
        font-size: 60px;

        @include mobile {
            order: -2;
            margin-bottom: 10px;
        }
    }

    &__partners {
        &-list {
            display: flex;
            justify-content: space-between;
            column-gap: 37px;
            margin-top: 100px;

            @include tablet {
                display: grid;
                grid-template-columns: repeat(3, 1fr);
                row-gap: 20px;
            }

            @include mobile {
                margin-top: 30px;

            }

            @include mobile-s {
                --heroPartnersWidthOffsetX: 60px;
                --container-padding-x: 20px;

                width: calc(100vw + var(--heroPartnersWidthOffsetX) * 2);
                margin-left: calc((var(--heroPartnersWidthOffsetX) + var(--container-padding-x)) * -1);

                column-gap: 0;
            }

        }

        &-item {
            @include tablet {
                display: flex;
                justify-content: center;
            }

            @include mobile-s {
                justify-content: flex-start;

                &:nth-child(-n + 3) {
                    justify-content: flex-end;
                }
            }
        }

        &-image {
            filter: grayscale(1);
        }
    }

    &__image {
        @include tablet {
            max-width: 40%;
            height: auto;
        }

        @include mobile {
            order: -1;
            width: 100%;
            max-width: 100%;
            margin-bottom: 20px;
        }
    }
}
</style>
