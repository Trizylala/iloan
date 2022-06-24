
<template>
<div class="tabs border-b-4 mb-3">
  <ul class="tab__header flex gap-1  flex-wrap -mb-px">
    <li v-for="title in tabTitles" :key="title"
    @click="selcTitle = title"
    class="mr-2 cursor-pointer"
    :class="{'text-yellow-300': title == selcTitle}">
      <span class="inline-block py-3 px-2 text-sm md:text-lg font-medium text-center text-gray-200 hover:text-gray-800 hover:border-purple-600">{{title}}</span>
    </li>
  </ul>
</div>
  <slot />
</template>

<script>
import { provide, ref } from "vue";
export default {
  setup(props, { slots }) {

    const tabTitles = ref(slots.default().map((tab) => tab.props.title))

    const selcTitle = ref(tabTitles.value[0])

    provide("selcTitle", selcTitle)


    return {
      tabTitles,
      selcTitle

    }
    
  },
}
</script>