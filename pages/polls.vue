<template>
  <div class="polls">
    <tabs>
      <tab title="Параметры" :selected="true" />
      <tab title="Вопросы" />
      <tab title="Логика" />
      <tab title="Условия" />
      <tab title="Респонденты">
        <respondents :rules="poll.respondents" />
      </tab>
    </tabs>
  </div>
</template>

<script>
import Tabs from '@/components/Tabs';
import Tab from '@/components/Tab';
import Respondents from '@/components/Respondents';

export default {
  name: 'polls',
  components: {
    tabs: Tabs,
    tab: Tab,
    respondents: Respondents,
  },
  data() {
    return {
      poll: {
        respondents: [],
      },
    };
  },
};
</script>

<style scoped></style>
