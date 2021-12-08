<template>
  <div class="home-poster">
    <div class="home-poster-container">
      <div class="woman">
        <nuxt-link :to="localePath({ name: 'category-woman' })">
          <p>{{ $t('home-poster.woman') }}</p>
        </nuxt-link>
      </div>
      <div class="img">
        <h1 class="title">ELENA</h1>
        <img src="~/assets/images/images/tel-aviv-fashion-week-innovation-2018.jpeg" alt="elena-poster" />
        <div class="txt">
          <div class="bonds">
            <p v-for="(bond, key) in $t('home-poster.bonds')" :key="key">{{ bond }}</p>
          </div>
          <div class="collections">
            <p v-for="(collection, key) in $t('home-poster.collections')" :key="key">{{ collection }}</p>
          </div>
        </div>
      </div>
      <div class="man">
        <nuxt-link :to="localePath({ name: 'category-man' })">
          <p>{{ $t('home-poster.man') }}</p>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';


export default Vue.extend({
  name: 'HomePoster',
});
</script>


<style scoped lang="scss">
@import 'assets/css/vars';

.home-poster {
  &-container {
    display: block;
    margin: $size-large 0;
    margin-bottom: $size-extra-large * 7;
    .img {
      position: relative;
      .title {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -85%);
        font-weight: normal;
        color: $white;
        font-size: 10vh ;
        z-index: 10;
        cursor: default;
      }
      .txt {
        position: absolute;
        margin-left: $size-large;
      }
      img {
        opacity: 0.8;
      }
    }
    .woman, .man {
      display: none;
      a {
        text-decoration: none;
      }
    }
    .txt {
      div {
        margin-top: $size-large;
        p {
          margin:0;
          padding:0;
        }
      }
    }
  }
}

@media screen and(min-width: $tablet) {
  .home-poster {
    &-container {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      grid-auto-rows: auto;
      grid-gap: $size-extra-large;
      place-items: center;
      .img {
        img {
          width: 100vh;
        }
      }
      .woman, .man {
        display: block;
      }
      .woman {
        p:before {
          content: '\003C\00a0';
        }
      }
      .man {
        p:after {
          content: '\00a0\02C3';
        }
      }
    }
  }
}

@media screen and(max-width: 1145px) {
  .home-poster {
    &-container {
      .img {
        img {
          width: 90vh;
        }
      }
    }
  }
}

@media screen and(max-width: $tablet) {
  .home-poster {
    &-container {
      .img {
        img {
          width: 100%;
        }
      }
    }
  }
}
</style>

<i18n src="./home-poster.i18n.yml" lang="yaml" />
