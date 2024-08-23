<script setup lang="ts">
const listNews:any=ref([]);
const route=useRoute();
const menuGlobo=useState<any>("menuGlobo");

const {data}= await useFetch(`https://reanweb.com/api/teaching/get-news.php?mid=${route.params.id}`);
listNews.value=JSON.parse(data.value as string);

//head title
if(menuGlobo.value.find((m:any)=>m.id==route.params.id)){
    const handleHeaders=menuGlobo.value.find((m:any)=>m.id==route.params.id)
    console.log(handleHeaders)
    useHead({
    titleTemplate: handleHeaders.name+' - Rin News',
    })
}

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
