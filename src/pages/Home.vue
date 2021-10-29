<template>
    <div>
        <Master>
            <div v-show="isLoad" class="container mt-5">
                <div class="row">
                    <div class="col text-center">
                        <div class="spinner-grow text-dark" role="status">
                            <span class="sr-only">Loading...</span>
                        </div>
                    </div>
                </div>
            </div>

            <div v-show="!isLoad" class="container mt-5">
                <div class="row">
                    <div
                        v-for="p in products"
                        :key="p.id"
                        class="col-md-4 col-lg-3 mb-3"
                    >
                        <div class="card border-0 shadow-sm">
                            <div class="card-body">
                                <img
                                    class="card-img-top mb-5"
                                    style="width: 100%; height: 250px"
                                    :src="p.image"
                                />
                                <h5 class="card-title">{{ p.title }}</h5>
                                <div class="card-text">
                                    {{
                                        p.description.substring(0, 100) + "..."
                                    }}
                                </div>
                            </div>
                            <div
                                class="
                                    card-footer
                                    d-flex
                                    justify-content-between
                                "
                            >
                                <p class="mb-0">$ {{ p.price }}</p>
                                <button
                                    @click="addToCart(p)"
                                    class="btn btn-sm btn-primary"
                                >
                                    Add to cart
                                </button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </Master>
    </div>
</template>

<script>
import Master from "../layouts/Master.vue";
import axios from "axios";
export default {
    name: "Home",
    components: { Master },
    data() {
        return {
            products: [],
            isLoad: true,
        };
    },
    created() {
        axios.get("https://fakestoreapi.com/products").then((res) => {
            this.products = res.data;
            this.isLoad = false;
        });
    },
    methods: {
        addToCart(p) {
            var cart = this.$root.cart;
            var isInCart = cart.find((v) => {
                return v.id == p.id;
            });

            if (isInCart) {
                isInCart.qty++;
            } else {
                cart.push({ ...p, qty: 1 });
            }
        },
    },
};
</script>
