<template>
  <div class="child">
    我是child组件
    <Sun></Sun>
  </div>
</template>

<script>
import Sun from "@/components/Sun";
export default {
  name: "Child",
  components: { Sun },
};
</script>

<style scoped>
.child {
  background-color: brown;
  padding: 30px 0px;
}
</style>
