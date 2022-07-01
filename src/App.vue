<template>
  <div id="app">
    <MainHeader />
    <main class="main">
      <router-view/>
    </main>
    <MainFooter />
  </div>
</template>

<script>
import MainHeader from '@/components/header/MainHeader';
import MainFooter from '@/components/footer/MainFooter';
export default {
  components: {
    MainHeader,
    MainFooter,
  }
}
</script>

<style lang="scss">
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}
</style>
