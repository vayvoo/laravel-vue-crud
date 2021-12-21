<template>
    <div>
        <h3 class="text-center">Mahsulot qo`shish</h3>
        <div class="row">
            <div class="col-md-6">
                <form @submit.prevent="addProduct">
                    <div class="form-group">
                        <label>Nomi</label>
                        <input type="text" class="form-control" v-model="product.name">
                    </div>
                    <div class="form-group">
                        <label>Ma`lumot</label>
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
                    <button type="submit" class="btn btn-primary" style="margin-top: 10px;">Qo'shish</button>
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
        methods: {
            addProduct() {
                this.axios
                    .post('http://localhost:8000/api/products', this.product)
                    .then(response => (
                        this.$router.push({ name: 'home' })
                    ))
                    .catch(err => console.log(err))
                    .finally(() => this.loading = false)
            }
        }
    }
</script>