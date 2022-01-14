<template>
  <h1>一个人的信息</h1>
  <h2>当前SUM的值为：{{ sum }}</h2>
  <button @click="sum++">点击SUM加1</button>
  <hr />
  <h2>当前信息为：{{ msg }}</h2>
  <button @click="msg += '!'">修改msg</button>
  <hr />
  <h3>当前此人的名字为：{{ person.name }}</h3>
  <h3>当前此人的年龄为：{{ person.age }}</h3>
  <h3>当前此人的薪水为：{{ person.job.j1.salary }}</h3>
  <button @click="person.name += '~'">修改姓名</button>
  <button @click="person.age++">增长年龄</button>
  <button @click="person.job.j1.salary++">涨薪</button>
</template>

<script>
import { reactive, ref } from "@vue/reactivity";
import { watch } from "@vue/runtime-core";
export default {
  name: "Demo",
  setup() {
    let sum = ref(0);
    let msg = ref("你好啊");
    let person = reactive({
      name: "张三",
      age: 18,
      job: {
        j1: {
          salary: 20,
        },
      },
    });

    //情况一：监视ref所定义的一个响应式数据
    watch(
      sum,
      (newValue, oldValue) => {
        console.log(`sum的值变化了,新值为:${newValue},旧值为：${oldValue}`);
      },
      { immediate: true }
    );
    //情况二：监视ref所定义的多个响应式数据
    watch(
      [sum, msg],
      (newValue, oldValue) => {
        console.log("sum或msg变了", newValue, oldValue);
      },
      { immediate: true }
    );
    /* 
				情况三：监视reactive所定义的一个响应式数据的全部属性
						1.注意：此处无法正确的获取oldValue,获取的oldValue也是新的值
						2.注意：强制开启了深度监视（deep配置无效）
			*/
    watch(
      person,
      (newValue, oldValue) => {
        console.log("person的值被修改了！！", newValue, oldValue);
      },
      { deep: true }
    );
    //情况四：监视reactive所定义的一个响应式数据中的某个属性
    watch(
      () => person.age,
      (newValue, oldValue) => {
        console.log("person中的age被修改了！！", newValue, oldValue);
      }
    );
    //情况五：监视reactive所定义的一个响应式数据中的某些属性
    watch([() => person.name, () => person.age], (newValue, oldValue) => {
      console.log("person中的age,name被修改了", newValue, oldValue);
    });
    //特殊情况
    watch(
      () => person.job,
      (newValue, oldValue) => {
        console.log("person的job被修改了！！！", newValue, oldValue);
      },
      { deep: true }
      //此处由于监视的是reactive素定义的对象中的某个属性，所以deep配置有效
    );
    return {
      sum,
      msg,
      person,
    };
  },
};
</script>

<style></style>
