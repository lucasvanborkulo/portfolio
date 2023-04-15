<template>
  <div class="content">
    <Navigation />
    <div class="hero">
      <span class="hero__text">{{ heroTextRendered }}</span>
    </div>
    <div class="carousel">

    </div>
    <div class="skills">
      <h1>Ervaringen</h1>
      <div class="skills__entries">
        <div class="skills__entry" v-for="skill in skills">
          <span>{{ skill }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Navigation from '../components/Navigation.vue';

export default {
  components: { Navigation },
  data() {
    return {
      heroText: "Hallo! Ik ben Lucas van Borkulo!",
      heroTextRendered: "",
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
      if (this.heroText.length > this.heroTextRendered.length)
        this.heroTextRendered += this.heroText.charAt(this.heroTextRendered.length);
    }
  },
  mounted() {
    setInterval(this.renderHeroText, 110);
  }
}
</script>
<style scoped lang="scss">
.content {
  .hero {
    background-color: #222222;
    height: calc(100vh - 80px - 140px);
    display: flex;
    align-items: center;
    justify-content: center;

    &__text {
      color: #ffffff;
      border-right: #ffffff solid 1px;
      padding-right: 1px;
      animation-name: typeIndicator;
      animation-duration: 1000ms;
      animation-iteration-count: infinite;
    }
  }

  .carousel {
    background-color: #111111;
    height: 140px;
  }

  .skills {
    height: 250px;
    background-color: #222222;
    display: flex;
    flex-direction: column;
    align-items: center;
    color: #ffffff;

    &__entries {
      display: flex;
      flex-direction: row;
      gap: 18px;
    }
  }
}

@keyframes typeIndicator {
  0% {
    border-right: #ffffff solid 1px;
  }

  100% {
    border-right: none;
  }
}
</style>
