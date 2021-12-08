<template>
  <home-poster />
</template>

<script lang="ts">
import Vue from 'vue';

import HomePoster from '~/components/sections/home-poster.vue';

import { Head } from '~/types';

export default Vue.extend({
  name: 'Home',
  components: {
    HomePoster,
  },
  head(): Head {
    return {
      title: this.$t('home.title').toString(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('home.description').toString(),
        },
      ],
    };
  },
});
</script>

<i18n src="./index.i18n.yml" lang="yaml" />
