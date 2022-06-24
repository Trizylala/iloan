<script setup>
import AppLayout from "@/Layouts/AppLayout.vue";
import { ref, onMounted } from "vue";
import { ethers } from "ethers";

import Tab from "../components/Tabs.vue";
import TabWrapper from "../components/TabsWrappers.vue";

const modal = ref(false);

const wallets = ref([
    {
        heading: "Browser wallet",
        iconUrl: "browserWallet.svg",
        meta() {
            console.log("Meta");
        },
    },
    {
        heading: "WalletConnect",
        iconUrl: "walletConnect.svg",
    },
    {
        heading: "Coinbase",
        iconUrl: "coinbase.svg",
    },
    {
        heading: "Torus",
        iconUrl: "torus.svg",
    },
    {
        heading: "Frame",
        iconUrl: "frame.svg",
    },
]);

// Web Browsers - MetaMask

const meta = ref(null);
const activeAcc = ref(true);
const metaAccount = ref(null);
const metaAddr = ref("");
const openBorrow = ref(false);

onMounted(() => {
    if (typeof window.ethereum !== "undefined") {
        meta.value = true;
    }
});

const metaMask = async (n) => {
    if (meta.value == true) {
        switch (n) {
            case 0:
                const provider = new ethers.providers.Web3Provider(
                    window.ethereum
                );

                const accounts = await provider.send("eth_requestAccounts", []);
                metaAddr.value = accounts[0];
                const balance = await provider.getBalance(metaAddr.value);
                console.log(
                    `MetaMask Account is  ${accounts} and balance is ${balance}`
                );

                modal.value = false;
                activeAcc.value = false;
                break;
            case 1:
                console.log("Second");
                break;
            case 2:
                console.log("Third");
                break;
            case 3:
                console.log("Fourth");
                break;
            case 4:
                console.log("Fifth");
                break;
        }
    } else {
        console.log("Install Metamask");
    }
};

const supplyCoins = ref([
    {
        id: 1,
        coinIcon: "busd.svg",
        coinName: "Binance USD",
        coinId: "BUSD",
        supplyBal: 0,
        supplyApy: 1.1,
        collateral: false,
    },
    {
        id: 2,
        coinIcon: "eth.svg",
        coinName: "Ethereum",
        coinId: "ETH",
        supplyBal: 0,
        supplyApy: 0.57,
        collateral: false,
    },
    {
        id: 3,
        coinIcon: "dai.svg",
        coinName: "DAI",
        coinId: "DAI",
        supplyBal: 0,
        supplyApy: 1.28,
        collateral: true,
    },
    {
        id: 4,
        coinIcon: "usdt.svg",
        coinName: "Tether",
        coinId: "USDT",
        supplyBal: 0,
        supplyApy: 1.27,
        collateral: false,
    },
]);
</script>

<template>
    <AppLayout title="Dashboard">
        <!-- <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Dashboard
            </h2>
        </template> -->

        <Teleport to="body">
            <div
                v-if="modal"
                class="fixed inset-0 z-50 w-full h-screen bg-black/90 flex items-center justify-center"
            >
                <div class="bg-white rounded-md px-4 py-2.5 w-[80%] h-fit">
                    <div class="flex flex-col gap-3">
                        <!-- Heading -->
                        <div class="flex justify-between items-center">
                            <h1 class="font-semibold text-xl pt-2.5">
                                Connect a wallet
                            </h1>
                            <span
                                class="font-bold text-lg cursor-pointer"
                                @click="modal = false"
                                >X</span
                            >
                        </div>
                        <!-- wallet list -->
                        <div class="flex flex-col gap-3">
                            <button
                                @click="metaMask(n)"
                                v-for="(wallet, n) in wallets"
                                :key="n"
                                class="bg-slate-300 flex justify-between items-center p-3 rounded cursor-pointer"
                            >
                                <span class="font-semibold text-lg">{{
                                    wallet.heading
                                }}</span>
                                <img
                                    class="last:h-6 last:w-6"
                                    :src="`icons/${wallet.iconUrl}`"
                                    alt="image"
                                />
                            </button>
                        </div>

                        <!--Foot  -->
                        <div class="flex flex-col gap-3 pb-5 pt-3">
                            <h1 class="text-sm">
                                Need help connecting a wallet?
                                <a
                                    class="underline underline-offset-2 hover:no-underline decoration-green-800 text-slate-600"
                                    href="http://"
                                    target="_blank"
                                    rel="noopener noreferrer"
                                    >Read our FAQ</a
                                >
                            </h1>
                            <span class="text-xs"
                                >Wallets are provided by External Providers and
                                by selecting you agree to Terms of those
                                Providers. Your access to the wallet might be
                                reliant on the External Provider being
                                operational.</span
                            >
                        </div>
                    </div>
                </div>
            </div>
        </Teleport>

        <div class="">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white shadow-xl sm:rounded-lg relative">
                    <!-- overflow-hidden -->
                    <section class="relative z-40">
                        <div class="bg-slate-700 pb-[77px] pt-8 z-30 relative">
                            <div class="flex flex-col gap-3 px-4 py-2.5">
                                <h1 class="text-gray-400 font-bold text-lg md:text-xl">
                                    Dashboard
                                </h1>

                                <!--  -->
                                <div class="flex items-center gap-2">
                                    <img
                                        class="object-contain w-7 h-7"
                                        src="icons/ethereum-logo.png"
                                        alt="eth-logo"
                                    />
                                    <span class="text-xl md:text-2xl text-white"
                                        >Ethereum</span
                                    >
                                    <svg
                                        class="w-6 h-6 text-white"
                                        fill="none"
                                        stroke="currentColor"
                                        viewBox="0 0 24 24"
                                        xmlns="http://www.w3.org/2000/svg"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            stroke-width="2"
                                            d="M19 9l-7 7-7-7"
                                        ></path>
                                    </svg>
                                </div>
                                <!-- end -->

                                <!--  -->
                                <div class="flex gap-[88px] text-white mt-6">
                                    <div class="flex flex-col">
                                        <span
                                            class="text-xs font-medium text-slate-400"
                                        >
                                            Net Worth
                                        </span>
                                        <p
                                            class="font-semibold text-slate-400 text-lg"
                                        >
                                            $ <span class="text-white">0</span>
                                        </p>
                                    </div>
                                    <div class="flex flex-col">
                                        <span
                                            class="text-xs font-medium text-slate-400"
                                        >
                                            Net APY⨀
                                        </span>
                                        <p
                                            class="font-semibold text-white text-lg"
                                        >
                                            0
                                            <span class="text-slate-400"
                                                >%</span
                                            >
                                        </p>
                                    </div>
                                </div>
                                <!-- end -->
                                <div
                                    class="w-[93%] h-[45px] rounded-md shadow-md px-4 py-1.5 bg-slate-500 border-2 border-white absolute top-[264px] left-4"
                                >
                                    <div class="flex text-white justify-between items-center">
                                        <div class="font-bold bg-sky-700 px-4 w-[40%] text-center
                                        text-sm py-1 rounded-md ">
                                            Supply
                                        </div>

                                        <div class="font-bold bg-sky-500 px-4 w-[40%] text-center
                                        text-sm py-1 rounded-md ">
                                            Borrow
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>
                    <!--  -->
                    <section class="">
                        <div class="bg-white z-50 flex-col flex gap-4">
                            <div
                                v-if="activeAcc"
                                class="flex flex-col items-center justify-center px-4 pt-2.5 pb-10"
                            >
                                <!-- image -->
                                <div class="mt-10">
                                    <img src="icons/img.svg" alt="img" />
                                </div>

                                <div class="text-center mt-[40px]">
                                    <h1 class="font-bold text-xl">
                                        Please, connect your wallet
                                    </h1>
                                    <p
                                        class="text-sm text-gray-600 max-w-[400px] pt-[10px] pb-7"
                                    >
                                        Please connect your wallet to see your
                                        supplies, loans, and open positions
                                    </p>
                                    <button
                                        @click="modal = true"
                                        class="bg-gradient-to-r from-cyan-500 to-blue-500 px-5 py-2 rounded-md 
                                        text-sm md:text-base text-white"
                                    >
                                        Connect wallet
                                    </button>
                                </div>
                            </div>
                            <!--  -->
                        </div>
                    </section>

                    <section class="flex flex-col gap-2 px-4 mt-4">
                        <div
                            class="mt-10 px-6 py-3 gap-2 flex flex-col justify-between mb-3 bg-slate-200 rounded-md shadow-md"
                        >
                            <div class="my-2">
                                <h1 class="text-lg md:text-xl font-semibold">
                                    Your supplies
                                </h1>
                            </div>
                            <div>
                                <p class="text-sm text-slate-800">
                                    Nothing supplied yet
                                </p>
                            </div>
                        </div>

                        <div
                            class="mt-1 px-6 py-3 gap-2 flex flex-col justify-between mb-7 bg-slate-200 rounded-md shadow-md"
                        >
                            <div class="my-2 flex justify-between items-center">
                                <h1 class="text-lg md:text-xl font-semibold">
                                    Assets to supply
                                </h1>
                                <span class="text-sm lg:text-base">-Hide</span>
                            </div>
                            <div
                                class="bg-sky-500/40 px-5 py-3 flex gap-2 justify-between rounded-md"
                            >
                                <span
                                    class="text-xs sm:text-sm max-w-[333px] text-slate-600"
                                    >Your Ethereum wallet is empty. Purchase or
                                    transfer assets</span
                                >
                            </div>
                        </div>

                        <div
                            class="bg-slate-200 rounded-md px-4 py-3 flex flex-col gap-6 justify-between"
                        >
                            <div
                                v-for="(supplyCoin, n) in supplyCoins"
                                :key="n"
                                class="flex flex-col gap-5 border-b-2 border-slate-500 pb-3"
                            >
                                <div class="flex gap-3 items-center mt-4">
                                    <img
                                        class="w-10 h-10"
                                        :src="`icons/${supplyCoin.coinIcon}`"
                                        :alt="`${supplyCoin.coinId}`"
                                    />
                                    <div>
                                        <h1 class="text-lg font-semibold">
                                            {{ supplyCoin.coinName }}
                                        </h1>
                                        <span class="text-sm text-slate-500">{{
                                            supplyCoin.coinId
                                        }}</span>
                                    </div>
                                </div>
                                <div class="flex flex-col gap-2">
                                    <div class="mt-4 flex flex-col">
                                        <ul class="flex justify-between">
                                            <li class="text-sm md:text-base">Supply balance</li>
                                            <li class="text-sm md:text-base">{{ supplyCoin.supplyBal }}</li>
                                        </ul>
                                        <ul class="flex justify-between">
                                            <li class="text-sm md:text-base">Supply APY</li>
                                            <li class="text-sm md:text-base">{{ supplyCoin.supplyApy }}%</li>
                                        </ul>
                                        <ul class="flex justify-between">
                                            <li class="text-sm md:text-base">Can be collateral</li>
                                            <li class="text-sm md:text-base" v-if="supplyCoin.collateral">
                                                Yes
                                            </li>
                                            <li class="text-sm md:text-base" v-else>-</li>
                                        </ul>
                                    </div>

                                    <div class="flex gap-3 justify-around items-center">
                                        <button
                                            class="bg-slate-100 text-xs sm:text-sm text-center font-semibold px-7 py-2 rounded-md w-fit text-slate-300"
                                        >
                                            Supply
                                        </button>
                                        <button
                                            @click="openBorrow = true"
                                            class="bg-slate-100 text-xs font-semibold text-slate-700 px-7 py-2 rounded-md sm:text-sm  w-fit"
                                        >
                                            Borrow
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </section>
                </div>
            </div>
        </div>
    </AppLayout>
</template>
