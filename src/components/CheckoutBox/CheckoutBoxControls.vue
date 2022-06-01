<template>
    <fragment>
        <h6 class="mt-4">Size<span class="text-danger">*</span></h6>
        <checkout-box-control-size-button
                v-for="(sButtonName, iIndex) in aSizes"
                @click-button="handleSelectSize"
                :key="iIndex"
                :s-active-button="sSize"
                :s-button-name="sButtonName"

        ></checkout-box-control-size-button>
        <br>
        <b-button variant="outline-secondary" class="m-1 mt-4 border-2" squared @click="handleAddToCart">ADD TO CART</b-button>
    </fragment>
</template>

<script>
    import CheckoutBoxControlSizeButton from './CheckoutBoxControlSizeButton';

    /**
     * CheckoutBoxControls Component
     *
     * @author Simon Peter Calamno <simon@simplexi.com.ph>
     * @since 2022.06.01
     */
    export default {
        name: 'CheckoutBoxControls',
        components: {CheckoutBoxControlSizeButton},
        props: {
            sSize : {
                type     : String,
                required : true
            },
            iProductId : {
                type     : Number,
                required : true
            }
        },
        data() {
            return {
                aSizes : [
                    'S',
                    'M',
                    'L'
                ]
            }
        },
        methods: {
            /**
             * Handles click of the add to cart button
             */
            handleAddToCart() {
                this.$emit('add-to-cart');
            },
            /**
             * Handles click of product size
             * @param sSize
             */
            handleSelectSize(sSize) {
                this.$emit('update-size', sSize);
            }
        }
    }
</script>

<style scoped>
    .active {
        color: #212529!important;
        background-color: transparent;
        border: 2px solid #000!important;
        box-shadow: initial!important;
    }

    .btn {
        color: #212529!important;
        background-color: transparent!important;
        box-shadow: initial!important;
    }

    .btn:active {
        color: #212529!important;
        background-color: transparent;
        border: 2px solid #000!important;
        box-shadow: initial!important;
    }

    .btn:focus {
        color: #212529!important;
        background-color: transparent;
        border: 2px solid #000!important;
        box-shadow: initial!important;
    }
</style>