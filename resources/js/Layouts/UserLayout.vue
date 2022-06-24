<script setup>
import { ref, provide } from "vue";
import { Inertia } from "@inertiajs/inertia";
import { Head, Link } from "@inertiajs/inertia-vue3";

defineProps({
    title: String,
});

const showingNavigationDropdown = ref(false);

const switchToTeam = (team) => {
    Inertia.put(
        route("current-team.update"),
        {
            team_id: team.id,
        },
        {
            preserveState: false,
        }
    );
};

const logout = () => {
    Inertia.post(route("logout"));
};

const hModal = ref(false);
const lModal = ref(false);
</script>

<template>
    <div>
        <Head :title="title" />

        <!-- <JetBanner /> -->

        <div class="min-h-screen bg-gray-100">
            <header class="fixed inset-0 bg-white shadow-xl h-[56px] z-50">
                <nav
                    class="max-w-[1366px] mx-auto px-4 py-3 flex gap-3 items-center justify-between"
                >
                    <div>
                       <h1 class="font-black text-2xl">Nimrod</h1>
                    </div>

                    <div class="flex gap-3 justify-between items-center">
                        <button
                            @click="lModal = true"
                            class="px-4 py-2 rounded-lg bg-slate-300 text-black text-sm text-center shadow-sm"
                        >
                            Launch App
                        </button>

                        <button @click="hModal = true" class="flex md:hidden">
                            <svg
                                class="w-6 h-6 text-gray-700"
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
            <!-- Launch App Modal -->

             <Teleport to="body">
        <div
            v-if="lModal"
            class="fixed inset-0 bg-slate-800/20 w-full h-full z-50 flex justify-center items-center"
        >
            <div
                class="w-[88%] md:w-[30%] bg-slate-100 h-fit rounded-md shadow-md flex flex-col px-4 py-2.5"
            >
                <div class="flex justify-between mt-4 items-center">
                    <h1 class="font-semibold text-2xl">Redirect notice</h1>
                    <span
                        @click="lModal = false"
                        class="font-black text-2xl cursor-pointer"
                        >X</span
                    >
                </div>

                <div class="flex gap-3 justify-center mt-5">
                  <div class="flex gap-5">
                    <h1 class="font-bold text-lg">NIMROD</h1>
                    <h1 class="font-bold text-lg">IPFS</h1>
                  </div>
                  <div>

                  </div>
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
                        maintained instance of the open source Nimord front end,
                        hosted and served on the distributed, peer-to-peer file
                        network known as the Interplanetary File System (IPFS).
                    </h1>
                    <Link
                    :href="route('login')"
                    class="text-white font-semibold bg-slate-800 rounded-md px-4 py-3 mb-6 text-center"
                >
                     Agree
                </Link>
                </div>
            </div>
        </div>
    </Teleport>


            <!-- Page Content -->
            <main>
                <slot />
            </main>
        </div>
    </div>
</template>
