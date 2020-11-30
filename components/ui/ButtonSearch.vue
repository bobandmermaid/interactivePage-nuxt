<template>
  <button class="gg-search" type="submit" />
</template>

<script>
export default {
  name: 'ButtonSearch',
};
</script>

<style scoped>
.gg-search {
  position: absolute;
  top: 13px;
  right: 10px;
  cursor: pointer;
  box-sizing: border-box;
  display: block;
  transform: scale(var(--ggs, 1));
  width: 16px;
  height: 16px;
  border: 2px solid;
  border-radius: 100%;
  margin-left: -4px;
  margin-top: -4px;
  background-color: transparent;
  color: #aeaeae;
  outline: none;
}
.gg-search::after {
  content: '';
  display: block;
  box-sizing: border-box;
  position: absolute;
  border-radius: 3px;
  width: 2px;
  height: 8px;
  background: currentColor;
  transform: rotate(-45deg);
  top: 10px;
  left: 12px;
}
</style>
