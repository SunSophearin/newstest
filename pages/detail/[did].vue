<script setup lang="ts">
const route = useRoute();
const detailNews:any=ref([""]);

//get data from api
const {data }= await useFetch(`https://reanweb.com/api/teaching/get-news-detail.php?id=${route.params.did}`);
detailNews.value=JSON.parse(data.value as string)

//SEO META 
useSeoMeta({
  title: detailNews.value.title,
  ogTitle: detailNews.value.title,
  description: detailNews.value.des,
  ogDescription: detailNews.value.des,
  ogImage: detailNews.value.img,
  twitterCard: detailNews.value.img,
})
</script>

<template>
    <div class="container">
        <div v-html="detailNews.des" class="w-[50%] mx-auto"></div>
    </div>
    
</template>