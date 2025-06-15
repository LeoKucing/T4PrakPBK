<template>
    <div style="padding: 30px; max-width: 600px; margin: auto;">

        <h3>Pilihan Menu</h3>

        <CoffeeCard
        v-for="menu in menus"
        :key="menu.id"
        :menu="menu"
        @pesan="tambahPesanan"
        />

        <div style="text-align: center; margin-top: 30px;">
        <router-link :to="{ path: '/checkout', query: { items: encodeURIComponent(JSON.stringify(keranjang)) }}">
            <button class="btn-dark">Lihat Keranjang ({{ keranjang.length }})</button>
        </router-link>
        </div>

    </div>
</template>

<script setup>
import CoffeeCard from '../components/CoffeeCard.vue'
import { ref } from 'vue'

const keranjang = ref([])

const menus = [
    { id: 1, nama: 'Es Kopi Susu RGT', harga: 18000, diskon: 20 },
    { id: 2, nama: 'Kopi Hitam Signature', harga: 15000, diskon: 0 },
    { id: 3, nama: 'Latte Rengat', harga: 20000, diskon: 10 },
]

function tambahPesanan(menu) {
    keranjang.value.push(menu)
}
</script>
