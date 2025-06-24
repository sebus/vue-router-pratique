<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'
import { RouterLink } from 'vue-router'

const UsersList = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://jsonplaceholder.typicode.com/users')
    // console.log(data)
    UsersList.value = data
  } catch (error) {
    console.log(error)
  }
})
</script>
<template>
  <main>
    <h1>User</h1>
    <p v-if="UsersList.length === 0">Chargement en cours...</p>
    <div v-else>
      <ul>
        <li v-for="user in UsersList" :key="user.id">
          <RouterLink
            :to="{
              name: 'user',
              params: { id: user.id },
            }"
            >{{ user.name }}</RouterLink
          >
          - {{ user.id }}
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
ul {
  margin: 24px 0;
}
</style>
