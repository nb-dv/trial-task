<template>
  <div>
    <SliderComponent />
    <ArticlesBlock />
  </div>
</template>

<script>
import ArticlesBlock from '@/components/main/ArticlesBlock';
import SliderComponent from '@/components/main/SliderComponent';

export default {
  name: 'MainPage',
  components: {
    ArticlesBlock,
    SliderComponent,
  },
}
</script>
