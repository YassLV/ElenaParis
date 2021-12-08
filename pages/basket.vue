<template>
  <div class="basket">
    <p><img src="~/assets/images/svg/basket.svg" alt="basket-icon" /></p>
    <p>{{ $t('basket.blocs.empty') }} <img src="~/assets/images/svg/smile.svg" alt="smile-icon" /></p>
    <nuxt-link :to="localePath({ name: 'likes' })">
      <a-button>
        {{ $t('basket.blocs.check-like') }}
      </a-button>
    </nuxt-link>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

import AButton from '~/components/elements/button';

import { Head } from '~/types';

export default Vue.extend({
  name: 'Basket',
  components: {
    AButton,
  },
  head(): Head {
    return {
      title: this.$t('basket.title').toString(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('basket.description').toString(),
        },
      ],
    };
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

.basket {
  text-align: center;
}
</style>

<i18n src="./basket.i18n.yml" lang="yaml" />
