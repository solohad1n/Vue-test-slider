<template>
  <div class="burger-menu">
    <span></span>
    <span></span>
    <span></span>
  </div>
</template>

<script>
export default {};
</script>

<style>
.burger-menu {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 60px;
  height: 20px;
  cursor: pointer;
  transform: translateY(-70%);
}

.burger-menu span {
  display: inline-block;
  width: 18px;
  border: 1px solid #333333;
  margin-bottom: 4px;
}
</style>