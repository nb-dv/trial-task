<template>
  <header class="header">
    <div class="header__container container">
      <div class="header__inner">
        <div class="header__logo">
          <img src="@/assets/images/header/logo.svg" alt="logo">
        </div>
        <div class="header__contacts contacts">
          <a class="contacts__tel" href="tel:8 800 000 00 00">8 800 000 00 00</a>
          <a class="contacts__email" href="mailto:sales@logo.ru">sales@logo.ru</a>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'MainHeader',
}
</script>

<style scoped lang="scss">
.header {
  padding: 29px 0;
  background-color: $white;;
  &__inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  &__logo {
    width: 120px;
    height: 30px;
  }
}
.contacts {
  display: flex;
  align-items: center;
  justify-content: space-between;
  & > a:last-child {
    margin-left: 40px;
  }
}
</style>
