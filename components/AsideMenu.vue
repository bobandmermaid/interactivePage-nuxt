<template>
  <aside class="aside">
    <button class="aside__index" />
    <ul class="aside__list">
      <li class="aside__element">
        <NuxtLink to="/polls">
          <image-document />
          {{ text.polls }}
        </NuxtLink>
      </li>
      <li class="aside__element">
        <NuxtLink to="/users">
          <image-user />
          {{ text.users }}
        </NuxtLink>
      </li>
      <li class="aside__element">
        <NuxtLink to="/blacklist">
          <image-flag />
          {{ text.blacklist }}
        </NuxtLink>
      </li>
      <li class="aside__element">
        <NuxtLink to="/callcenter">
          <image-smartphone />
          {{ text.callcenter }}
        </NuxtLink>
      </li>
    </ul>
  </aside>
</template>

<script>
import ImageDocument from '@/components/ui/ImageDocument';
import ImageUser from '@/components/ui/ImageUser';
import ImageFlag from '@/components/ui/ImageFlag';
import ImageSmartphone from '@/components/ui/ImageSmartphone';

export default {
  components: {
    ImageSmartphone,
    ImageFlag,
    ImageUser,
    ImageDocument,
  },
  data() {
    return {
      text: {
        polls: 'Опросы',
        users: 'Пользователи',
        blacklist: 'Черный лист',
        callcenter: 'Колл-центр',
      },
    };
  },
  name: 'AsideMenu',
};
</script>

<style scoped>
.aside {
  width: 160px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-right: 1px solid #f1f1f1;
}

.aside__index {
  width: 50px;
  height: 50px;
  background: #c81717;
  border-radius: 50%;
  border-style: none;
  cursor: pointer;
  margin: 30px 0 60px;
}

.aside__list {
  display: block;
  list-style: none;
  padding: 0;
  margin: 0;
}

a {
  text-decoration: none;
  color: #000;
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 90px;
  align-items: center;
  justify-content: center;
  border: 2px solid transparent;
  border-radius: 8px;
  margin-bottom: 15px;
  padding: 0 8px;
}

a:hover {
  border-color: #cfee73;
  color: #bed768;
  border-radius: 8px;
}

.nuxt-link-active {
  font-weight: bold;
  background-color: #f1f1f1;
}
</style>
