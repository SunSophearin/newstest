<script setup lang="ts">
const { data } = await useFetch(
  "https://reanweb.com/api/teaching/get-menu.php"
);
const menu = JSON.parse(data.value as string);
const menuGlobo=useState("menuGlobo",()=>menu);

</script>
<template>
  
  <div class="container bg-black text-white sticky left-0 top-0">
    <ul class="flex p-5 gap-6 w-[90%] mx-auto">
      <li class="hover:text-red-500 cursor-pointer font-bold transform duration-300">
        <NuxtLink to="/">HOME</NuxtLink>
      </li>
      <li 
      class="hover:text-red-500 cursor-pointer font-bold transform duration-300"
      v-for="(m, i) in menu" :key="i">
        <NuxtLink :to="`/category/${m.id}`">{{ m.name }}</NuxtLink>
        
      </li>
    </ul>
  </div>
</template>
<style scoped>
.router-link-active{
  color: red;
}
</style>
