<script setup>
const links = ["/"];
</script>
<template>
    <div>
        <v-app>
            <v-toolbar color="blue" density="comfortable">
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
                
            </v-toolbar>
            <v-main><NuxtPage /></v-main>

            <v-footer class="bg-grey-lighten-1">
                <v-row justify="center" no-gutters>
                    <NuxtLink v-for="link in links" :key="link" :to="link"
                        ><v-btn
                            color="white"
                            variant="text"
                            class="mx-2"
                            rounded="xl"
                            >{{ link }}</v-btn
                        ></NuxtLink
                    >
                    <v-col class="text-center mt-4" cols="12">
                        {{ new Date().getFullYear() }} —
                        <strong>Idraulica</strong>
                    </v-col>
                </v-row>
            </v-footer>
        </v-app>
    </div>
</template>
