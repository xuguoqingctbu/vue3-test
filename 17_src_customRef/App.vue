<template>
  <input type="text" v-model="keyWord" />
  <h3>keyword:{{ keyWord }}</h3>
</template>

<script>
import { customRef } from "@vue/reactivity";
export default {
  name: "App",
  setup() {
    //自定义一个ref——名为：myRef，实现延迟加载
    function myRef(value, delay) {
      // eslint-disable-next-line no-unused-vars
      let timer;
      return customRef((track, trigger) => {
        return {
          get() {
            console.log(`有人从myRef这个容器中读取数据了，我把${value}给他了`);
            track();
            return value;
          },
          set(newValue) {
            console.log(`有人从myRef这个容器中修改数据了，修改值为${newValue}`);
            clearTimeout(timer);
            timer = setTimeout(() => {
              value = newValue;
              trigger();
            }, delay);
          },
        };
      });
    }
    // let keyWord = ref("");
    let keyWord = myRef("张三", 1000);
    return {
      keyWord,
      myRef,
    };
  },
};
</script>

<style></style>
