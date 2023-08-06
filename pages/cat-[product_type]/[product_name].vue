<script setup>
const route = useRoute();
const { data } = await useFetch(
    "http://127.0.0.1:3001/api/review/show?product_name=" +
        route.params.product_name
);
</script>
<template>
    <div>
        <MyHeader :title="'Recensioni'" />
        <Review :response="data.response"></Review>
        

        <div class="bg-white py-24 sm:py-32">
            <div class="mx-auto max-w-7xl px-6 lg:px-8">
                <div class="mx-auto max-w-2xl lg:mx-0">
                    <h2
                        class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl"
                    >
                        Cosa ne pensano gli utenti
                    </h2>
                    <p class="mt-2 text-lg leading-8 text-gray-600">
                        Leggiamo le recensioni ecc ecc.
                    </p>
                </div>
                <div
                    class="mx-auto mt-10 grid max-w-2xl grid-cols-1 gap-x-8 gap-y-16 border-t border-gray-200 pt-10 sm:mt-16 sm:pt-16 lg:mx-0 lg:max-w-none lg:grid-cols-3"
                >
                    <p
                        v-if="!data.response.user_reviews.length"
                        class="mt-2 text-lg leading-8 text-gray-600"
                    >
                        <br />
                        Non ci sono ancora recensioni.
                    </p>
                    <UserReviews  v-else :reviews="data.response.user_reviews"></UserReviews>
                    

                    <!-- More posts... -->
                </div>
                <div
                    class="mx-auto flex max-w-2xl lg:mx-0 border-t border-gray-200 pt-10 sm:mt-16 sm:pt-16 lg:mx-0 lg:max-w-none gap-4"
                >
                    <h2
                        class="text-2xl font-bold tracking-tight text-gray-900 sm:text-3xl"
                    >
                        Vuoi lasciare una recensione?
                    </h2>
                    <NuxtLink
                        :to="'/addreview/' + data.response.product_name"
                        class="inline-block rounded-md border border-transparent bg-red-800 px-4 py-2 text-center font-medium text-white hover:bg-red-900"
                        >Clicca qui</NuxtLink
                    >
                    <AddUserReviewForm></AddUserReviewForm>
                </div>
            </div>
        </div>
    </div>
</template>
