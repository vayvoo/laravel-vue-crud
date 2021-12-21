<template>
    <div>
        <h2 class="text-center">Mahsulotlar ro'yxati</h2>
 
        <table class="table">
            <thead>
            <tr>
                <th>Nomi</th>
                <th>Ma'lumot</th>
                <th>Rangi</th>
                <!-- <th>Actions</th> -->
            </tr>
            </thead>
            <tbody>
            <tr v-for="product in products" :key="product.id">
                <td>{{ product.name }}</td>
                <td>{{ product.detail }}</td>
                <td>{{ product.color }}</td>
                <td>
                    <div class="btn-group" role="group">
                        <router-link :to="{name: 'edit', params: { id: product.id }}" class="btn btn-success" style="margin-right: 10px;">Tahrirlash</router-link>
                        <button class="btn btn-danger" @click="deleteProduct(product.id)">O'chirish</button>
                    </div>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
</template>
 
<script>
    export default {
        data() {
            return {
                products: []
            }
        },
        created() {
            this.axios
                .get('http://localhost:8000/api/products/')
                .then(response => {
                    this.products = response.data;
                });
        },
        methods: {
            deleteProduct(id) { 
                this.axios
                    .delete(`http://localhost:8000/api/products/${id}`)
                    .then(response => {
                        let i = this.products.map(data => data.id).indexOf(id);
                        this.products.splice(i, 1)
                    });
            }
        }
    }
</script>