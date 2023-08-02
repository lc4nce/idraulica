<script setup>
const route = useRoute()
const { data } = await useFetch(
    "http://127.0.0.1:3001/api/review/show?product_name=" + route.params.product_name
);
console.log(route.params)

</script>
<template>
   <p>{{ data }}</p>
</template>
