<template>
  <section class="section container">
    <SectionHeader title="Team"
      content="Meet the skilled and experienced team behind our successful digital marketing strategies">
    </SectionHeader>
    <div class="section__body">
      <div class="team">
        <ul class="team__list grid grid--3">
          <li class="team__item" v-for="(member, index) in teamMembers" :key="index">
            <TeamCard :member="member" />
          </li>
        </ul>
        <ButtonMy @click="handleClick">See all team</ButtonMy>
      </div>
    </div>
  </section>
</template>

<script>
import SectionHeader from './SectionHeader.vue';
import ButtonMy from './ButtonMy.vue';
import TeamCard from './TeamCard.vue';
import picture1 from '../assets/images/Picture.svg';
import picture2 from '../assets/images/Picture (1).svg';
import picture3 from '../assets/images/Picture (2).svg';
import picture4 from '../assets/images/Picture (3).svg';
import picture5 from '../assets/images/Picture (4).svg';
import picture6 from '../assets/images/Picture (5).svg';

export default {
  components: {
    SectionHeader,
    ButtonMy,
    TeamCard,
  },
  data() {
    return {
      teamMembers: [],
    };
  },
  async created() {
    this.teamMembers = await this.loadTeamMembers();
  },
  methods: {
    async loadTeamMembers() {
      const members = [
        {
          image: picture1,
          name: 'John Smith',
          position: 'CEO and Founder',
          link: '/',
          description: '10+ years of experience in digital marketing. Expertise in SEO, PPC, and content strategy',
        },
        {
          image: picture2,
          name: 'Jane Doe',
          position: 'Director of Operations',
          link: '/',
          description: '7+ years of experience in project management and team leadership. Strong organizational and communication skills',
        },
        {
          image: picture3,
          name: 'Michael Brown',
          position: 'Senior SEO Specialist',
          link: '/',
          description: '5+ years of experience in SEO and content creation. Proficient in keyword research and on-page optimization',
        },
        {
          image: picture4,
          name: 'Emily Johnson',
          position: 'PPC Manager',
          link: '/',
          description: '3+ years of experience in paid search advertising. Skilled in campaign management and performance analysis',
        },
        {
          image: picture5,
          name: 'Brian Williams',
          position: 'Social Media Specialist',
          link: '/',
          description: '4+ years of experience in social media marketing. Proficient in creating and scheduling content, analyzing metrics, and building engagement',
        },
        {
          image: picture6,
          name: 'Sarah Kim',
          position: 'Content Creator',
          link: '/',
          description: '2+ years of experience in writing and editing. Skilled in creating compelling, SEO-optimized content for various industries',
        },

      ];
      return members;
    },
    handleClick() {
      console.log('clicked');
    },
  },
};
</script>
<style scope lang="scss">
.team {
  display: flex;
  flex-direction: column;
  row-gap: 40px;
}
.button {
  width: 269px;
  align-self: end;
  @include mobile-s {
    width: 100%;
  }
}
</style>
