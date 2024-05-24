<template>
  <main>
    <h1 class="text-xl font-semibold">hello world</h1>
    <pre>{{ runs }}</pre>
  </main>


  <!-- <RouterView /> -->
</template>

<script setup lang="ts">
import { defineComponent, ref, onMounted } from 'vue'
// import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'

type runType = { id: number, title: string, startOn: string, completeOn: string, location: string, version: number }

const runs = ref<runType[]>([])

async function getRuns() {
  const response = await fetch('http://localhost:8080/api/runs')
  const data: runType[] = await response.json()
  runs.value = data && data || []
}

onMounted(() => {
  getRuns()
})


</script>
