<template>
  <div class="likes">
    <p><img src="~/assets/images/svg/likes.svg" alt="likes-icon" /></p>
    <p>{{ $t('likes.blocs.empty') }} <img src="~/assets/images/svg/smile.svg" alt="smile-icon" /></p>
    <nuxt-link :to="localePath({ name: 'basket' })">
      <a-button>
        {{ $t('likes.blocs.check-basket') }}
      </a-button>
    </nuxt-link>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';

import AButton from '~/components/elements/button';

import { Head } from '~/types';

export default Vue.extend({
  name: 'likes',
  components: {
    AButton,
  },
  head(): Head {
    return {
      title: this.$t('likes.title').toString(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('likes.description').toString(),
        },
      ],
    };
  },
});
</script>

<style scoped lang="scss">
@import 'assets/css/vars';

.likes {
  text-align: center;
}
</style>

<i18n src="./likes.i18n.yml" lang="yaml" />
