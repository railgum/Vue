<template>
  <div class="costList">
    <div class="itemTitle">
      <div>#</div>
      <div>Date</div>
      <div>Category</div>
      <div>Value</div>
    </div>
    <div
      class="listItem"
      v-for="(item, index) in items"
      :key="index"
    >
      <div>{{ index+1 }}</div>
      <div>{{ item.date}}</div>
      <div>{{item.category}}</div>
      <div>{{ item.value}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CostList",
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
};
</script>
<style lang="scss" scoped>
.costList {
  width: 45%;
  height: 500px;
  //margin-left: 30px;
  text-align: left;
  .itemTitle {
    margin-top: 40px;
    display: flex;
    padding-left: 20px;
    border-bottom: 1px solid black;
    height: 40px;
    font-weight: bolder;
    div:nth-child(n + 2) {
      width: 100px;
      margin-left: 50px;
    }
  }
  .listItem {
    display: flex;
    padding-left: 20px;
    border-bottom: 1px solid black;
    height: 40px;
    align-items: center;
    div:nth-child(n + 2) {
      width: 100px;
      margin-left: 50px;
    }
  }
}
</style>