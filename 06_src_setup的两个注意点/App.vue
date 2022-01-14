<template>
  <Demo @hello="showHelloMsg" msg="hello" school="上海校区">
    <span>test</span>
    <template v-slot:list>
      <ul >
        <li>李四</li>
        <li>张三</li>
      </ul>
    </template>

    <template v-slot:qwd>
      <span>上海地区</span>
    </template>
    <template v-slot:sad>
      <span>上海地区2</span>
    </template>
  </Demo>
</template>

<script>
import Demo from "./components/Demo";

export default {
  name: "App",
  components: { Demo },
  setup() {
    function showHelloMsg(value) {
      console.log(`你触发了hello自定义事件！,我收到的参数为:${value}`);
    }
    //返回一个对象（常用）
    return { showHelloMsg };
  },
};
</script>

<style></style>
