<template>
{{ items }}
</template>

<script>
export default {
  name: "ExpenseList",
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<style lang="scss" scoped>
</style>