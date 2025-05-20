<template>
  <button
    @click="handleClick"
    @keydown.enter="handleClick"
    @keydown.space="handleClick"
    ref="button"
    class="keyboard-btn"
  >
    {{ label }}
  </button>
</template>

<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps({
  label: String,
});

const button = ref(null);

const handleClick = () => {
  alert(`${props.label} activated!`);
};

// Ensure button is focusable
onMounted(() => {
  button.value.focus();
});
</script>

<style>
.keyboard-btn {
  padding: 12px 24px;
  font-size: 16px;
  background: #41b883;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.keyboard-btn:focus {
  outline: 3px solid #ff8c00;
}
</style>