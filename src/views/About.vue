<template>
  <div class="create container">
    <h1>新規作成</h1>
    <form class="flex flex-col" @submit.prevent="createUser">
      <div>
        <label>name</label>
        <input class="focus:ring-indigo-500 focus:border-indigo-500 flex-1 block w-full rounded-none rounded-r-md sm:text-sm border-gray-300" type="name" v-model="name">
      </div>
      <div>
        <label>email</label>
        <input class="focus:ring-indigo-500 focus:border-indigo-500 flex-1 block w-full rounded-none rounded-r-md sm:text-sm border-gray-300" type="email" v-model= "email">
      </div>
      <div>
        <label>password</label>
        <input class="focus:ring-indigo-500 focus:border-indigo-500 flex-1 block w-full rounded-none rounded-r-md sm:text-sm border-gray-300" type= "string" v-model="password">
      </div>
      <input type="submit" value="送信">
    </form>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "@vue/runtime-core"
import Client from '../api/client';

export default defineComponent({
  setup() {
    const name = ref('')
    const email = ref('')
    const password = ref('')
    const createUser = ()=>{
      Client.post('/users', {user: {name: name.value, email: email.value, password: password.value}}).then((res)=>{
        name.value = ''
        email.value = ''
        password.value = ''
        console.log(res.data)
      })
    }
    return{
      createUser,
      name,
      email,
      password
    }
  },
})
</script>
