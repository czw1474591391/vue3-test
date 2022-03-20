<template>
  <div v-if="isShow">
    <h3>{{ age }}</h3>
    <h3>{{ name }}</h3>
    <h3>{{ person }}</h3>
    <button @click="age++">增加年龄</button>
    <button @click="name += '-'">改变名字</button>
    <button @click="person.salary++">改变person工资</button>
    <button @click="person.type = '后端开发'">改变person职位</button>
    <button @click="person.job.salary = 40">改变person内的job对象</button>
  </div>
</template>

<script setup>
import { reactive, ref, defineProps, watchEffect } from 'vue';
defineProps({
  isShow: {
    type: Boolean,
    default: true
  }
});
const age = ref(0);
const name = ref('张三');
const person = reactive({
  type: '前端开发',
  salary: 10,
  job: {
    salary: 20
  }
});

// watchEffect函数，函数内部用到哪个就监听哪个
watchEffect(() => {
  const x1 = age;
  console.log(person.job.salary);
  console.log('执行了' + x1.value);
});

// // 1、监听ref定义的多个响应式数据,immediate属性代表初始化就执行一次
// watch(
//   [age, name],
//   (newValue, oldValue) => {
//     console.log(newValue, oldValue);
//   },
//   { immediate: true }
// );

// // 2、监听reactive定义的响应式数据，oldValue无法获取（deep深度监视失败）
// watch(
//   person,
//   (newValue, oldValue) => {
//     console.log(newValue, oldValue);
//   },
//   { deep: true }
// );

// // 3、监听reactive定义的响应式数据中的某个属性(使用箭头函数)
// watch(
//   () => person.type,
//   (newValue, oldValue) => console.log(newValue, oldValue)
// );
// // 4、监听reactive定义的响应式数据中的某些属性(使用数组嵌套箭头函数)
// watch([() => person.type, () => person.salary], (newValue, oldValue) =>
//   console.log(newValue, oldValue)
// );

// // 5、特殊情况 监听reactive内的对象属性要开启deep深度检测
// watch(
//   () => person.job,
//   (newValue, oldValue) => console.log(newValue, oldValue),
//   { deep: true }
// );
</script>

<style></style>
