<template>
  <div class="home">
    <h1>Home</h1>
    <input type="text" v-model="search">
    <p>search term - {{search}}</p>
    <div v-for="(name, idx) in matchingNames" :key="idx">{{ name }}</div>

  </div>
</template>

<script>
import {computed, ref, watch, watchEffect,reactive} from 'vue'

export default {
  name: 'Home',
  setup() {
    const search = ref('')
    const names = ref(['Bazil', 'Rick', 'Morty', 'Bender', 'Robby', 'Alex', 'Victor'])

    watch(search, () => {
      console.log('watch fire')
    })

    watchEffect(() => {
      console.log('watchEffect fire', search.value)
    })

    const matchingNames = computed(() => {
      return names.value.filter((name) => name.includes(search.value))
    })

    return {names, search, matchingNames }
  }
}
</script>
