<template>
  <section class="hero">
      <div class="hero__slider">
        <div class="swiper-container" ref="bannerSwiper">
          <div class="swiper-wrapper" >
            <div
              class="swiper-slide hero__slide"
              v-for="banner in banners"
              :key="banner.id"
            >
              <div class="container ">
                <div class="hero__banner banner">
                  <div class="banner__info">
                    <h1 class="banner__header">{{ banner.header }}</h1>
                    <p class="banner__text">{{ banner.text }}</p>
                    <a href="/" class="banner__link">
                      Подробнее
                    </a>
                  </div>
                  <div class="banner__image" >
                    <img src="@/assets/images/main/slider-1.png">
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="container slider__container">
            <div class="swiper-pagination banner__pagination"></div>
          </div>
        </div>
      </div>
  </section>

</template>

<script>
import {Swiper,  Navigation, Pagination } from 'swiper'
import 'swiper/css'
import 'swiper/css/navigation'
import 'swiper/css/pagination'

export default {
  name: 'SliderComponent',
  components: Swiper,
  data() {
    return {
      banners: [
        {
          id: 1,
          image: '@/assets/images/main/slider-img.png',
          header: 'Как бизнесу сохранять IT-кадры на фоне кризиса',
          text: 'Инструменты, которые могут использовать компании для удержания сотрудников',
        },
        {
          id: 2,
          image: '@/assets/images/main/slider-img.png',
          header: 'Как бизнесу сохранять IT-кадры на фоне кризиса',
          text: 'Инструменты, которые могут использовать компании для удержания сотрудников',
        },
        {
          id: 3,
          image: '@/assets/images/main/slider-img.png',
          header: 'Как бизнесу сохранять IT-кадры на фоне кризиса',
          text: 'Инструменты, которые могут использовать компании для удержания сотрудников',
        },
      ]
    }
  },
  mounted() {
    new Swiper(this.$refs.bannerSwiper, {
      modules: [Navigation, Pagination],
      slidesPerView: 1,
      loop: true,
      navigation: {
        nextEl: '.swiper-button-next',
        prevEl: '.swiper-button-prev',
      },
      pagination: {
        el: ".swiper-pagination",
        clickable: true,
        bulletClass: `swiper-pagination-bullet swiper-pagination-custom`
      },
      scrollbar: {
        el: '.swiper-scrollbar',
      },
    })
  },
}
</script>

<style scoped lang="scss">
.hero {
  width: 100%;
  margin-top: 88px;
  background: linear-gradient(100.68deg,#5991ff 13.6%,#0050ef 94.69%);
  &__slider {
    position: relative;
    width: 100%;
    height: 546px;
    @include phone {
      height: 365px;
    }
  }
  &__slide {
    height: 100%;
  }
}
.banner {
  display: flex;
  width: 100%;
  height: 546px;
  &__pagination {
    bottom: 64px;
    left: 15px;
    width: auto;
    @include phone {
      bottom: 197px;
    }
  }
  &__info {
    flex-direction: column;
    margin-top: 10%;
    max-width: 574px;
    @include phone {
      max-width: 318px;
      margin-top: 20px;
    }
  }
  &__header {
    color: $white;
    font-weight: 600;
    font-size: 40px;
    line-height: 56px;
    margin: 0;
    @include phone {
      font-size: 20px;
      line-height: 24px;
    }
  }
  &__text {
    margin-top: 24px;
    margin-bottom: 32px;
    color: $white;
    @include phone {
      font-size: 14px;
      line-height: 22px;
    }
  }
  &__image {
    position: absolute;
    bottom: -4px;
    right: 0;
    width: 50%;
    max-width: 650px;
    @include phone {
      bottom: 177px;
    }
    & > img {
      position: relative;
      bottom: 0;
      right: 0;
      width: 100%;
      height: 100%;
    }
    @include small-tablet {
      width: 60%;
    }
  }
  &__link {
    display: inline-block;
    padding: 16px 32px;
    color: $blue-color;
    background: $white;
    font-weight: 600;
    -webkit-border-radius: 10px;
    -moz-border-radius: 10px;
    border-radius: 10px;
    @include phone {
      padding: 14px 24px;
    }
  }

}
.slider__container {
  position: relative;
}
</style>
