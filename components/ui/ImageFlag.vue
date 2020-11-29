<template>
  <i class="gg-flag"></i>
</template>

<script>
export default {
  name: 'ImageFlag',
};
</script>

<style scoped>
.gg-flag {
  box-sizing: border-box;
  position: relative;
  display: block;
  transform: scale(var(--ggs, 1));
  width: 24px;
  height: 36px;
  border-left: 2px solid;
}
.gg-flag::after,
.gg-flag::before {
  content: '';
  display: block;
  box-sizing: border-box;
  position: absolute;
  width: 16px;
  height: 18px;
}
.gg-flag::before {
  border-top: 2px solid;
  border-bottom: 2px solid;
}
.gg-flag::after {
  border: 2px solid;
  border-left: 0;
  top: 2px;
  left: 12px;
}
</style>
