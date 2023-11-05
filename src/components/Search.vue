<template>
  <div class="mt-5 flex gap-4">
    <input
      type="text"
      class="bg-slate-800 text-white p-2 w-80 rounded-2xl"
      placeholder="Digite o usuário do GitHub"
      v-model="username"
    />
    <button class="bg-indigo-600 text-white p-4 rounded-2xl" @click="fetchUser">
      Pesquisar
    </button>
  </div>
  <Card v-if="user.name" :user="user" />
</template>

<script setup>
import { reactive, ref } from "vue";
import Card from "./Card.vue";

const username = ref("");
const user = reactive({
  name: "",
  login: "",
  bio: "",
  avatarURL: "",
});

const fetchUser = async () => {
  const result = await fetch(`https://api.github.com/users/${username.value}`);
  const data = await result.json();

  Object.assign(user, {
    name: data.name,
    login: data.login,
    bio: data.bio,
    avatarURL: data.avatar_url,
  });
};
</script>
