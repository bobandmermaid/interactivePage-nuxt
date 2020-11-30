<template>
  <div class="header">
    <form class="search">
      <label>
        <input
          class="search__input"
          type="text"
          placeholder="Поиск по системе"
        />
      </label>
      <button-search />
    </form>
    <div class="header__profile">
      <button class="header__image" />
      <div class="header__name">
        <p class="header__title">{{ text.title }}</p>
        <p class="header__subtitle">{{ text.subtitle }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import ButtonSearch from '@/components/ui/ButtonSearch';
export default {
  components: { ButtonSearch },
  data() {
    return {
      text: {
        title: 'Alexander C.',
        subtitle: 'Администратор',
      },
    };
  },
  name: 'Header',
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
}

.search {
  position: relative;
  width: 430px;
  margin: 13px 0 0;
}

.search__input {
  width: 100%;
  height: 36px;
  padding-left: 15px;
  border: 1px solid #dbdbdb;
  border-radius: 4px;
}

.header__profile {
  display: flex;
  flex-direction: row;
  align-items: center;
}

.header__image {
  width: 60px;
  height: 60px;
  background: #4456cf;
  border-radius: 50%;
  border-style: none;
  cursor: pointer;
}

.header__name {
  display: block;
  margin-left: 10px;
}

.header__title {
  font-weight: bold;
}

.header__subtitle {
  color: #ccc;
  font-size: 14px;
}
</style>
