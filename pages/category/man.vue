<template>
  <main>
    <div class="content-p">
      <p class="subtitle" v-for="(subtitle, key) in $t('man.subtitles')" :key="key">
        {{ subtitle }}
      </p>
      <store-section />
    </div>
    <advantages-section />
  </main>
</template>

<script lang="ts">
import Vue from 'vue';

import AdvantagesSection from '~/components/sections/advantages-section.vue';
import StoreSection from "~/components/sections/store-section.vue";

import { Head } from '~/types';

export default Vue.extend({
  name: 'Man',
  components: {
    StoreSection,
    AdvantagesSection
  },
  head(): Head {
    return {
      title: this.$t('man.title').toString(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('man.description').toString(),
        },
      ],
    };
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

main {
  .subtitle {
    text-align: center;
  }
}

@media screen and(min-width: $tablet) {
  .content-p {
    padding: 0 10%
  }
}

</style>

<i18n src="./man.i18n.yml" lang="yaml" />
