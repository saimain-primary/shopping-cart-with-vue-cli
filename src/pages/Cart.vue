<template>
    <Master>
        <div class="container">
            <div class="row">
                <div class="col">
                    <div class="card">
                        <div class="card-body">
                            <div class="table-responsive">
                                <table class="table">
                                    <thead>
                                        <tr>
                                            <th scope="col">Name</th>
                                            <th scope="col">Image</th>
                                            <th scope="col">Qty</th>
                                            <th scope="col">Price</th>
                                            <th scope="col">Total</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr v-for="p in cart" :key="p.id">
                                            <td>{{ p.title }}</td>
                                            <td>
                                                <img
                                                    width="50px"
                                                    :src="p.image"
                                                    alt=""
                                                />
                                            </td>
                                            <td>
                                                <span
                                                    @click="addQty(p)"
                                                    class="
                                                        btn btn-sm btn-success
                                                    "
                                                    >+</span
                                                >
                                                {{ p.qty }}
                                                <span
                                                    @click="reduceQty(p)"
                                                    class="
                                                        btn btn-sm btn-danger
                                                    "
                                                    >-</span
                                                >
                                            </td>
                                            <td>${{ p.price }}</td>
                                            <td>${{ p.price * p.qty }}</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </Master>
</template>

<script>
import Master from "../layouts/Master.vue";
export default {
    name: "Cart",
    components: { Master },
    data() {
        return {
            cart: [],
        };
    },
    created() {
        this.cart = this.$root.cart;
    },
    methods: {
        addQty(p) {
            p.qty++;
        },
        reduceQty(p) {
            if (p.qty > 1) {
                p.qty--;
            }
        },
    },
};
</script>
