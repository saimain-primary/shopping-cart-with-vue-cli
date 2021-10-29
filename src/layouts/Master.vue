<template>
    <div>
        <Nav></Nav>
        <slot></slot>
    </div>
</template>
<script>
import Nav from "./Nav.vue";
export default {
    name: "Master",
    components: { Nav },
};
</script>
