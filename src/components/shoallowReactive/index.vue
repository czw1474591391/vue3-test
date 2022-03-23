<template>
  <div v-if="isShow">
    <!-- <h3>{{ person }}</h3> -->
    <h3>{{ person1.age }}</h3>
    <button @click="person.name += '-'">改变姓名</button>
    <button @click="person.job.age++">改变深层次对象</button>
    <button @click="changeShallowRef">改变shallowref对象</button>
  </div>
</template>

<script setup>
import { shallowReactive, shallowRef, triggerRef, defineProps } from 'vue';

defineProps({
  isShow: {
    type: Boolean,
    default: true
  }
});
// shallowReactive只监听浅层次对象(对象第一层属性)，非递归监听
const person = shallowReactive({
  name: '张三',
  job: {
    age: 18
  }
});
const person1 = shallowRef({
  age: 18
});
function changeShallowRef() {
  person1.value.age = 20;
  triggerRef(person1);
  // 对于 shallow 过的 ref 对象，我们还可以手动去触发 ref 的变化监听事件来实现界面的改变
}
</script>

<style></style>
