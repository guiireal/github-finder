<template>
  <div
    class="bg-slate-800 mt-12 flex flex-col items-center border border-indigo-600 rounded-3xl w-96"
  >
    <img
      class="w-40 h-40 rounded-full mx-auto mt-4"
      :src="user.avatarURL"
      alt="Github user"
    />
    <h1 class="text-white font-semibold px-5">{{ user.name }}</h1>
    <h2 class="text-white font-semibold px-5 py-4">@{{ user.login }}</h2>
    <p class="text-white max-w-md px-5 pt-2 pb-5">
      {{ user.bio }}
    </p>
  </div>
</template>

<script setup>
defineProps({
  user: {
    type: Object,
    required: true,
  },
});
</script>
