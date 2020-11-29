<template>
  <div class="tab" v-show="tabSelected">
    <slot />
  </div>
</template>

<script>
export default {
  name: 'Tab',
  props: {
    title: {
      type: String,
      required: true,
    },
    selected: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      tabSelected: false,
    };
  },
  mounted() {
    this.tabSelected = this.selected;
  },
};
</script>

<style scoped></style>
