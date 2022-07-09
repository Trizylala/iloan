<script setup>
import { Head, Link } from "@inertiajs/inertia-vue3";
import { ref } from "vue";
import anime from "animejs/lib/anime.es.js";
// import Swiper core and required modules
import { Virtual } from "swiper";
import Tab from "../components/Tabs.vue";
import TabsWrapper from "../components/TabsWrapper.vue";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "swiper/css/scrollbar";

const slides = Array.from({ length: 1000 }).map(
    (el, index) => `Slide ${index + 1}`
);

const onSwiper = (swiper) => {
    console.log(swiper);
};
const onSlideChange = () => {
    console.log("slide change");
};

defineProps({
    canLogin: Boolean,
    canRegister: Boolean,
    laravelVersion: String,
    phpVersion: String,
});

anime({
    targets: ".el",
    translateX: 250,
});

// New Data
const openModal = ref(false);
const hModal = ref(false);
</script>

<template>
    <Head title="Home" />

    <!-- <div class="relative flex dark:bg-gray-900 sm:pt-0">
        <div
            v-if="canLogin"
            class="hidden fixed top-0 right-0 px-6 py-4 sm:block z-50"
        >
            <Link
                v-if="$page.props.user"
                :href="route('dashboard')"
                class="text-sm text-gray-700 underline"
            >
                Dashboard
            </Link>

            <template v-else>
                <Link
                    :href="route('login')"
                    class="text-sm text-gray-700 underline"
                >
                    Log in
                </Link>

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ml-4 text-sm text-gray-700 underline"
                >
                    Register
                </Link>
            </template>
        </div>
    </div> -->

    <header class="fixed inset-0 bg-white h-[56px] z-50">
        <nav
            class="max-w-[1666px] mx-auto px-4 py-3 flex gap-3 items-center justify-between"
        >
            <div>
                <span class="text-2xl font-bold text-gray-800">NIMROD</span>
            </div>

            <div class="flex gap-3 justify-between items-center">
                <button
                    @click="openModal = true"
                    class="px-4 py-2 rounded-lg bg-slate-300 text-black shadow-sm"
                >
                    Launch App
                </button>
                <button @click="hModal = true" class="flex md:hidden">
                    <svg
                        class="w-7 h-7 text-gray-700"
                        fill="none"
                        stroke="currentColor"
                        viewBox="0 0 24 24"
                        xmlns="http://www.w3.org/2000/svg"
                    >
                        <path
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="M4 6h16M4 12h16M4 18h7"
                        ></path>
                    </svg>
                </button>
            </div>
        </nav>
    </header>
    <!--  -->
    <!--  -->
    <Teleport to="body">
        <div
            v-if="openModal"
            class="fixed inset-0 bg-slate-800/20 w-full h-full z-50 flex justify-center items-center"
        >
            <div
                class="w-[88%] bg-slate-100 h-fit rounded-md shadow-md flex flex-col px-4 py-2.5"
            >
                <div class="flex justify-between mt-4 items-center">
                    <h1 class="font-semibold text-2xl">Redirect notice</h1>
                    <span
                        @click="openModal = false"
                        class="font-black text-2xl cursor-pointer"
                        >X</span
                    >
                </div>

                <div class="flex gap-3 justify-center mt-5">
                    <img
                        class="object-contain w-[59%]"
                        src="images/aaveIPFS.svg"
                        alt="images-middle"
                    />
                </div>

                <div class="flex flex-col gap-6 mt-7">
                    <h1 class="pb-5 pt-3">
                        By accessing this link you are leaving,
                        <a class="font-bold" href="">nimrod.com</a>
                        and are being redirected to a third party, independent
                        website.
                    </h1>

                    <h1 class="pb-5">
                        This redirect takes you to a community deployed and
                        maintained instance of the open source Nimrod front end,
                        hosted and served on the distributed, peer-to-peer file
                        network known as the Interplanetary File System (IPFS).
                    </h1>

                    <button
                        class="text-white font-semibold bg-slate-800 rounded-md px-4 py-3 mb-6"
                    >
                        Agree
                    </button>
                </div>
            </div>
        </div>
    </Teleport>
    <Teleport to="body">

        <div v-if="hModal" class="min-h-screen w-full absolute inset-0 bg-transparent z-50 overflow-hidden">

        <div class="flex px-4 py-2.5 bg-slate-600 h-full w-[69%]">
            <div>

            </div>

        </div>

        </div>

    </Teleport>


</template>
