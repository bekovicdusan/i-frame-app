<template>
  <div class="form-group">
    <label class="label title">Select output mode</label>
    <label for="iFrame" class="label radio">iFrame
      <input @change="$emit('mode-changing', selectedMode)" type="radio" name="selected_mode" value="iFrame" v-model="selectedMode"/>
    </label>
    <label for="source" class="label radio">Source
      <input @change="$emit('mode-changing', selectedMode)" type="radio" name="selected_mode" value="pre" v-model="selectedMode"/>
    </label>
  </div>
</template>

<script>

export default {
  setup() {
    const selectedMode = 'iFrame'

    return {
      selectedMode
    }
  }
}
</script>

