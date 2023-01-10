<template>
  <div class="view">
    <button class="load-button" @click.prevent="handleClick">
      Load
    </button>
    <component class="dynamic-view" :is="selectedMode" :src="selectedUrl" v-show="shouldShow">
      {{ content }}
    </component>
    <iframe :src="selectedUrl" frameborder="0" hidden ref="hiddenFrame"></iframe>
  </div>
</template>

<script>
import { computed, ref } from 'vue'

export default {
  props: {
    mode: {
      type: String,
      required: true
    },
    url: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const shouldShow = ref(false) 
    const selectedMode = computed(() => props.mode)
    const selectedUrl = computed(() => props.url)
    const hiddenFrame = ref(null)
    const content = ref('')

    const handleClick = () => {
      shouldShow.value = true
      
      content.value = hiddenFrame.value.contentWindow.document.body.innerHtml || 'please enter a url of the website'
    }

    return {
      shouldShow,
      selectedMode,
      selectedUrl,
      hiddenFrame,
      content,

      handleClick
    }
  }
}
</script>