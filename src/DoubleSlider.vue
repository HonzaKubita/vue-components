<template>
  <div class="double-sliders">
    <input 
      type="range" 
      class="double-slider double-slider-left" 
      :min="props.min" 
      :max="props.max" 
      :step="props.step"
      v-model.number="min"
      @input="validateDoubleSlider('min')"
    >
    <input 
      type="range" 
      class="double-slider double-slider-right" 
      :min="props.min" 
      :max="props.max"
      :step="props.step" 
      v-model.number="max" 
      @input="validateDoubleSlider('max')"
    >
  </div>
</template>

<script setup>

const props = defineProps(["modelValue", "max", "min", "step", "space"]);
const emit = defineEmits(["update:modelValue"]);

const min = ref(props.modelValue.min);
const max = ref(props.modelValue.max);

function validateDoubleSlider(side) {
  if (side == "min" && min.value > max.value) {
    min.value = max.value;
  }
  else if (side == "max" && max.value < min.value) {
    max.value = min.value;
  }

  let value = {min: min.value, max: max.value}

  emit('update:modelValue', value);
}

</script>


<style>

.double-sliders {
  width: 90%;

  padding: 20px;

  display: flex;
  justify-content: center;
  align-items: center;

  position: relative;
}

.double-slider {
  -webkit-appearance: none;
  background: transparent; 
  position: absolute;
}

.double-slider-left::-webkit-slider-thumb {
  transform: translateX(-7.5px);
}
.double-slider-right::-webkit-slider-thumb {
  transform: translateX(7.5px);
}

.double-slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  height: 15px;
  width: 15px;
  border-radius: 50%;
  background: black;
  cursor: pointer;
  margin-top: -5px;
  position: relative;
  z-index: 1;
}
.double-slider::-webkit-slider-runnable-track {
  width: 100%;
  height: 5px;
  background: #e8e8e8;
  border-radius: 3px;
  border: none;
}

</style>
