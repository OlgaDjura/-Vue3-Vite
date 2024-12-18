<template>
  <div id="app" class="body">
  <HeaderMy/>

  <main>
  <HeroMy></HeroMy>
  <ServicesMy></ServicesMy>
  <StudiesMy></StudiesMy>
  <ProcessMy></ProcessMy>
  <TeamMy></TeamMy>
  <ReviewsMy></ReviewsMy>
  <ContactUsForm></ContactUsForm>
  <FooterMy></FooterMy>
  </main>
</div>
</template>

<script>
import HeaderMy from './components/HeaderMy.vue';
import HeroMy from './components/HeroMy.vue';
import ServicesMy from './components/ServicesMy.vue';
import StudiesMy from './components/StudiesMy.vue';
import ProcessMy from './components/ProcessMy.vue';
import TeamMy from './components/TeamMy.vue';
import ReviewsMy from './components/ReviewsMy.vue';
import ContactUsForm from './components/ContactUsForm.vue';
import FooterMy from './components/FooterMy.vue';



export default {
  components: {
    HeaderMy,
    HeroMy,
    ServicesMy,
    StudiesMy,
    ProcessMy,
    TeamMy,
    ReviewsMy,
    ContactUsForm,
    FooterMy,
  }
}
</script>


<style scoped>


</style>
