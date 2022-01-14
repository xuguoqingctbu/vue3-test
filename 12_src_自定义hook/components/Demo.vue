<template>
  <h1>一个人的信息</h1>
  <h2>当前SUM的值为：{{ sum }}</h2>
  <button @click="sum++">点击SUM加1</button>
  <hr />
  <h3>当前点的坐标为x：{{ point.x }},y:{{ point.y }}</h3>
</template>

<script>
import { ref } from "vue";
import userPoint from "../hooks/usePoint";
export default {
  name: "Demo",
  setup() {
    //数据
    let sum = ref(0);
    let point = userPoint();
    return {
      sum,
      point,
    };
  },
};
</script>

<style></style>
