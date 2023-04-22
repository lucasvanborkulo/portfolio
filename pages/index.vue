<template>
  <div class="content">
    <Navigation />
    <div class="hero">
      <span class="hero__text">{{ heroText.rendered }}</span>
    </div>
    <div class="about-me">
      <span class="subtitle">In het kort</span>
    </div>
    <div class="skills">
      <span class="subtitle">Ervaringen</span>
      <div class="skills__entries">
        <div class="skills__entry" v-for="skill in skills">
          <span>{{ skill }}</span>
        </div>
      </div>
    </div>
    <Footer />
  </div>
</template>

<script>
import Footer from '../components/Footer.vue';
import Navigation from '../components/Navigation.vue';

export default {
  components: { Navigation, Footer },
  data() {
    return {
      heroText: {
        result: "Hallo! Ik ben Lucas van Borkulo!",
        rendered: ""
      },
      skills: [
        "JavaScript",
        "Java",
        "HTML",
        "CSS/SCSS",
        "Node.js",
        "SQL",
        "Vue.js",
        "Nuxt.js",
        "Laravel",
        "PHP",
        "Linux",
        "React.js",
        "Redis",
        "GraphQL",
        "WordPress"
      ]
    }
  },
  methods: {
    renderHeroText() {
      if (this.heroText.result.length > this.heroText.rendered.length)
        this.heroText.rendered += this.heroText.result.charAt(this.heroText.rendered.length);
    }
  },
  mounted() {
    setInterval(this.renderHeroText, 110);
  }
}
</script>
<style scoped lang="scss">
.content {
  .subtitle {
    font-weight: 400;
    font-size: 150%;
  }

  .hero {
    background-color: #f8f8f8;
    height: calc(100vh - 80px - 140px);
    display: flex;
    align-items: center;
    justify-content: center;

    &__text {
      color: #000;
      border-right: #000 solid 1px;
      padding-right: 1px;
      animation-name: typeIndicator;
      animation-duration: 1s;
      animation-iteration-count: infinite;
      font-size: 300%;
    }
  }

  .about-me {
    background-color: #ffffff;
    height: 150px;
    padding-block: 25px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .skills {
    height: 200px;
    background-color: #f8f8f8;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 30px;
    color: #000000;
    padding-block: 25px;

    &__entry {
      transition-duration: 300ms;

      &:hover {
        font-size: 130%;
        transition-duration: 300ms;
      }
    }

    &__entries {
      display: flex;
      flex-direction: row;
      gap: 18px;
    }
  }
}

@keyframes typeIndicator {
  0% {
    border-right: #000 solid 2px;
  }

  100% {
    border-right: #00000000 solid 2px;
  }
}
</style>
