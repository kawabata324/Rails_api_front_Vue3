<template>
  <div class="home">
    <ul v-for="data in dataList" :key="data.id">
      <li>
        <label>id</label>
        {{ data.id }}
        <label>name</label>
        {{ data.name }}
        <label>email</label>
        {{ data.email }}
        <label>age</label>
        {{ data.age }}
        <label>password</label>
        {{data.password}}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { reactive } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import Client from '../api/client'


interface User {
  id: number;
  name: string;
  email: string;
  password: string;
  created_at: Date;
}

export default defineComponent({
  name: "Home",
  setup() {
    let dataList: User[] = reactive([]);

    onMounted(() => {
      Client.get('/users').then((res) => {
        res.data.forEach((element: User) => {
          dataList.push(element);
        });
      });
    });
    return {
      dataList,
    };
  },
});
</script>
