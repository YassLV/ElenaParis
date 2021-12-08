<template>
  <main>
    <div class="content-article">
      <div class="pictures-container">
        <div v-for="(el, key) in selectPictures()" :key="key">
          <img :src="require(`@/assets/images/images/template/${el}.jpg`)" :alt="`${el}-icon`" />
        </div>
      </div>
      <div class="description-container">
        <h1>{{ selectTitle() }}</h1>
        <div class="size">
          {{ $t('article.blocs.your-size') }}
        </div>
        <div class="container-purchase">
          <a-button disabled>
            {{ $t('article.blocs.add-basket') }}
          </a-button>
          <div class="heart">
            <img class="tablet-logo" src="~/assets/images/svg/heart-icon.svg" alt="elena-icon" />
          </div>
        </div>
        <p class="conditions">{{ $t('article.blocs.conditions')}} </p>
        <div class="more">
          <description-block title="Description" description="Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum. Stet clita kasd gubergren, no sea takimata sanctus est Lorem ipsum dolor sit amet. Lorem ipsum dolor sit amet, consetetur sadipscing elitr, sed diam nonumy eirmod tempor invidunt ut labore" />
          <description-block title="Information taille & coupe" description=" invidunt ut labore et dolore magna aliquyam erat, sed diam voluptua. At vero eos et accusam et justo duo dolores et ea rebum." />
        </div>
      </div>
    </div>
    <advantages-section />
  </main>
</template>

<script lang="ts">
import Vue from 'vue';

import { Context } from '@nuxt/types';
import AdvantagesSection from '~/components/sections/advantages-section.vue';
import DescriptionBlock from "~/components/elements/description-block/description-block.vue";
import { ARTICLE_ENPOINTS } from '~/types/article/enums';
import AButton from '~/components/elements/button';

import { Head } from '~/types';

export default Vue.extend({
  name: 'Article',
  components: {
    DescriptionBlock,
    AdvantagesSection,
    AButton,
  },
  data() {
    return {
      man_black_pictures: [
        'template_1',
        'template_2',
        'template_3',
        'template_4'
      ],
      man_blue_pictures: [
        'template_1',
        'template_2',
        'template_3',
        'template_4'
      ],
      woman_or_pictures: [
        'template_1',
        'template_2',
        'template_3',
        'template_4'
      ],
      woman_blue_pictures: [
        'template_1',
        'template_2',
        'template_3',
        'template_4'
      ],
    };
  },
  async asyncData(context: Context): Promise<void> {

    const ALLOWED_QUERY_PARAMS = Object.values(ARTICLE_ENPOINTS);

    const { article } = context.query;

    if(!article) {
      context.redirect(context.localePath({ name: 'index' }));
    }

    if (
      !(
        (Object.values(ALLOWED_QUERY_PARAMS) as string[]).includes(article.toString())
      )
    ) {
      context.redirect(context.localePath({ name: 'index' }));
    }
  },
  methods: {
    selectPictures(): string[] {
      const { article } = this.$route.query;
      switch (article) {
        case ARTICLE_ENPOINTS.MAN_BLUE:
          return this.man_blue_pictures;
        case ARTICLE_ENPOINTS.MAN_BLACK:
          return this.man_black_pictures;
        case ARTICLE_ENPOINTS.WOMAN_BLUE:
          return this.woman_blue_pictures;
        case ARTICLE_ENPOINTS.WOMAN_OR:
          return this.woman_or_pictures;
      }
      return [];
    },
    selectTitle(): string {
      const { article } = this.$route.query;
      switch (article) {
        case ARTICLE_ENPOINTS.MAN_BLUE:
          return this.$t('article.blocs.titles.man_blue').toString();
        case ARTICLE_ENPOINTS.MAN_BLACK:
          return this.$t('article.blocs.titles.man_black').toString();
        case ARTICLE_ENPOINTS.WOMAN_BLUE:
          return this.$t('article.blocs.titles.woman_blue').toString();
        case ARTICLE_ENPOINTS.WOMAN_OR:
          return this.$t('article.blocs.titles.woman_or').toString();
      }
      return '';
    }
  },
  head(): Head {
    return {
      title: this.selectTitle(),
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$t('article.description').toString(),
        },
      ],
    };
  },
});
</script>


<style scoped lang="scss">
@import 'assets/css/vars';

.content-article {
  margin: $size-extra-large * 2 0;
  .pictures-container div img {
    width: 100%;
  }
  .description-container {
    margin: 0 $size-small $size-small;

    h1 {
      font-size: $size-large;
      font-weight: normal;
    }
    .size {
      margin-top: $size-large;
      border: 1px solid $black;
      border-radius: 50px;
      padding: $size-normal $size-extra-large * 2;
      position: relative;
      &:after {
        position: absolute;
        top: 50%;
        right: 50px;
        transform: translateY(-50%);
        content: '\02C5';
        font-weight: bold;
      }
    }
    .container-purchase {
      .e-button {
        width: 100%;
      }
      .heart {
        border-radius: 50px;
        height: 50px;
        border: 1px solid $black;
        width: 100%;
        text-align: center;
        padding-top: $size-normal;
      }
    }
    .conditions {
      margin: $size-large 0;
    }
    .more {
      div:first-child {
        margin-bottom: $size-large;
      }
    }
  }
}

@media screen and(min-width: $tablet) {
  .content-article {
    padding: 0 10%;
    display: grid;
    grid-template-columns: 1.5fr 1fr;
    grid-auto-rows: auto;
    grid-gap: $size-extra-large * 2;
    .description-container {
      .container-purchase {
        display: grid;
        grid-template-columns: 70% 10%;
        grid-auto-rows: auto;
        grid-gap: $size-normal;
        justify-content: center;
        align-items: center;
        .heart {
          width: 50px;
        }
      }
    }
    .pictures-container {
      display: grid;
      grid-template-columns: repeat(2, 50%);
      grid-auto-rows: auto;
      grid-gap: $size-small;
      :first-child {
        grid-column: 1 / 3;
      }
    }
  }
}
</style>

<i18n src="./article.i18n.yml" lang="yaml" />
