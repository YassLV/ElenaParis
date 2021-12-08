<template>
  <main>
    <h1>{{ $t('privacy-policy.blocs.title') }}</h1>
    <div>
      <h2>{{ $t('privacy-policy.blocs.privacy-policy-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.privacy-policy')" :key="key">
        {{ txt }}
      </p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.informations-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.informations')" :key="key">
        {{ txt }}
      </p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.data-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.data')" :key="key">
        {{ txt }}
      </p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.your-right-title') }}</h2>
      <p class="subtitle">{{ $t('privacy-policy.blocs.your-right') }}</p>
      <p class="list" v-for="(txt, key) in $t('privacy-policy.blocs.your-right')" :key="key">
        {{ txt }}
      </p>
      <p class="more">{{ $t('privacy-policy.blocs.your-right-more') }}</p>
      <p class="more">{{ $t('privacy-policy.blocs.your-right-more-more') }}</p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.link-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.link')" :key="key">
        {{ txt }}
      </p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.security-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.security')" :key="key">
        {{ txt }}
      </p>
    </div>
    <div>
      <h2>{{ $t('privacy-policy.blocs.divulg-title') }}</h2>
      <p v-for="(txt, key) in $t('privacy-policy.blocs.divulg')" :key="key">
        {{ txt }}
      </p>
      <div>
        <h2>{{ $t('privacy-policy.blocs.informations-contact-title') }}</h2>
        <p v-for="(txt, key) in $t('privacy-policy.blocs.informations-contact')" :key="key">
          {{ txt }}
        </p>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import Vue from 'vue';

import { Head } from '~/types';


export default Vue.extend({
  name: 'PrivacyPolicy',
  head(): Head {
    return {
      title: this.$t('privacy-policy.title').toString(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('privacy-policy.description').toString(),
        },
      ],
    };
  },
});
</script>

<style lang="scss" scoped>
@import '~assets/css/vars';

main {
  padding: 0 $size-small;
}

@media screen and(min-width: $tablet) {
  main {
    padding: 0 10%;
    .subtitle {
      margin-top: $size-normal;
    }
    .list {
      &:before {
        content: '- ';
      }
    }
  }
}
</style>

<i18n src="./privacy-policy.i18n.yml" lang="yaml" />
