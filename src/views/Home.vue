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
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { reactive } from "@vue/reactivity";
import { onMounted } from "@vue/runtime-core";
import axios from "axios";

interface User{
  id: number;
  name: string;
  email: string;
  age: number;
  created_at: Date;
}

export default defineComponent({
  name: "Home",
  setup() {
    let dataList: User[] = reactive([]);
    const url = "http://localhost:3004/users";
    onMounted(() => {
      axios.get(url).then((res) => {
        console.log(res.data);
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
