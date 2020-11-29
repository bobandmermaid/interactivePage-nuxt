<template>
  <div class="tabs">
    <ul class="tabs__list">
      <li
        v-for="(tab, index) in tabs"
        :key="index"
        :class="{ tabs__selected: tab.tabSelected }"
      >
        <a class="tabs__link" :href="tab.href" @click="selectTab(tab)">{{
          tab.title
        }}</a>
      </li>
    </ul>
    <slot />
  </div>
</template>

<script>
export default {
  data() {
    return {
      tabs: [],
    };
  },
  created() {
    this.tabs = this.$children;
  },
  methods: {
    selectTab(data) {
      this.tabs.forEach((tab) => {
        tab.tabSelected = tab.title === data.title;
      });
    },
  },
};
</script>

<style scoped>
.tabs {
  margin-top: 40px;
}

.tabs__list {
  display: flex;
  list-style: none;
  padding: 0;
  margin: 0;
  border-bottom: 1px solid #cfee73;
}

li {
  flex-grow: 1;
  text-align: center;
}

li:last-child {
  margin-right: 60px;
}

.tabs__link {
  display: block;
  color: #4c9b5d;
  text-decoration: none;
  padding: 15px 0;
  cursor: pointer;
}

.tabs__selected .tabs__link {
  color: #000;
  font-weight: bold;
  border-bottom: 2px solid #cfee73;
}
</style>
