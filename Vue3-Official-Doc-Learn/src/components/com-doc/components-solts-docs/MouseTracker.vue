<script setup>// <!-- MouseTracker.vue -->
import { ref, onMounted, onUnmounted } from 'vue';
const x = ref(0)
const y = ref(0)
function update(e) {
    x.value = e.pageX; // 滑鼠座標
    y.value = e.pageY;
}
onMounted(() => { window.addEventListener('mousemove', update) })
onUnmounted(() => { window.removeEventListener('mousemove', update) })
</script>
<template>
    <slot :x="x" :y="y" />
</template>