<script setup lang="ts">
import { TresCanvas, useRenderLoop } from '@tresjs/core'
import { OrbitControls } from '@tresjs/cientos'
import { ref } from 'vue'

const torusRef = ref()
const plus1 = ref()
const plus2 = ref()

// Используем useRenderLoop для анимации
const { onLoop } = useRenderLoop()

onLoop(({ delta }) => {
  if (torusRef.value) {
    // Вращаем фигуру по оси Y
    torusRef.value.rotation.y += delta
  }
  if (plus1.value) {
    // Вращаем фигуру по оси Y
    plus1.value.rotation.y += delta
  }
  if (plus2.value) {
    // Вращаем фигуру по оси Y
    plus2.value.rotation.y += delta
  }
})
</script>

<template>
  <TresCanvas clear-color="#82DBC5" window-size>
    <TresPerspectiveCamera :position="[3, 0, 6]" />

    <OrbitControls />

    <TresMesh ref="torusRef">
      <TresTorusGeometry :args="[2.5, 0.4, 32, 64]" />
      <TresMeshBasicMaterial color="orange" />
    </TresMesh>

    <!-- Буква "L" -->
    <TresMesh :position="[-2, 0, 0]">
      <TresBoxGeometry :args="[0.1, 0.5, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[-1.85, -0.25, 0]">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>

    <!-- Буква "U" -->
    <TresMesh :position="[-1.2, 0, 0]">
      <TresBoxGeometry :args="[0.1, 0.5, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[-0.9, 0, 0]">
      <TresBoxGeometry :args="[0.1, 0.5, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[-1.05, -0.25, 0]">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>

    <!-- Буква "I" -->
    <TresMesh :position="[-0.4, 0, 0]">
      <TresBoxGeometry :args="[0.1, 0.5, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>

    <!-- Буква "S" -->
    <TresMesh :position="[0.2, 0.25, 0]">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[0, 0.1, 0]">
      <TresBoxGeometry :args="[0.1, 0.3, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[0.2, -0.1, 0]">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[0.4, -0.25, 0]">
      <TresBoxGeometry :args="[0.1, 0.3, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[0.2, -0.4, 0]">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>

    <!-- Символ "+" -->
    <TresMesh :position="[1, 0, 0]" ref="plus1">
      <TresBoxGeometry :args="[0.4, 0.1, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>
    <TresMesh :position="[1, 0, 0]" ref="plus2">
      <TresBoxGeometry :args="[0.1, 0.4, 0.1]" />
      <TresMeshBasicMaterial color="white" />
    </TresMesh>

    <TresAmbientLight :intensity="1" />
  </TresCanvas>
</template>

<style>
html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}
#app {
  height: 100%;
  width: 100%;
}
</style>
