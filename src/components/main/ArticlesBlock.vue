<template>
  <section class="articles">
    <div class="articles__container container">
      <div class="articles__filters">
        <FilterByName :authors="allAuthors" @sortingArticles="sortingArticles" class="articles__filter"/>
        <FilterByDate @filteringArticles="filteringArticles" class="articles__filter"/>
      </div>
      <div class="articles__items">
        <div class="articles__empty" v-if="!sortArticles.length">
          В указанные даты статей нет :(
          <span>Все статьи опубликованы 25.04.2022</span>
        </div>
        <article
          class="articles__item article"
          v-for="(article, i) in sortArticles"
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
  </section>
</template>

<script>
import axios from 'axios';
import FilterByName from '@/components/main/FilterByName';
import FilterByDate from '@/components/main/FilterByDate';

export default {
  name: 'ArticlesBlock',
  components: {
    FilterByName,
    FilterByDate,
  },
  data() {
    return {
      articles: [],
      allAuthors: [],
      sortArticles: [],
    }
  },
  methods: {
    filteringArticles(startDate, endDate) {
      this.sortArticles = this.filterCoursesByPriceRange(this.articles, startDate, endDate)
    },
    filterCoursesByPriceRange(articles, startDate, endDate) {
      const dateToNumber = date => date === '' ? 0 : new Date(date.toString()).getTime() +
        new Date(date.toString()).getTime() + new Date(date.toString()).getTime() ;
      return articles.filter(article => {
        return (dateToNumber(article.publishedAt)) >= dateToNumber(startDate)  &&
          (endDate !== '' ? dateToNumber(article.publishedAt) <= dateToNumber(endDate) : true);
      })
    },
    sortingArticles(author) {
      (author === 'Выбор автора') ? this.sortArticles = [...this.articles] : this.sortArticles = this.articles.filter(article => article.author === author);
    },
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
        this.articles = res.data.articles;
        this.sortArticles = res.data.articles;
      })
      .finally(() => {
        if (this.articles.length) {
          this.articles.forEach(article => {
            if (article.author !== null && !this.allAuthors.includes(article.author)) {
              this.allAuthors.push(article.author);
            }
          })
        }
      })
    },
  },
  mounted() {
    this.getArticlesData();
  },
}
</script>

<style scoped lang="scss">
.articles {
  &__items {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  &__empty {
    margin-bottom: 30px;
    & > span {
      display: block;
      margin-top: 20px;
      font-size: 12px;
      color: $grey-color;
    }
  }
  &__filters {
    position: sticky;
    top: 88px;
    display: flex;
    align-items: center;
    padding: 40px 0 56px 0 ;
    background-color: $main-bg;
    @include tablet {
      flex-direction: column;
    }
  }
  &__filter {
    &:first-child {
      margin-right: 20px;
      @include tablet {
        margin-bottom: 16px;
        margin-right: 0;
      }
    }
    @include tablet {
      width: 100%;
    }
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
  @include small-tablet {
    width: 100%;
  }
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
