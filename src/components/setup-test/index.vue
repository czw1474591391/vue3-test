<template>
  <div v-if="isShow">
    <h2>{{ name }}</h2>
    <h2>{{ sex }}</h2>
    <h2>{{ info }}</h2>
    <h2>{{ number }}</h2>
    <button @click="asyWelcome">触发vue2方法</button>
    <button @click="changeIinfo">修改vue3属性</button>
    <button @click="test1">触发父组件方法</button>
    <slot name="abc"></slot>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
  name: 'setup',
  data() {
    return {
      sex: '男'
    };
  },
  methods: {
    asyWelcome() {
      alert('vue2中的方法');
    }
  },
  props: ['data', 'isShow'],
  emits: ['hello'],
  setup(prop, context) {
    // ref使用reflmpl实例对象通过get set劫持响应基本数据类型、
    // 通过es6 proxy响应引用数据类型,内部求助了”reactive“函数
    const name = ref('张三');
    const info = ref({
      type: '前端开发'
    });
    const number = reactive([1, 2, 3]);
    function changeIinfo() {
      name.value = '李四';
      info.value.type = 'java开发';
      number[0] = 666;
    }
    function test1() {
      context.emit('hello');
    }
    return {
      name,
      info,
      number,
      changeIinfo,
      test1
    };
  }
};
</script>

<style></style>
