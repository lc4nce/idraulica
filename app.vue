<script setup>
const route = useRoute();
const titles = {
    index: "Homepage",
    reviews: "Recensioni",
    about: "Chi siamo",
};

const highlightIndex = computed(() => {
    switch (route.name) {
        case "index":
            return 1;
        
        case "cat-product_type-product_name":
        case "reviews":
        case "addreview-product_name":
            return 2;
        
        case "about":
            return 3;
        
        case "installers":
        case "collaborate":
            return 4;
    }
});
</script>
<template>
    <div>
        <v-app>
            <!-- <v-toolbar color="blue" density="comfortable">
                <v-toolbar-title>Title</v-toolbar-title>
                <NuxtLink v-for="link in links" :key="link" :to="link"
                        ><v-btn
                            color="white"
                            variant="text"
                            class="mx-2"
                            rounded="xl"
                            >{{ link }}</v-btn
                        ></NuxtLink
                    >
                <v-spacer></v-spacer>
                <v-btn icon>
                    <v-icon>mdi-magnify</v-icon>
                </v-btn>
                
            </v-toolbar> -->
            <MyNavbar :index="highlightIndex"></MyNavbar>

            <NuxtPage />

            <v-footer class="bg-black">
                <v-row justify="center" no-gutters>
                    <!-- <NuxtLink v-for="link in links" :key="link" :to="link"
                        ><v-btn
                            color="white"
                            variant="text"
                            class="mx-2"
                            rounded="xl"
                            >{{ link }}</v-btn
                        ></NuxtLink
                    > -->
                    <v-col class="text-center mt-4" cols="12">
                        {{ new Date().getFullYear() }} —
                        <strong>Idraulica</strong>
                    </v-col>
                </v-row>
            </v-footer>
        </v-app>
    </div>
</template>
