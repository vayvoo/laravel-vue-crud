<template>
    <div class="container"> 
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            <div class="collapse navbar-collapse">
                <div class="navbar-nav">
                    <router-link to="/" class="nav-item nav-link">Mahsulotlar ro'yxati</router-link>
                    <router-link to="/create" class="nav-item nav-link">Yangi qo'shish</router-link>
                </div>
            </div>
        </nav>

        <router-view> </router-view>
    </div>
</template>
 
<script>
    export default {}
</script>