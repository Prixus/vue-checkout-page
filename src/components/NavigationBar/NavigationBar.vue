<template>
    <div>
        <b-navbar toggleable="lg" type="dark" variant="light" class="justify-content-end text-black" >
            <b-navbar-brand href="#">NavBar</b-navbar-brand>
            <b-nav-item-dropdown v-if="aCart.length > 0" :text="sMyCartText" right>
                <b-dropdown-item
                        v-for="(oCartItem, iIndex) in aCart"
                        :key="iIndex"
                        href="#"> {{ oCartItem.sTitle }} </b-dropdown-item>
            </b-nav-item-dropdown>
            <b-nav-item-dropdown v-else :text="sMyCartText" disabled></b-nav-item-dropdown>
        </b-navbar>
    </div>
</template>

<script>
    /**
     * Navigation Bar Component
     * @author Simon Peter Calamno
     * @since 2022.06.01
     */
    export default {
        name: 'NavigationBar',
        props: {
            aCart : {
                type     : Array,
                required : true
            }
        },
        computed: {
            /**
             * Text that will show the my cart and number of items inserted in the cart
             * @returns {string}
             */
            sMyCartText() {
                const iCartCount = this.aCart.length;
                return `My Cart (${iCartCount})`;
            }
        }
    }
</script>

<style scoped>
.text-dark a {
    color: rgba(var(--bs-dark-rgb), var(--bs-text-opacity)) !important;
}

li {
    list-style: none!important;
}
</style>