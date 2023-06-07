<script setup>
import { computed, ref } from 'vue';

const count = ref(0)
const double = computed(() => count.value * 2)
const emit = defineEmits(['increment'])
const color = computed(() => count.value >= 3 ? 'red' : 'black')

defineProps({
  prefix: String
})

function handleClic() {
  count.value++
  emit('increment')
}
</script>


<template>
  <div>
    <p class="compteur">
      {{ prefix }} compteur : {{ count }} *2 = {{ double }}

      <button @click="handleClic">Augmenter</button>
    </p>
  </div>
</template>


<style>
.compteur {
  color: v-bind(color);
}
</style>