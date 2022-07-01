<template>
  <header class="header">
    <div class="header__container container">
      <div class="header__inner">
        <div class="header__logo">
          <img src="@/assets/images/header/logo.svg" alt="logo">
        </div>
        <div class="header__contacts contacts">
          <a class="contacts__tel" href="tel:8 800 000 00 00">8 800 000 00 00</a>
          <a class="contacts__tel--mobile" href="tel:8 800 000 00 00">
            <img src="@/assets/images/header/phone-mobile.svg" alt="8 800 000 00 00">
          </a>
          <a class="contacts__email" href="mailto:sales@logo.ru">sales@logo.ru</a>
          <a class="contacts__email--mobile" href="mailto:sales@logo.ru">
            <img src="@/assets/images/header/mail-mobil.svg" alt="sales@logo.ru">
          </a>
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
  position: fixed;
  z-index: 1000;
  width: 100%;
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
  &__tel {
    @include phone {
      display: none;
    }
  }
  &__tel--mobile {
    display: none;
    @include phone {
      display: block;
    }
  }
  &__email {
    margin-left: 40px;
    @include phone {
      display: none;
    }
  }
  &__email--mobile {
    display: none;
    margin-left: 20px;
    @include phone {
      display: block;
    }
  }
}
</style>
