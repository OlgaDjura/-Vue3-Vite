<template>
  <section class="section container">
        <SectionHeader title="Our Working Process" content=" Step-by-Step Guide to Achieving.
                        Your Business Goals"></SectionHeader>
            <div class="section__body">
                <div class="process">
                    <ol class="process__list">
                        <li class="process__item">
                          <AccordionMy title="Consultation"
                              content="During the initial consultation, we will discuss your business goals and objectives, target audience, and current marketing efforts. This will allow us to understand your needs and tailor our services to best fit your requirements."
                            :open="true"></AccordionMy>
                        </li>
                        <li class="process__item">
                            <AccordionMy title="Research and Strategy Development"
                              content="During the initial consultation, we will discuss your business goals and
                                        objectives, target audience, and current marketing efforts. This will allow us
                                        to understand your needs and tailor our services to best fit your requirements."
                            :open="false"></AccordionMy>
                        </li>
                        <li class="process__item">
                        <AccordionMy title="Implementation"
                            content="During the initial consultation, we will discuss your business goals and
                                        objectives, target audience, and current marketing efforts. This will allow us
                                        to understand your needs and tailor our services to best fit your requirements."
                            :open="false"></AccordionMy>
                        </li>
                        <li class="process__item">
                          <AccordionMy title="Monitoring and Optimization"
                              content="During the initial consultation, we will discuss your business goals and
                                        objectives, target audience, and current marketing efforts. This will allow us
                                        to understand your needs and tailor our services to best fit your requirements."
                            :open="false"></AccordionMy>
                        </li>
                        <li class="process__item">
                          <AccordionMy title="Reporting and Communication"
                              content="During the initial consultation, we will discuss your business goals and
                                        objectives, target audience, and current marketing efforts. This will allow us
                                        to understand your needs and tailor our services to best fit your requirements."
                            :open="false"></AccordionMy>
                        </li>
                        <li class="process__item">
                          <AccordionMy title="Continual Improvement"
                              content="During the initial consultation, we will discuss your business goals and
                                        objectives, target audience, and current marketing efforts. This will allow us
                                        to understand your needs and tailor our services to best fit your requirements."
                            :open="false"></AccordionMy>
                        </li>
                    </ol>
                </div>
            </div>
  </section>
</template>

<script>
import AccordionMy from './AccordionMy.vue';
import SectionHeader from './SectionHeader.vue';
export default {
  components: {
    AccordionMy,
    SectionHeader
  }
}
</script>

<style scoped lang="scss">
.process {
    &__list {
        display: flex;
        flex-direction: column;
        row-gap: 30px;
        counter-reset: custom-counter;
        list-style: none;

        @include mobile {
            row-gap: 20px;
        }
    }

    &__item {
        --counterContent: counter(custom-counter);
        counter-increment: custom-counter;

        &:nth-child(-n + 9) {
            --counterContent: '0' counter(custom-counter);
        }
    }
  }
</style>
