<template>
  <header class="header">
    <div class="header__content">
      <a class="header__link" href="">
        <img class="header__logo" src="../../../public/logo.png" alt="" />
      </a>
      <div class="header__burger-menu">
        <BurgerMenu />
      </div>
    </div>
  </header>
</template>

<script>
import BurgerMenu from "../Burger-menu/Burger-menu.vue";
export default { components: { BurgerMenu } };
</script>

<style scoped>
.header {
  text-align: center;
}
.header__logo {
  margin-top: 20px;
}
</style>