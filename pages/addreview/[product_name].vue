<script setup>
const route = useRoute();
const { data } = await useFetch(
    "http://127.0.0.1:3001/api/review/show?product_name=" +
        route.params.product_name
);

const user_review = ref({
    firstname: "",
    lastname: "",
    email: "",
    confirmed: true,
    title: "",
    body: "",
    rating: 3,
    date: Date.now()
})

async function formRequest() {
    return await useFetch("http://127.0.0.1:3001/api/review/add-user-review", {
        method: "POST",
        body: {
            "reviewId": data.value.response._id,
            "user_review": user_review.value
        }
    });
}
</script>
<template>
    <div>
        <div class="isolate bg-white px-6 py-24 sm:py-32 lg:px-8">
            <div
                class="absolute inset-x-0 top-[-10rem] -z-10 transform-gpu overflow-hidden blur-3xl sm:top-[-20rem]"
                aria-hidden="true"
            ></div>
            <div class="mx-auto max-w-2xl text-center">
                <h2
                    class="text-3xl font-bold tracking-tight text-gray-900 sm:text-4xl"
                >
                    Aggiungi una recensione
                </h2>
                <p class="mt-2 text-lg leading-8 text-gray-600">
                    Inserisci alcuni dati e cosa pensi del prodotto "{{
                        data.response.product_name
                    }}".
                </p>
            </div>
            <form
                action="#"
                method="POST"
                class="mx-auto mt-16 max-w-xl sm:mt-20"
                @submit.prevent="formRequest"
            >
                <div class="grid grid-cols-1 gap-x-8 gap-y-6 sm:grid-cols-2">
                    <div>
                        <label
                            for="first-name"
                            class="block text-sm font-semibold leading-6 text-gray-900"
                            >Nome</label
                        >
                        <div class="mt-2.5">
                            <input
                                v-model="user_review.firstname"
                                type="text"
                                name="first-name"
                                id="first-name"
                                autocomplete="given-name"
                                class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            />
                        </div>
                    </div>
                    <div>
                        <label
                            for="last-name"
                            class="block text-sm font-semibold leading-6 text-gray-900"
                            >Cognome</label
                        >
                        <div class="mt-2.5">
                            <input
                                v-model="user_review.lastname"
                                type="text"
                                name="last-name"
                                id="last-name"
                                autocomplete="family-name"
                                class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            />
                        </div>
                    </div>
                    <div class="sm:col-span-2">
                        <label
                            for="email"
                            class="block text-sm font-semibold leading-6 text-gray-900"
                            >Email</label
                        >
                        <div class="mt-2.5">
                            <input
                                v-model="user_review.email"
                                type="email"
                                name="email"
                                id="email"
                                autocomplete="email"
                                class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            />
                        </div>
                    </div>
                    <div class="sm:col-span-2">
                        <label
                            for="title"
                            class="block text-sm font-semibold leading-6 text-gray-900"
                            >Titolo recensione</label
                        >
                        <div class="mt-2.5">
                            <input
                                v-model="user_review.title"
                                type="text"
                                name="title"
                                id="title"
                                class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            />
                        </div>
                    </div>

                    <div class="sm:col-span-2">
                        <label
                            for="body"
                            class="block text-sm font-semibold leading-6 text-gray-900"
                            >Cosa ne pensi?</label
                        >
                        <div class="mt-2.5">
                            <textarea
                                v-model="user_review.body"
                                name="body"
                                id="body"
                                rows="4"
                                class="block w-full rounded-md border-0 px-3.5 py-2 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                            ></textarea>
                        </div>
                    </div>
                    <div class="flex gap-x-4 sm:col-span-2">
                        <div class="flex h-6 items-center">
                            <!-- Enabled: "bg-indigo-600", Not Enabled: "bg-gray-200" -->
                            <button
                                type="button"
                                class="bg-gray-200 flex w-8 flex-none cursor-pointer rounded-full p-px ring-1 ring-inset ring-gray-900/5 transition-colors duration-200 ease-in-out focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                                role="switch"
                                aria-checked="false"
                                aria-labelledby="switch-1-label"
                            >
                                <span class="sr-only">Agree to policies</span>
                                <!-- Enabled: "translate-x-3.5", Not Enabled: "translate-x-0" -->
                                <span
                                    aria-hidden="true"
                                    class="translate-x-0 h-4 w-4 transform rounded-full bg-white shadow-sm ring-1 ring-gray-900/5 transition duration-200 ease-in-out"
                                ></span>
                            </button>
                        </div>
                        <label
                            class="text-sm leading-6 text-gray-600"
                            id="switch-1-label"
                        >
                            By selecting this, you agree to our
                            <a href="#" class="font-semibold text-indigo-600"
                                >privacy&nbsp;policy</a
                            >.
                        </label>
                    </div>
                </div>
                <div class="mt-10">
                    <button
                        type="submit"
                        class="block w-full rounded-md bg-indigo-600 px-3.5 py-2.5 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
                    >
                        Let's talk
                    </button>
                </div>
            </form>
        </div>
    </div>
</template>
