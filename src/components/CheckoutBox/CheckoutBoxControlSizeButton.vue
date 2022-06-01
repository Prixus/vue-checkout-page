<template>
    <b-button
            :class="{active : isActive}"
            @click="handleButtonClick"
            variant="outline-secondary"
            class="m-1"
            squared
    >
        {{ sButtonName }}
    </b-button>
</template>

<script>
    /**
     * CheckoutBoxControl Size Button Component
     *
     * @author Simon Peter Calamno
     * @since 2022.06.01
     */
    export default {
        name: 'CheckoutBoxControlSizeButton',
        props: {
            sActiveButton : {
                type     : String,
                required : true
            },
            sButtonName : {
                type : String,
                required: true
            }
        },
        computed : {
            isActive() {
                return this.sActiveButton === this.sButtonName;
            }
        },
        methods : {
            handleButtonClick() {
                this.$emit('click-button', this.sButtonName);
            }
        }
    }
</script>