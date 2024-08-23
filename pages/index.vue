<script setup lang="ts">
const listNews:any=ref([]);
const {data}= await useFetch('https://reanweb.com/api/teaching/get-news.php?mid=0');
listNews.value=JSON.parse(data.value as string);
useHead({
    titleTemplate:' Rin News',
    })
</script>
<template>
    <div class="w-[90%] mx-auto">
        <div class="grid gap-6 mb-8 md:grid-cols-2 lg:grid-cols-4 mt-3">
            <div class="w-full h-full" v-for="l in listNews" :key="l.id">
                <div class="w-full h-full" @click="$router.push(`/detail/${l.id}`)">
                   <div class="h-2/3 bg-red-500">
                    <img :src="l.img" alt="" class="w-full h-full object-cover">
                </div>
                <div class="h-1/3 bg-blue-500">
                    <h1 class="p-2 font-bold">{{l.title}}</h1>
                </div> 
                </div>
            </div>
        </div>
    </div>
</template>
