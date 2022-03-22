<template>
  <ul>
    <li class="li_1"></li>
    <li class="li_2"></li>
    <li class="li_3"></li>
  </ul>
  <teleport :to="body">
    <img src="https://img0.baidu.com/it/u=3077713857,1222307962&fm=26&fmt=auto&gp=0.jpg" />
  </teleport>
  <div class="btnGroup">
    <button @click="target = '.li_1'">传送1</button>
    <button @click="target = '.li_2'">传送2</button>
    <button @click="target = '.li_3'">传送3</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';
const target = ref('.li_1');
console.log(target);
</script>

<style></style>
