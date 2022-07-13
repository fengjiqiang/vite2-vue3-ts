<template>
  <h1>{{ msg }}</h1>
  <div>用户名:{{ mainStore.name }}<br />长度:{{ mainStore.nameLength }}</div>
  <button @click="updateName">修改store中的name</button>
  <hr />
  <n-button class="button-custom" @click="updateName2">修改store中的name2</n-button>
</template>

<script setup lang="ts">
import { useMainStore } from '@/store/main'
import { NButton } from "naive-ui"
defineProps<{ msg: string }>()

const mainStore = useMainStore()

const updateName = ()=>{
  // $patch 修改 store 中的数据
  mainStore.$patch({
    name: '名称被修改了,nameLength也随之改变了'
  })
}
const updateName2 = ()=>{
  // $patch 修改 store 中的数据
  mainStore.$patch({
    name: '二次修改name值'
  })
}
console.log(import.meta.env.VITE_USER_NODE_ENV)
</script>

<style scoped>
.button-custom {
  background-color: #216BFF;
  color: #ffffff;
  border-radius: 4px;
}
</style>
