<template>
    <div class="navigation">
        <div class="navigation__logo">
            <span>Lucas van Borkulo</span>
        </div>
        <ul class="navigation__links">
            <NuxtLink to="/"><li class="navigation__link">Home</li></NuxtLink>
            <NuxtLink to="/work"><li class="navigation__link">Mijn werk</li></NuxtLink>
            <NuxtLink to="/about"><li class="navigation__link">Over mij</li></NuxtLink>
            <NuxtLink to="/contact"><li class="navigation__link">Contact</li></NuxtLink>
        </ul>
    </div>
</template>
<style scoped lang="scss">
.navigation {
    background-color: #111111;
    height: 80px;
    display: flex;
    align-items: center;
    padding-inline: 48px;

    &__logo {
        width: 20%;
        color: #ffffff;
    }

    &__links {
        list-style: none;
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 80%;
    }
    a {
        text-decoration: none;
        color: #ffffff;
    }
    .nuxt-link-active {
        text-decoration: underline;
    }
}
</style>