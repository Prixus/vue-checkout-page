<template>
    <b-row class="mt-4">
        <b-card no-body>
            <b-row class="row-no-padding" border-variant="light">
                <b-col md="6">
                    <b-card-img src="https://mrdevelopertestassets.s3.ap-southeast-2.amazonaws.com/classic-tee.jpg" alt="Image" class="rounded-0"></b-card-img>
                </b-col>
                <b-col md="6">
                    <b-card-body>
                        <b-card-title title-tag="h5">
                            {{ sTitle }}
                        </b-card-title>
                        <b-card-sub-title sub-title-text-variant="">
                            <hr>
                                <strong>{{ sPrice }}</strong>
                            <hr>
                        </b-card-sub-title>
                        <b-card-text>
                            {{ sDescription }}
                            <checkout-box-controls
                                    :i-product-id="1"
                                    :s-size="sSize"
                                    @update-size="handleUpdateSize"
                                    @add-to-cart="handleAddToCart"
                            ></checkout-box-controls>
                        </b-card-text>
                    </b-card-body>
                </b-col>
            </b-row>
        </b-card>
    </b-row>
</template>

<script>
    import CheckoutBoxControls from './CheckoutBoxControls';

    /**
     * Initial data that will be used for the checkbox page
     * @type {{sDescription: string, sTitle: string, sPrice: string, sSize: string}}
     */
    const oDefaultData = {
        sTitle       : 'Classic Tee',
        sPrice       : '$75.00',
        sDescription : 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.',
        sSize        : '-'
    };

    /**
     * Checkbox Component
     * @author Simon Peter Calamno
     * @since 2022.06.01
     */
    export default {
        name       : 'CheckoutBox',
        components : {CheckoutBoxControls},
        data() {
            return {...oDefaultData}
        },
        methods: {
            /**
             * Handle Updating of the size state
             * @param sSize
             */
            handleUpdateSize(sSize) {
                this.sSize = sSize;
            },
            /**
             * Handles Add to cart of a selected product
             */
            handleAddToCart() {
                if (this.sSize === '-') {
                    alert('No Size has been selected');
                    return;
                }

                this.$emit('add-to-cart', {...this.$data});
                this.resetCheckoutData();
            },
            /**
             * Resets the checkout data
             */
            resetCheckoutData() {
                Object.assign(this.$data, {...oDefaultData});
            }
        }
    }
</script>