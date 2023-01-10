<template>
  <form class="mode-form">
    <label for="url" class="label url">Select website
      <input id="url" type="text" v-model="url" placeholder="Please enter the website's URL" />
    </label>
    <ModePicker @mode-changing="handleModeChange"/>
    <DynamicView :mode="selectedMode" :url="url"/>
  </form>
</template>

<script>
import { ref } from 'vue'

import DynamicView from './DynamicView.vue'
import ModePicker from './ModePicker.vue';

export default {
  components: {
    DynamicView,
    ModePicker
  },
  setup () {
    const selectedMode = ref('iFrame')
    const url = ref('')

    const handleModeChange = (mode) => {
      selectedMode.value = mode
    }

    return {
      selectedMode,
      url,
      
      handleModeChange
    }
  }
}
</script>