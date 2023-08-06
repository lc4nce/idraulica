<script setup>
const props = defineProps(["reviews"]);
</script>
<template>
  <div
    v-for="review in props.reviews"
    class="flex max-w-xl flex-col items-start justify-between"
  >
    <article>
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
          <span class="absolute inset-0"></span>
          <div class="text-center">
            <v-rating v-model="review.rating" readonly></v-rating>
          </div>
          {{ review.title }}
        </h3>
        <p class="mt-5 line-clamp-3 text-sm leading-6 text-gray-600">
          {{ review.body }}
        </p>
      </div>
      <div class="relative flex items-center gap-x-4">
        <div class="text-sm leading-6">
          <p class="font-semibold text-gray-900">
              <span class="absolute inset-0"></span>
              {{ review.firstname + " " + review.lastname }}
          </p>
        </div>
      </div>
    </article>
  </div>
</template>
