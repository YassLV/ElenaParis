<template>
  <main>
    <div class="container">
      <div v-for="el in gender()" :key="key">
        <div class="icons-container">
          <div>
            <img src="~/assets/images/svg/likes-icon.svg" alt="likes-icon" />
          </div>
          <div>
            <img src="~/assets/images/svg/basket-icon.svg" alt="basket-icon" />
          </div>
        </div>
        <nuxt-link v-if="el.link" :to="localePath({ name: 'category-article', query: { article: el.link }})">
          <img :src="require(`@/assets/images/images/${getGender}/${el.img}.jpg`)" :alt="`${el.img}-icon`" />
        </nuxt-link>
        <img v-else :src="require(`@/assets/images/images/${getGender}/${el.img}.jpg`)" :alt="`${el.img}-icon`" />
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from 'vue';


export default Vue.extend({
  name: 'StoreSection',
  props: {
    isWoman: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      man: [
        {
          link: 'man-blue',
          img: 'blue',
          alt: 'Bl',
          color: 'blue',
        },
        {
          link: 'man-black',
          img: 'black',
          alt: 'Bl',
          color: 'black',
        },
        {
          link: null,
          img: 'full',
          alt: 'full',
          color: 'black',
        }
      ],
      woman: [
        {
          link: 'woman-blue',
          img: 'blue',
          alt: 'Bl',
          color: 'blue',
        },
        {
          link: 'woman-or',
          img: 'or',
          alt: 'or',
          color: 'or',
        },
        {
          link: null,
          img: 'full',
          alt: 'full',
          color: 'blue',
        }
      ],
    }
  },
  computed: {
    getGender() {
      if(this.isWoman) {
        return 'woman';
      } else {
        return 'man';
      }
    }
  },
  methods: {
    gender() {
      if (this.isWoman) {
        return this.woman;
      } else {
        return this.man;
      }
    }
  }
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

.container {
  div  {
    position: relative;
    img {
      width: 100%;
    }
    .icons-container {
      position: absolute;
      top: 5px;
      right: 5px;
      width: 80px;
      div {
        display: inline-block;
        width: 25px;
        margin-left: $size-small;
      }
    }
  }
}

@media screen and(min-width: 700px) {
  .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-auto-rows: auto;
    grid-gap: $size-extra-large;
  }
}
</style>
