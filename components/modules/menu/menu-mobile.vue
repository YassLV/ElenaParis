<template>
  <nav :class="classNames">
    <div class="links">
      <ul>
        <li>
          <nuxt-link :to="localePath({ name: 'category-man' })" :class="{ active: isLinkActive('category-man') }"
          >
            {{ $t('menu.man') }}
          </nuxt-link>
        </li>
        <li class="end-cat">
          <nuxt-link :to="localePath({ name: 'category-woman' })" :class="{ active: isLinkActive('category-woman') }">
            {{ $t('menu.woman') }}
          </nuxt-link>
        </li>
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
  </nav>
</template>

<script lang="ts">
import Vue from 'vue';


export default Vue.extend({
  name: 'MenuMobile',
  props: {
    isActive: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classNames() {
      return {
        'mobile-menu': true,
        active: this.isActive,
      };
    },
  },
  methods: {
    isLinkActive(routeName: string): boolean {
      return this.localePath({ name: routeName })  === this.$route.path;
    },
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

.mobile-menu {
  position: fixed;
  z-index: 5000;
  top: 0;
  left: -100%;
  height: 100%;
  width: 100%;
  background-color: $darkBlack;
  color: $white;
  transition: all 1s;

  .end-cat {
    margin-bottom: $size-extra-large;
  }

  .links {
    margin-top: $size-extra-large;
  }

  .links {
    padding-left: 10%;
    ul {
      list-style-type: none;
      li {
        color: $white;
        a {
          color: $white;
          text-decoration: none;
          font-weight: bold;
          &.active {
            color: $whiteActive !important;
          }
        }
      }
    }
  }

  &.active {
    left: 0;
    transition: all 1s;

    ul {
      opacity: 1;
    }
  }

  ul {
    opacity: 0;
    margin-top: 100px;
    transition: all 0.5s;
    font-size: $size-large;

    .navigation-item {
      margin-bottom: $size-normal;
      margin-left: 10%;
      &.active {
        display: block;
        align-items: center;
        border: 2px solid $white;
        border-left: none;
        border-right: none;
        text-decoration: none;
        margin-left: 0;
        padding: 10px 0 10px 10%;
        width: 100%;
        margin-bottom: $size-normal * 2;
        &:after {
          margin: 0;
          height: 0;
        }
      }
    }
  }
}

@media screen and(min-width: $mobile) {
  .menu-mobile {
    display: none;

    ul {
      font-size: $size-extra-large;
    }
  }
}

@media screen and(min-width: $tablet) {
  .menu-mobile {
    display: none;
  }
}
</style>

<i18n src="./menu.i18n.yml" lang="yaml" />
