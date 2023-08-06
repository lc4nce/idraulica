<script setup>
    const props = defineProps(["response"]);
</script>
<template>
    <div v-if="props.response"
        class="relative flex w-full items-center overflow-hidden bg-white px-4 pb-8 pt-7 shadow-2xl sm:px-6 sm:pt-8 md:p-6 lg:p-8">
        <div class="grid w-full grid-cols-1 items-start gap-x-6 gap-y-8 sm:grid-cols-12 lg:gap-x-8">
            <div class="aspect-h-3 aspect-w-2 overflow-hidden rounded-lg bg-gray-100 sm:col-span-4 lg:col-span-5">
                <img src="https://www.aircondirect.co.uk/Images/SF12000_1_Supersize.jpg?width=650&height=650&v=46"
                    alt="Two each of gray, white, and black shirts arranged on table." class="object-cover object-center" />
            </div>
            <div class="sm:col-span-8 lg:col-span-7">
                <h2 class="text-2xl font-bold text-gray-900 sm:pr-12">
                    {{ props.response.product_name }}
                </h2>

                <section aria-labelledby="information-heading" class="mt-2">
                    <h3 id="information-heading" class="sr-only">
                        Product information
                    </h3>

                    <p class="text-2xl text-gray-900">
                        {{ props.response.product_type }}
                    </p>

                    <!-- Reviews -->
                    <div class="mt-6">
                        <h4 class="sr-only">Reviews</h4>
                        <div class="flex items-center">
                            <div class="flex items-center">
                                <!-- Active: "text-gray-900", Default: "text-gray-200" -->
                                
                                <v-rating v-model="props.response.rating" readonly></v-rating>
                            </div>
                        </div>
                    </div>
                </section>

                <section aria-labelledby="options-heading" class="mt-10">
                    {{ props.response.body }}
                </section>
            </div>
        </div>
    </div>
</template>