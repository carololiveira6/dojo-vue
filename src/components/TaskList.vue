<template>
  <div>
    <br />
    <div>
      <input v-model="time" @change="changeTime" type="checkbox" :id="`check-${props.index}`" />
      <label :for="`check-${props.index}`">{{ props.task }} {{ props.time }}</label>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue"

const props = defineProps({
  time: Number,
  task: String,
  index: Number
})

const time = ref(0)

const emit = defineEmits(['changeTime'])
function changeTime() {
  emit('changeTime', props.time)
  console.log(time)
}
</script>

<style></style>
