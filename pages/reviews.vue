<script setup>
const { data } = await useFetch("http://127.0.0.1:3001/api/review/");
</script>
<template>
    <div>
        <MyHeader :title="'Recensioni'" />
        <div class="bg-white">
            <div
                class="mx-auto max-w-2xl px-4 py-16 sm:px-6 sm:py-24 lg:max-w-7xl lg:px-8"
            >
                <h2 class="sr-only">Products</h2>

                <div
                    class="grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 xl:gap-x-8"
                >
                    <NuxtLink
                        v-for="obj in data.response"
                        :to="'cat-' + obj.product_type + '/' + obj.product_name"
                        class="group"
                    >
                        <div
                            class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-lg bg-gray-200 xl:aspect-h-8 xl:aspect-w-7"
                        >
                            <img
                                src="https://www.aircondirect.co.uk/Images/SF12000_1_Supersize.jpg?width=650&height=650&v=46"
                                alt="Tall slender porcelain bottle with natural clay textured body and cork stopper."
                                class="h-full w-full object-cover object-center group-hover:opacity-75"
                            />
                        </div>
                        <h3 class="mt-4 text-sm text-gray-700">
                            {{ obj.product_name }}
                        </h3>
                        <p class="mt-1 text-lg font-medium text-gray-900">
                            {{ obj.rating }}/10
                        </p>
                    </NuxtLink>
                    <!-- More products... -->
                </div>
            </div>
        </div>
    </div>
</template>
