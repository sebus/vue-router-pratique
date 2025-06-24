<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

const props = defineProps({
  id: {
    type: String,
    required: true,
  },
})

const user = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get(`https://jsonplaceholder.typicode.com/users/${props.id}`)
    console.log(data)
    user.value = data
  } catch (error) {
    console.log(error)
  }
})
</script>
<template>
  <main>
    <p v-if="user.length === 0">Chargement en cours...</p>
    <div v-else>
      <h1>{{ user.name }}</h1>
      <p>Email: {{ user.email }}</p>
      <p>Phone: {{ user.phone }}</p>
    </div>
  </main>
</template>

<style scoped></style>
