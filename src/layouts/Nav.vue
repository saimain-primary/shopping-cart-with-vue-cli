<template>
    <div class="pb-5">
        <nav class="navbar navbar-expand-lg navbar-light bg-light fixed-top">
            <div class="container-md">
                <router-link class="navbar-brand" to="/"
                    >Shopping Cart with Vue</router-link
                >
                <router-link class="navbar-brand" to="/cart"
                    ><i class="fas fa-shopping-cart"></i>
                    <span class="badge badge-danger rounded-pill">{{
                        cart.length
                    }}</span></router-link
                >
            </div>
        </nav>
    </div>
</template>

<script>
export default {
    name: "Nav",
    data() {
        return {
            cart: [],
        };
    },
    created() {
        this.cart = this.$root.cart;
    },
};
</script>
