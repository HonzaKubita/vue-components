<template>

<p>Min: {{ range.min }} | Max: {{ range.max }}</p>

<DoubleSlider :min="0" :max="100" :step="1" v-model="range"/>

</template>

<!-- Composition API -->
<script setup>

const range = reactive({ // Define a reactive for accessing the values
  min: 0,   // Position of the left slider (minimum)
  max: 100  // Position of the right slider (maximum)
})

</script>

<!-- Options API -->

<!--
<script>

export default {
  data: () => ({
    range: {
      min: 0,  // Position of the left slider (minimum)
      max: 100 // Position of the right slider (maximum)
    }
  })
}

</script>
-->
