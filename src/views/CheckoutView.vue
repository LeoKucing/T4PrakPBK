<template>
    <div style="padding: 30px; max-width: 600px; margin: auto;">

        <h3>🛒 Keranjang Pesanan</h3>

        <div v-if="items.length === 0">
        <p>Keranjang masih kosong.</p>
        </div>

        <div v-else>
        <CheckoutCard
            v-for="(item, i) in items"
            :key="i"
            :item="item"
        />

        <h4 style="margin-top:20px">Total Bayar: Rp {{ totalBayar }}</h4>

        <router-link to="/">
            <button class="btn-dark" style="margin-top: 20px;">Kembali ke Menu</button>
        </router-link>
        </div>

    </div>
</template>

<script setup>
import CheckoutCard from '../components/CheckoutCard.vue'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const items = JSON.parse(decodeURIComponent(route.query.items || '[]'))

const totalBayar = computed(() =>
    items.reduce((total, item) => {
        const hargaDiskon = item.harga - (item.harga * item.diskon / 100)
        return total + hargaDiskon
    }, 0)
)
</script>
