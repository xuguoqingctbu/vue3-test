<template>
  <h1>一个人的信息</h1>
  <h2>当前SUM的值为：{{ sum }}</h2>
  <button @click="sum++">点击SUM加1</button>
  <hr />
</template>

<script>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from "vue";
export default {
  name: "Demo",
  setup() {
    //数据
    let sum = ref(0);
    console.log("-----setup-----");
    onBeforeMount(() => {
      console.log("-------- onBeforeMount--------");
    });
    onMounted(() => {
      console.log("-------- onMounted---------");
    });
    onBeforeUpdate(() => {
      console.log("----------onBeforeUpdate---------");
    });
    onUpdated(() => {
      console.log("---------- onUpdated--------");
    });
    onBeforeUnmount(() => {
      console.log("-----------onBeforeUnmount----------");
    });
    onUnmounted(() => {
      console.log("---------onUnmounted----------");
    });
    return {
      sum,
    };
  },
  beforeCreate() {
    console.log("@@@@@@@@@@@@-------------beforeCreate");
  },
  created() {
    console.log("@@@@@@@@@@@@-------------created");
  },
  beforeMount() {
    console.log("@@@@@@@@@@@@---------beforeMount");
  },
  mounted() {
    console.log("@@@@@@@@@@@@-----------mounted");
  },
  beforeUpdate() {
    console.log("@@@@@@@@@@@@---------beforeUpdate");
  },
  updated() {
    console.log("@@@@@@@@@@@@---------updated");
  },
  beforeUnmount() {
    console.log("@@@@@@@@@@@@----------beforeUnmount");
  },
  unmounted() {
    console.log("@@@@@@@@@@@@----------unmounted");
  },
};
</script>

<style></style>
