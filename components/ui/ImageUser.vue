<template>
  <i class="gg-user-list" />
</template>

<script>
export default {
  name: 'ImageUser',
};
</script>

<style scoped>
.gg-user-list {
  display: block;
  transform: scale(var(--ggs, 1));
  box-sizing: border-box;
  width: 26px;
  height: 36px;
}
.gg-user-list::after,
.gg-user-list::before {
  content: '';
  display: block;
  box-sizing: border-box;
  position: absolute;
  border: 2px solid;
}
.gg-user-list::before {
  width: 18px;
  height: 18px;
  border-radius: 30px;
  top: 0;
  left: 5px;
}
.gg-user-list::after {
  width: 28px;
  height: 15px;
  border-bottom: 0;
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
  top: 22px;
}
</style>
