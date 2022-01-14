<template>
  <div class="app">
    我是App 组件
    <Child />
  </div>
</template>

<script>
import Child from "@/components/Child";
import { reactive, toRefs, provide } from "vue";
export default {
  name: "App",
  components: { Child },
  setup() {
    let car = reactive({ name: "奔驰", price: "40万" });
    provide("car", car); //给自己的后代组件传递数据
    return {
      ...toRefs(car),
    };
  },
};
</script>

<style scoped>
.app {
  background-color: blueviolet;
  padding: 50px 0px;
}
</style>
