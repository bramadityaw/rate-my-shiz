<script setup>

import { ref } from 'vue'

const isFilled = ref({
  1: false,
  2: false,
  3: false,
  4: false,
  5: false
})

function resetStars() {
  for (let i = 0; i <= 5; i++) {
    isFilled.value[i] = false
  }
}

function fillStars(e) {
  resetStars()
  isFilled.value[e] = true
  if (e >= 2) {
    for (let i = 0; i <= e; i++) {
      isFilled.value[i] = true
    }
  }
}

</script>
<template>
  <div id="star-rating" class="m-auto">
    <button type="button" @click="fillStars(n)" @dblclick="resetStars" v-for="n in 5" :key="n">
      <img
        class="star"
        :src="'/src/assets/icons/star' + (isFilled[n] ? '_full' : '') + '.svg'"
        :alt="n + ' star' + (n > 1 ? 's' : '')"
      />
    </button>
  </div>
</template>