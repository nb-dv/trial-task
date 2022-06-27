<template>
  <div class="articles">
    <div class="articles__container container">
      <div class="articles__filters"></div>
      <div class="articles__items">
        <article
          class="articles__item article"
          v-for="(article, i) in articles"
          :key="i"
        >
          <router-link to="{name: 'main'}">
            <span class="article__date">{{ formatDate(article.publishedAt) }}</span>
            <h2 class="article__title">{{ article.title }}</h2>
            <p class="article__content">
              {{ article.description}}
            </p>
            <span
              class="article__author"
              v-show="article.author"
            >
              {{ article.author }}
            </span>
          </router-link>
        </article>
      </div>
    </div>
  </div>

</template>

<script>
import axios from 'axios'

export default {
  name: 'ArticlesBlock',
  data() {
    return {
      articles: [],
    }
  },
  computed: {
  },
  methods: {
    formatDate(date) {
      return new Date(date).toLocaleString('ru', {
        year: 'numeric',
        month: 'long',
        day: 'numeric',
      }).replace(/\s*г\./, '');
    },
    getArticlesData() {
      axios.get('https://mocki.io/v1/a5814d24-4e22-49fc-96d1-0e9ae2952afc')
      .then(res => {
        console.log(res.data.articles)
        this.articles = res.data.articles;
      })
    },
  },
  mounted() {
    this.getArticlesData();
  }
}
</script>

<style scoped lang="scss">
.articles {
  &__items {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
}

.article {
  width: calc(50% - 10px);
  max-width: 572px;
  padding: 24px;
  margin-bottom: 20px;
  //margin-right: 10px;
  line-height: 24px;
  background-color: $white;
  -webkit-border-radius: 20px;
  -moz-border-radius: 20px;
  border-radius: 20px;
  &__date {
    margin-bottom: 24px;
    font-size: 12px;
    font-weight: 600;
    line-height: 18px;
    color: $light-blue-color;
  }
  &__title {
    height: 64px;
    font-size: 20px;
    font-weight: 600;
    line-height: 32px;
    color: rgba(0, 0, 0, 0.65);
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
  }
  &__content {
    height: 72px;
    margin: 24px 0;
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    -webkit-box-orient: vertical;
  }
  &__author {
    display: inline-block;
    padding: 8px 20px;
    font-size: 12px;
    font-weight: 600;
    line-height: 18px;
    color: $blue-color;
    background: rgba(0, 80, 239, 0.06);
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
  }
}

</style>
