<template>
    <div class="footer__navigation">
                <a href="/" class="footer__logo logo">
                    <img class="logo__imge" src="../assets/images/footer.svg" alt="positivus" width="180" height="29"
                        loading="lazy">
                </a>
                <nav class="footer__menu">
                    <ul class="footer__menu-list">
                        <li class="footer__menu-item">
                            <a href="/" class="footer__menu-link">About us</a>
                        </li>
                        <li class="footer__menu-item">
                            <a href="/" class="footer__menu-link">Services</a>
                        </li>
                        <li class="footer__menu-item">
                            <a href="/" class="footer__menu-link">Use Cases</a>
                        </li>
                        <li class="footer__menu-item">
                            <a href="/" class="footer__menu-link">Pricing</a>
                        </li>
                        <li class="footer__menu-item">
                            <a href="/" class="footer__menu-link">Blog

                            </a>
                        </li>
                    </ul>
                </nav>

                <div class="footer__soc1als soc1als">
                    <ul class="soc1als__list">
                        <li class="soc1als__item">
                            <a href="/" class="soc1als__link">
                                <span class="visually-hidden">LinkedIn</span>
                                <svg width="17.000000" height="17.000000" viewBox="0 0 17 17" fill="none"
                                    xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                    <defs />
                                    <path
                                        d="M2.06 4.09C0.9 4.09 0 3.18 0 2.07C0 0.95 0.9 0 2.06 0C3.17 0 4.07 0.95 4.07 2.07C4.07 3.18 3.17 4.09 2.06 4.09ZM13.45 17L17 17L17 10.78C17 7.75 16.31 5.36 12.76 5.36C11.06 5.36 9.9 6.32 9.42 7.22L9.37 7.22L9.37 5.68L6.03 5.68L6.03 17L9.53 17L9.53 11.42C9.53 9.93 9.79 8.5 11.65 8.5C13.45 8.5 13.45 10.2 13.45 11.47L13.45 17ZM3.81 17L0.31 17L0.31 5.68L3.81 5.68L3.81 17Z"
                                        fill="#B9FF66" fill-opacity="1.000000" fill-rule="evenodd" />
                                </svg>
                            </a>
                        </li>
                        <li class="soc1als__item">
                            <a href="/" class="soc1als__link">
                                <span class="visually-hidden">Facebook</span>
                                <svg fill="#000000" version="1.1" xmlns="http://www.w3.org/2000/svg"
                                    xmlns:xlink="http://www.w3.org/1999/xlink" width="800px" height="800px"
                                    viewBox="0 0 512 512" xml:space="preserve">
                                    <path style="display: inline;" d="M283.122,122.174c0,5.24,0,22.319,0,46.583h83.424l-9.045,74.367h-74.379
		c0,114.688,0,268.375,0,268.375h-98.726c0,0,0-151.653,0-268.375h-51.443v-74.367h51.443c0-29.492,0-50.463,0-56.302
		c0-27.82-2.096-41.02,9.725-62.578C205.948,28.32,239.308-0.174,297.007,0.512c57.713,0.711,82.04,6.263,82.04,6.263
		l-12.501,79.257c0,0-36.853-9.731-54.942-6.263C293.539,83.238,283.122,94.366,283.122,122.174z">
                                    </path>
                                </svg>
                            </a>
                        </li>
                        <li class="soc1als__item">
                            <a href="/" class="soc1als__link">
                                <span class="visually-hidden">Twitter</span>
                                <svg width="17.613281" height="14.303711" viewBox="0 0 17.6133 14.3037" fill="none" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                                    <path d="M15.82 3.54C16.5 3.03 17.13 2.41 17.61 1.68C16.99 1.96 16.26 2.17 15.54 2.24C16.3 1.79 16.85 1.1 17.13 0.24C16.44 0.65 15.64 0.96 14.85 1.13C14.16 0.41 13.23 0 12.2 0C10.2 0 8.58 1.62 8.58 3.61C8.58 3.89 8.61 4.17 8.68 4.44C5.68 4.27 2.99 2.82 1.2 0.65C0.89 1.17 0.72 1.79 0.72 2.48C0.72 3.72 1.34 4.82 2.34 5.48C1.75 5.44 1.17 5.3 0.68 5.03L0.68 5.06C0.68 6.82 1.92 8.27 3.58 8.61C3.3 8.68 2.96 8.75 2.65 8.75C2.41 8.75 2.2 8.71 1.96 8.68C2.41 10.13 3.75 11.16 5.34 11.2C4.1 12.16 2.55 12.75 0.86 12.75C0.55 12.75 0.27 12.71 0 12.68C1.58 13.71 3.48 14.3 5.54 14.3C12.2 14.3 15.82 8.82 15.82 4.03C15.82 3.86 15.82 3.72 15.82 3.54Z" fill="#000000" fill-opacity="1.000000" fill-rule="nonzero"/>
                                </svg>
                            </a>
                        </li>
                    </ul>
                </div>
            </div>
</template>

<script>
export default {
}
</script>

<style scoped lang="scss">
.footer {
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
}

.soc1als {
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
</style>
