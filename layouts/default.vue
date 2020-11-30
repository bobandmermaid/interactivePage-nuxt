<template>
  <div class="content">
    <aside-menu />
    <div class="content__body">
      <header-box />
      <nuxt />
    </div>
  </div>
</template>

<script>
import AsideMenu from '@/components/AsideMenu';
import Header from '@/components/Header';
export default {
  components: {
    'header-box': Header,
    'aside-menu': AsideMenu,
  },
};
</script>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.content {
  display: flex;
  max-width: 1024px;
  margin: 0 auto;
}

.content__body {
  padding: 30px;
  flex-grow: 1;
}
</style>
