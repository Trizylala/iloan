
<template>
<div v-show="title == selcTitle">
  <slot />
  
</div>
</template>

<script>
import { inject } from "vue";
export default {
  props:['title'],
  setup() {

      const selcTitle = inject("selcTitle")

      return {
        selcTitle
      }
    
  },
}
</script>