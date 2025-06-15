<template>
    <div class="card-dark fade-in">
        <h3>{{ menu.nama }} ☕</h3>
        <p>Harga: Rp {{ menu.harga }}</p>
        <p v-if="menu.diskon">Diskon: {{ menu.diskon }}%</p>

        <button class="btn-dark" @click="tambah">Tambah Pesanan</button>
    </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

const props = defineProps({
    menu: Object
})

const emit = defineEmits(['pesan'])

function tambah() {
    emit('pesan', props.menu)
}
</script>