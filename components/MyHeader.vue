<script setup>
const props = defineProps(["title"]);
</script>
<template>
    <div>
        <header v-if="props.title" class="bg-white shadow">
            <div class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8">
                <h1 class="text-3xl font-bold tracking-tight text-gray-900">
                    {{ props.title }}
                </h1>
            </div>
        </header>
    </div>
</template>
