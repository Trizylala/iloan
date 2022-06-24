<script setup>
import UserLayout from "@/Layouts/UserLayout.vue";
import { ref, onMounted } from "vue";
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
import Nimrod from "../components/Nimrod.vue";
import { on } from "events";

const slides = Array.from({ length: 1000 }).map(
  (el, index) => `Slide ${index + 1}`
);

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

const screen = ref(null)
const perView = ref(null)

onMounted(()=>{
  screen.value = window.innerWidth
  if (screen.value <= 533) {
    perView.value = 1.5
    } else if (screen.value >=744) {
      perView.value = 2.3
    }
})


// New Data
const openModal = ref(false);
const hModal = ref(false);

const worksArray = ref([
  {
    heading: "Submit Nimord Request for comment(ARC)",
    text: "Discuss with community members and receive feedback.",
    url: "Visit Docs",
    urlLink: "",
  },
  {
    heading: "Create a snapshot",
    text: "Gauge community sentiment on a new proposal through a Snapshot.",
    url: "How to create snapshot",
    urlLink: "",
  },
  {
    heading: "Submit an Nimord Request for Improvement(AIP)",
    text: "The proposal is submittted through a GitHub pull request, and the community votes on approvals",
    url: "",
  },
]);

const footerArray1 = ref([
  {
    id: 1,
    text: "babillonToken",
    urlLink: "",
  },
  {
    id: 2,
    text: "Bug Bounty",
    urlLink: "",
  },
  {
    id: 3,
    text: "Flash Loans",
    urlLink: "",
  },
  {
    id: 4,
    text: "Rate Switching",
    urlLink: "",
  },
  {
    id: 5,
    text: "Technical Paper",
    urlLink: "",
  },
  {
    id: 6,
    text: "Nimordgate",
    urlLink: "",
  },
  {
    id: 7,
    text: "Careers",
    urlLink: "",
  },
]);

const footerArray2 = ref([
  {
    id: 1,
    text: "Branding",
    urlLink: "",
  },
  {
    id: 2,
    text: "Blog",
    urlLink: "",
  },
  {
    id: 3,
    text: "Contract",
    urlLink: "",
  },
  {
    id: 4,
    text: "Terms of Use",
    urlLink: "",
  },
  {
    id: 5,
    text: "Privacy Policy",
    urlLink: "",
  },
]);

const nimrodMart = ref([
  {
    id: 1,
    mart: "Ethereum",
    martIcon: "aave.svg",
    text: "Aave was first deployed on the Ethereum network in January 2020. Ethereum is the largest market on the Aave protocol by liquidity and has the most listed assets.",
    urlLink: "",
  },
  {
    id: 2,
    mart: "Polygon",
    martIcon: "polygon.svg",
    text: "Faster transactions and lower fees make interacting with Aave on Polygon perfect for high volume transactions. Earn rewards in polygon for supply liquidity and borrowing.",
    urlLink: "",
  },
  {
    id: 3,
    mart: "Avalanche",
    martIcon: "avalanche.svg",
    text: "Fast and cheaper transactions. Earn rewards in AVAX for borrowing or supplying liquidity.",
    urlLink: "",
  },
  {
    id: 4,
    mart: "Arbitrum",
    martIcon: "arbitrum.svg",
    text: "Ethereums security with speed. Arbitrum is a L2 rollup deployed on Aave for secure, fast transactions.",
    urlLink: "",
  },
  {
    id: 5,
    mart: "AMM",
    martIcon: "AMM.svg",
    text: "Reduced volatility from supplying multiple assets and earn trading fees from the market.",
    urlLink: "",
  },
  {
    id: 6,
    mart: "Fantom",
    martIcon: "fantom.svg",
    text: "Fantom is a fast, high-throughput open-source smart contract platform for digital assets and dApps.",
    urlLink: "",
  },
  {
    id: 7,
    mart: "Harmony",
    martIcon: "harmony.svg",
    text: "Harmony is your open platform for assets, collectibles, identity, governance. Harmony offers secure bridges for cross-chain asset transfers with Ethereum, Binance and 3 other chains.",
    urlLink: "",
  },
  {
    id: 8,
    mart: "Optimsim",
    martIcon: "optimism.svg",
    text: "Optimism is an EVM equivalent Optimistic Rollup chain. It's designed to be fast, simple, and secure.",
    urlLink: "",
  },
  {
    id: 9,
    mart: "Centrifuge RWA",
    martIcon: "rwa.svg",
    text: "Bridge real world assets like invoices, real estate, and royalties to DeFi.",
    urlLink: "",
  },
]);
</script>

<template>
  <UserLayout title="Home">
    <section>
      <div class="z-10">
        <div class="bg-sky-400">
          <div class="h-[390px] md:h-[526px] max-w-[1288px] mx-auto flex flex-col px-4 py-2.5 relative">
            <div class="absolute top-[29%] md:top-[33%]">
              <div>
               <Nimrod />
              </div>
              <div class="mt-7">
                <h1
                  class="
                    font-semibold
                    text-white text-lg
                    md:text-2xl
                    md:font-bold
                    uppercase
                    tracking-wider
                    max-w-[200px]
                    md:max-w-none
                  "
                >
                  Nimrod Liquidity Protocol
                </h1>
              </div>
              <div class="mt-2">
                <h1 class="font-black text-white text-xl pt-2 md:max-w-[500px] md:leading-loose lg:text-4xl max-w-[300px]">
                  Earn interest, borrow assets, and build applications
                </h1>
              </div>
            </div>
          </div>
        
          <div class="bg-slate-800 h-[400px] md:h-[200px] flex flex-col md:flex-row">

            <div class="max-w-[1288px] mx-auto px-4 py-2.5">

              <div class="mt-7">
                <h1 class="font-bold text-2xl md:font-medium md:text-4xl lg:text-5xl text-white">
                  $ 14,666,369,777.27
                </h1>
              </div>

              <div class="mt-3 ">
                <h2 class="text-slate-400">
                  of liquidity is locked in Nimord across 7 networks and over 13
                  markets.
                </h2>
              </div>
            </div>

            <div class="max-w-[1288px] mx-auto mt-3 px-4 py-2.5">
              <TabsWrapper>
                <Tab title="Supply">
                  <div>
                    <h1 class="text-white max-w-[500px]  lg:text-lg">
                      Supply into the protocol and watch your assets grow as a
                      liquidity provider
                    </h1>
                  </div>
                </Tab>
                <Tab title="Stake">
                  <div>
                    <h1 class="text-white max-w-[500px]  lg:text-lg">
                      Deposit your NIMROD into the protocol and earn rewards for
                      securing the protocol
                    </h1>
                  </div>
                </Tab>
                <Tab title="Loan">
                  <div>
                    <h1 class="text-white max-w-[500px]  lg:text-lg">
                      Borrow against your collateral from across multiple
                      networks and assets
                    </h1>
                  </div>
                </Tab>
                <Tab title="Vote">
                  <div>
                    <h1 class="text-white max-w-[500px]  lg:text-lg">
                      Participate in Nimord governance and vote on new
                      proposals, new assets, and protocol upgrades
                    </h1>
                  </div>
                </Tab>
              </TabsWrapper>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="bg-slate-800">
      <div class="max-w-[1288px] mx-auto px-4 py-2.5">
        <div class="flex flex-col">
          <div class="mt-8 mb-1.5">
            <h1 class="font-bold text-3xl first-letter:text-4xl text-white">
              Nimrod Markets
            </h1>
          </div>
        </div>
      </div>

      <div class="px-4 py-2.5 mt-7">
        <!-- Swiper screen < 731 -->
        <swiper
          :modules="[Virtual]"
          :slides-per-view="perView"
          :space-between="30"
          virtual
          class="block"
        >
          <swiper-slide
            v-for="(nimMart, n) in nimrodMart"
            :key="n"
            :virtualIndex="index"
          >
            <div
              class="
                w-[98%]
                h-[330px]
                bg-sky-800
                shadow-xl
                max-w-[1288px]
                mx-auto
                rounded-md
                relative
                p-3
                text-white
              "
            >
              <div class="absolute inset-0 px-3 pt-4">
                <div class="flex justify-between items-center">
                  <div>
                    <img
                      :src="`icons/${nimMart.martIcon}`"
                      :alt="`${nimMart.mart}`"
                      class="w-[46px] h-[46px]"
                    />
                  </div>

                  <div class="flex gap-3 items-center justify-between">
                    <span class="text-sm">Go to Market</span>
                    <svg
                      class="w-4 h-4"
                      fill="none"
                      stroke="currentColor"
                      viewBox="0 0 24 24"
                      xmlns="http://www.w3.org/2000/svg"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M14 5l7 7m0 0l-7 7m7-7H3"
                      ></path>
                    </svg>
                  </div>
                </div>
              </div>

              <div class="absolute top-[25%]">
                <div class="flex gap-3 items-center">
                  <h1 class="font-bold text-lg">{{ nimMart.mart }}</h1>
                  <svg
                    width="20"
                    height="20"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg"
                  >
                    <path
                      d="M11 3a1 1 0 1 0 0 2h2.586l-6.293 6.293a1 1 0 1 0 1.414 1.414L15 6.414V9a1 1 0 1 0 2 0V4a1 1 0 0 0-1-1h-5Z"
                      fill="currentColor"
                    ></path>
                    <path
                      d="M5 5a2 2 0 0 0-2 2v8a2 2 0 0 0 2 2h8a2 2 0 0 0 2-2v-3a1 1 0 0 0-2 0v3H5V7h3a1 1 0 0 0 0-2H5Z"
                      fill="currentColor"
                    ></path>
                  </svg>
                </div>
              </div>

              <div class="absolute top-[40%]">
                <p>
                  <span class="font-medium text-slate-400">
                    {{ nimMart.text }}
                  </span>
                </p>
              </div>
            </div>
          </swiper-slide>
        </swiper>

        <!--  -->

        <!--  -->

    
          <div   v-for="(nimMart, n) in nimrodMart"
            :key="n"
            class="hidden">
            <h1>1</h1>
           
          </div>

        <div
          class="
            w-full
            bg-sky-800
            h-[270px]
            mt-[59px]
            rounded-md
            max-w-[1288px]
            mx-auto
            flex
            justify-center
            items-center
          "
        >
          <div class="p-4 flex flex-col gap-3 text-white">
            <h1 class="font-bold text-xl">And more to come...</h1>
            <h3 class="text-base text-slate-400 font-medium mb-4">
              Submit a proposal to deploy a new market in the Nimord ecosystem.
              You can learn from the Nimord governance.
            </h3>

            <button
              class="
                bg-slate-200
                font-semibold
                text-gray-800 text-sm
                px-4
                py-1
                rounded-md
                w-fit
              "
            >
              Learn More
            </button>
          </div>
        </div>
      </div>
    </section>
    <section class="bg-slate-800 relative">
      <div class="flex flex-col items-center justify-between px-4 py-2.5">
        <div class="mt-10 flex flex-col gap-3 items-center">
          <h1
            class="
              text-white
              font-bold
              text-3xl md:text-4xl lg:text-5xl text-center
              max-w-[300px]
              sm:max-w-[500px]
              mx-auto
              tracking-wide
              leading-[44px]
            "
          >
            Governed by the community
          </h1>
          <p
            class="
              text-base text-slate-400
              font-medium
              text-center
              pt-3
              max-w-[399px]
            "
          >
            MINROD is a fully decentralized, community governed protocol with
            111,232 token holders.
          </p>
          <button
            class="
              bg-slate-300
              px-4
              py-2.5
              rounded-md
              mb-5
              mt-4
              font-medium
              text-sm
              max-w-[200px]
            "
          >
            Governance Forum
          </button>
        </div>

        <div>
          <img
            class="w-[90%] h-[50%] object-contain bg-center"
            src="images/governanceGhosts.svg"
            alt=""
          />
        </div>
      </div>

      <!--  -->
      <div class="flex flex-col gap-3">
        <div class="mt-7 mb-4">
          <h1 class="text-white text-center text-2xl font-bold pb-5">
            How it Works
          </h1>
        </div>
        <!-- Mobile view -->
        <div
          class="relative flex flex-col md:hidden"
          v-for="(wa, n) in worksArray"
          :key="n"
        >
          <div class="mb-5">
            <div
              class="
                w-full
                h-[2px]
                bg-gradient-to-r
                from-teal-700
                to-slate-300
                mb-5
                relative
              "
            ></div>
            <div
              class="
                bg-sky-700
                rounded-full
                h-10
                w-10
                absolute
                -top-[18px]
                left-8
                flex
                items-center
                justify-center
                font-semibold
                text-xl text-white
              "
            >
              {{ n + 1 }}
            </div>
          </div>

          <div class="px-4 py-2.5 text-white">
            <h1 class="text-sm font-bold text-slate-200 pb-2">
              {{ wa.heading }}
            </h1>
            <p class="text-sm text-slate-400 font-medium pb-3">
              {{ wa.text }}
            </p>
            <div class="mb-5">
              <a class="text-sm no-underline font-semibold" href="">{{
                wa.url
              }}</a>
            </div>
          </div>
        </div>
        <!-- Tablet  -->

        <div class="hidden md:block">
          <div class="relative">
          <div class="w-full h-[2px] bg-gradient-to-r
                from-teal-700
                to-slate-300 relative">
            </div>
            <div class="font-bold text-white absolute -top-5 w-full">
              <ul class="flex justify-around">

                <li class="bg-sky-700 rounded-full h-10 flex items-center justify-center w-10 text-center">1</li>
                <li class="bg-sky-700 rounded-full h-10 flex items-center justify-center w-10 text-center">2</li>
                <li class="bg-sky-700 rounded-full h-10 flex items-center justify-center w-10 text-center">3</li>

              </ul>
            </div>
        </div>
        <div class="flex w-full justify-around mt-9">
          <div  v-for="(wa, n) in worksArray"
          :key="n"
          class="flex flex-col text-white">
            <h1 class="font-bold text-sm pb-3 max-w-[200px]">{{wa.heading}}</h1>
            <h2 class="text-sm pb-2 max-w-[200px]">{{wa.text}}</h2>
            <a href="http://" target="_blank" rel="noopener noreferrer">{{wa.url}}</a>
          </div>

        </div>
        </div>

      </div>
    </section>

    <section class="bg-slate-800">
      <div class="px-4 py-2.5 max-w-[1666px] mx-auto">
        <div class="flex flex-col gap-3 mb-7">
          <div class="mt-10">
            <ul class="flex gap-6 mb-7">
              <li
                class="
                  h-10
                  w-10
                  bg-slate-200
                  rounded-full
                  flex
                  items-center
                  justify-center
                "
              >
                <img class="w-[19px] h-[19px]" src="icons/twitter.svg" alt="icons" />
              </li>
              <li
                class="
                  h-10
                  w-10
                  bg-slate-200
                  rounded-full
                  flex
                  items-center
                  justify-center
                "
              >
                <img class="w-[19px] h-[19px]" src="icons/github.svg" alt="icons" />
              </li>
              <li
                class="
                  h-10
                  w-10
                  bg-slate-200
                  rounded-full
                  flex
                  items-center
                  justify-center
                "
              >
                <img class="w-[19px] h-[19px]" src="icons/discord.svg" alt="icons" />
              </li>
              <li
                class="
                  h-10
                  w-10
                  bg-slate-200
                  rounded-full
                  flex
                  items-center
                  justify-center
                "
              >
                <img class="w-[19px] h-[19px] bg-center" src="icons/telegram.svg" alt="icons" />
              </li>
            </ul>
          </div>
          <div class="flex gap-[100px]">
            <div class="flex flex-col gap-3 text-slate-400">
              <a
                class="font-semibold text-sm"
                v-for="(fAi, n) in footerArray1"
                :key="n"
                href=""
                >{{ fAi.text }}</a
              >
            </div>
            <div class="flex flex-col gap-3 text-slate-400">
              <a
                class="font-semibold text-sm"
                v-for="(fAii, n) in footerArray2"
                :key="n"
                href=""
                >{{ fAii.text }}</a
              >
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Fixed chat box -->
    <div
      class="
        h-[60px]
        w-[60px]
        rounded-full
        bg-sky-800
        fixed
        bottom-6
        right-7
        border-2 border-teal-900
        z-50
        flex
        items-center
        justify-center
      "
    >
      <svg
        class="w-10 h-10 text-white"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M8 10h.01M12 10h.01M16 10h.01M9 16H5a2 2 0 01-2-2V6a2 2 0 012-2h14a2 2 0 012 2v8a2 2 0 01-2 2h-5l-5 5v-5z"
        ></path>
      </svg>
    </div>
  </UserLayout>
</template>