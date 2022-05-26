<template>
 <div>
  {{ items }}
 </div>
</template>

<script>
export default {
  name: ExpensesList,
  props: {
    items: {
      type: Array,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
