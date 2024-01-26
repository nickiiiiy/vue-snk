<script setup>
import { ref, onMounted } from 'vue'
import CardList1 from '../components/CardList1.vue'

import axios from 'axios'

const orders = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://28c151f355b88608.mokky.dev/orders')
    orders.value = data.map((obj) => obj.item)
  } catch (err) {
    console.log(err)
  }
})
</script>
<template>
  <h2 class="text-3xl font-bold mb-8">Мои заказы</h2>
  <CardList1 />
</template>
