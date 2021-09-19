<template>
  <nav class="nav">
    <router-link to="/">
      <img
        class="nav-logo"
        src="@/assets/images/devchallenges-logo.svg"
        alt="devchallenges logo"
      >
    </router-link>
    <ul class="nav-list">
      <li
        v-for="navRoute in navRoutes"
        :key="navRoute.route"
        class="nav-item"
      >
        <router-link
          exact-active-class="active"
          class="nav-link"
          :to="navRoute.route"
        >
          {{ navRoute.routeName }}
        </router-link>
      </li>
    </ul>
  </nav>
</template>

<script setup lang="ts">
const navRoutes = [
  {
    route: '/buttons',
    routeName: 'Buttons',
  },
  {
    route: '/inputs',
    routeName: 'Inputs',
  },
];
</script>

<style lang="scss">
@use '@/assets/scss/abstracts/_variables.scss' as var;
.nav {
  width: 13.625rem;
  background-color: var.$clr-sidebar-bg;
  min-height: 100vh;
  padding: 2.8125rem 2rem 2rem 2rem;

  &-logo {
    height: 1.125rem;
  }

  &-list {
    margin-top: 7.625rem;
  }

  &-item {
    list-style: none;

    & + * {
      margin-top: 1.25rem;
    }
  }

  &-link {
    color: var.$clr-neutral-inactive;
    text-decoration: none;
    transition: color 200ms ease-out;

    &:hover {
      color: darken($color: var.$clr-neutral-inactive, $amount: 10);
    }

    &.active {
      color: var.$clr-neutral;
    }
  }
}

</style>
