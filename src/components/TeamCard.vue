<template>
    <article class="team-card" v-if="member && Object.keys(member).length">
        <header class="team-card__header">
            <img
            :src="member.image || 'defoult'"
            alt=""
            class="team-card__image"
            width="100"
            height="100"
            loading="lazy">
            <div class="team-card__info">
                <h3 class="team-card__name h4">{{ member.name || 'no name' }}</h3>
                <p class="team-card__post">{{ member.position || 'no post' }}</p>
            </div>
            <a :href="member.link" class="team-card__link" target="_blank">
                <span class="visually-hidden">LikeIn</span>
                <svg width="17" height="17" viewBox="0 0 17 17" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path
                        d="M2.06 4.09C0.9 4.09 0 3.18 0 2.07C0 0.95 0.9 0 2.06 0C3.17 0 4.07 0.95 4.07 2.07C4.07 3.18 3.17 4.09 2.06 4.09ZM13.45 17L17 17L17 10.78C17 7.75 16.31 5.36 12.76 5.36C11.06 5.36 9.9 6.32 9.42 7.22L9.37 7.22L9.37 5.68L6.03 5.68L6.03 17L9.53 17L9.53 11.42C9.53 9.93 9.79 8.5 11.65 8.5C13.45 8.5 13.45 10.2 13.45 11.47L13.45 17ZM3.81 17L0.31 17L0.31 5.68L3.81 5.68L3.81 17Z"
                        fill="#B9FF66" />
                </svg>
            </a>
        </header>
        <div class="team-card__body">
            <p>{{ member.description || 'no description' }}</p>
        </div>
    </article>
</template>

<script>
export default {
    name: 'TeamCard',
    props: {
        member: {
            type: Object,
            required: true,
            default: () => ({
                image: '',
                name: '',
                post: '',
                link: '',
                description: ''
            }),
        },
    }
}
</script>


<style scoped lang="scss">
.team-card {
    //display: grid;
    //grid-template-columns: repeat(3, 1fr); /* Задаем 3 колонки */
    //gap: 20px; /* Промежуток между карточками */
    height: 100%;
    padding: 40px 35px;
    border: var(--border);
    border-radius: var(--border-radius-large);
    box-shadow: var(--shadow);

    @include mobile {
        padding-inline: 50px;
    }

    &__header {
        display: flex;

    }

    &__image {
        &:not(:last-child) {
            margin-right: 20px;
        }
    }

    &__info {
        align-self: end;

        &:not(:last-child) {
            margin-right: 10px;
        }
    }

    &__link {
        @include flex-center;
        @include square(34px);

        flex-shrink: 0;
        align-self: start;
        margin-left: auto;
        color: var(--color-accent);
        background-color: var(--color-dark);
        border-radius: 50%;
    }

    &__name {
        &:not(:last-child) {
            margin-bottom: 3px;
        }
    }

    &__body {
        --teamCardMarginTop: 28px;
        margin-top: var(--teamCardMarginTop);
        padding-top: var(--teamCardMarginTop);
        border-top: var(--border);

        @include mobile {
            --teamCardMarginTop: 20px;

        }
    }
}
</style>
