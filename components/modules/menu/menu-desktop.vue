<template>
  <header>
    <burger-button :is-active="isActive" @toggle="emitToggle" />
    <div class="logo-container">
      <nuxt-link :to="localePath({ name: 'index' })">
        <img class="tablet-logo" src="~/assets/images/logos/elena-paris-logo.svg" alt="elena-icon" />
        <img class="mobile-logo" src="~/assets/images/logos/elena-logo.svg" alt="elena-icon" />
      </nuxt-link>
    </div>
    <div class="links">
      <ul>
        <li>
          {{ $t('menu.search') }}
        </li>
        <li>
          <nuxt-link :to="localePath({ name: 'help' })" :class="{ active: isLinkActive('help') }">
            {{ $t('menu.help') }}
          </nuxt-link>
        </li>
        <li>
          <nuxt-link :to="localePath({ name: 'basket' })" :class="{ active: isLinkActive('basket') }">
            {{ $t('menu.basket') }}
          </nuxt-link>
        </li>
      </ul>
    </div>
  </header>
</template>

<script lang="ts">
import Vue from 'vue';

import BurgerButton from '~/components/elements/burger-button';


export default Vue.extend({
  name: 'Header',
  props: {
    isActive: {
      type: Boolean,
      default: false,
    },
  },
  components: {
    BurgerButton,
  },
  methods: {
    emitToggle(): void {
      this.$emit('toggle');
    },
    isLinkActive(routeName: string): boolean {
      return this.localePath({ name: routeName }) === this.$route.path;
    },
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/_vars.scss';

header {
  min-height: 80px;
  padding-top: $size-large;
  .burger-button {
    float: left;
  }
  .logo-container {
    position: absolute;
    right: $size-large;
    .mobile-logo {
      display: block;
    }
    .tablet-logo {
      display: none;
    }
  }
  .links,
  .buttons {
    display: none;
  }
}

@media screen and(min-width: $tablet) {
  header {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-auto-rows: auto;
    grid-gap: $size-extra-large;
    .logo-container {
      place-self: center start;
      position: relative;
      transform: translate(-50%);
      right: 0;
      left: 50%;
      margin-left: $size-extra-large * 3;
      .mobile-logo {
        display: none;
      }
      .tablet-logo {
        display: block;
      }
    }
    .links {
      display: block;
      ul {
        li {
          display: inline-block;
          padding-right: $size-large;
          color: $black;
          a {
            color: $black;
            text-decoration: none;
            &.active {
              font-weight: bold;
            }
          }
        }
      }
    }
    .buttons {
      display: block;
      .button {
        margin-left: $size-normal;
      }
    }
    div {
      align-content: center;
      place-self: center end;
      padding-right: $size-extra-large * 3;
    }
  }
}
</style>

<i18n src="./menu.i18n.yml" lang="yaml" />
