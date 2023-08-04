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
        <div
            class="relative flex w-full items-center overflow-hidden bg-white px-4 pb-8 pt-7 shadow-2xl sm:px-6 sm:pt-8 md:p-6 lg:p-8"
        >
            <div
                class="grid w-full grid-cols-1 items-start gap-x-6 gap-y-8 sm:grid-cols-12 lg:gap-x-8"
            >
                <div
                    class="aspect-h-3 aspect-w-2 overflow-hidden rounded-lg bg-gray-100 sm:col-span-4 lg:col-span-5"
                >
                    <img
                        src="https://tailwindui.com/img/ecommerce-images/product-quick-preview-02-detail.jpg"
                        alt="Two each of gray, white, and black shirts arranged on table."
                        class="object-cover object-center"
                    />
                </div>
                <div class="sm:col-span-8 lg:col-span-7">
                    <h2 class="text-2xl font-bold text-gray-900 sm:pr-12">
                        {{ data.response.product_name }}
                    </h2>

                    <section aria-labelledby="information-heading" class="mt-2">
                        <h3 id="information-heading" class="sr-only">
                            Product information
                        </h3>

                        <p class="text-2xl text-gray-900">
                            {{ data.response.product_type }}
                        </p>

                        <!-- Reviews -->
                        <div class="mt-6">
                            <h4 class="sr-only">Reviews</h4>
                            <div class="flex items-center">
                                <div class="flex items-center">
                                    <!-- Active: "text-gray-900", Default: "text-gray-200" -->
                                    {{ data.response.rating }}/10
                                </div>
                            </div>
                        </div>
                    </section>

                    <section aria-labelledby="options-heading" class="mt-10">
                        {{ data.response.body }}
                    </section>
                </div>
            </div>
        </div>

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
                    <article
                        v-for="review in data.response.user_reviews"
                        class="flex max-w-xl flex-col items-start justify-between"
                    >
                        <div class="flex items-center gap-x-4 text-xs">
                            <time datetime="2020-03-16" class="text-gray-500">{{
                                review.date
                            }}</time>
                            <!-- <a href="#" class="relative z-10 rounded-full bg-gray-50 px-3 py-1.5 font-medium text-gray-600 hover:bg-gray-100">Marketing</a> -->
                        </div>
                        <div class="group relative">
                            <h3
                                class="mt-3 text-lg font-semibold leading-6 text-gray-900 group-hover:text-gray-600"
                            >
                                <a href="#">
                                    <span class="absolute inset-0"></span>
                                    {{ review.rating + "/10 " + review.title }}
                                </a>
                            </h3>
                            <p
                                class="mt-5 line-clamp-3 text-sm leading-6 text-gray-600"
                            >
                                {{ review.body }}
                            </p>
                        </div>
                        <div class="relative flex items-center gap-x-4">
                            <div class="text-sm leading-6">
                                <p class="font-semibold text-gray-900">
                                    <a href="#">
                                        <span class="absolute inset-0"></span>
                                        {{
                                            review.firstname +
                                            " " +
                                            review.lastname
                                        }}
                                    </a>
                                </p>
                            </div>
                        </div>
                    </article>

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
                </div>
            </div>
        </div>
    </div>
</template>
