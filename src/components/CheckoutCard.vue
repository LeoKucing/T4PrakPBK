<template>
    <div class="card-dark fade-in">
        <h4>{{ item.nama }}</h4>
        <p>Harga: Rp {{ item.harga }}</p>
        <p v-if="item.diskon">Diskon: {{ item.diskon }}%</p>
        <p>Total: Rp {{ finalHarga(item) }}</p>
    </div>
</template>

<script setup>
import { defineProps } from 'vue'

const props = defineProps({
    item: Object
})

function finalHarga(item) {
  return item.harga - (item.harga * item.diskon / 100)
}
</script>
