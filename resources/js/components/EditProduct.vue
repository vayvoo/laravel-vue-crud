<template>
    <div>
        <h3 class="text-center">Mahsulotni o'zgartirish</h3>
        <div class="row">
            <div class="col-md-6">
                <form @submit.prevent="updateProduct">
                    <div class="form-group">
                        <label>Nomi</label>
                        <input type="text" class="form-control" v-model="product.name">
                    </div>
                    <div class="form-group">
                        <label>Ma'lumot</label>
                        <input type="text" class="form-control" v-model="product.detail">
                    </div>
                    <div class="form-group">
                        <label>Rangi</label>
                        <select class="form-control" v-model="product.color">
                            <option>Qizil</option>
                            <option>Yashil</option>
                            <option>Sariq</option>
                        </select>
                    </div>
                    <button type="submit" class="btn btn-primary">Qo'shish</button>
                </form>
            </div>
        </div>
    </div>
</template>
 
<script>
    export default {
        data() {
            return {
                product: {}
            }
        },
        created() {
            this.axios
                .get(`http://localhost:8000/api/products/${this.$route.params.id}`)
                .then((res) => {
                    this.product = res.data;
                });
        },
        methods: {
            updateProduct() {
                this.axios
                    .patch(`http://localhost:8000/api/products/${this.$route.params.id}`, this.product)
                    .then((res) => {
                        this.$router.push({ name: 'home' });
                    });
            }
        }
    }
</script>