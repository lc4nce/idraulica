<script setup>
const route = useRoute()

const { data } = await useFetch(
    "http://127.0.0.1:3001/api/review/"
);
</script>
<template>
    <div >
        <div v-for="obj in data.response">
            <v-card
                class="m-2"
                :title="obj.product_name"
                :text="obj.body"
                variant="tonal"
            >
                <v-card-actions>
                    <NuxtLink :to="obj.product_type + '/' + obj.product_name"
                        ><v-btn>Leggi la recensione</v-btn></NuxtLink
                    >
                </v-card-actions>
            </v-card>
        </div>
    </div>
</template>
