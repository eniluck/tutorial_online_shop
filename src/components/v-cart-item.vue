<template>
    <div class="v-cart-item">
        <img class="v-cart-item__image" :src="require('../assets/images/' + cart_item_data.image)" alt="img">
        <div class="v-cart-item__info">
            <p class="v-cart-item__info-name">{{cart_item_data.name}}</p>
            <p class="v-cart-item__info-price">{{cart_item_data.price}}</p>
            <p class="v-cart-item__info-article">{{cart_item_data.article}}</p>
        </div>
        <div class="v_cart_item__info_quantity">
            <p>Qty:</p>
            <span>
                <span 
                    class="quantity__btn" 
                    @click="decrementItem">
                    -
                </span>
                {{cart_item_data.quantity}}
                <span 
                    class="quantity__btn" 
                    @click="incrementItem">
                    +
                </span>
            </span>
        </div>
        <button @click="deleteFromCart">
            Delete
        </button>
  </div>
</template>

<script>
export default {
    name: "v-cart-item",
    props: {
        cart_item_data: {
            type: Object,
            default(){
                return {}
            }
        }
    },
    data() {
        return {

        }
    },
    computed: {},
    methods: {
        deleteFromCart(){
            this.$emit('deleteFromCart')
        },
        decrementItem(){
            this.$emit('decrement')
        },
        incrementItem(){
            this.$emit('increment')
        }

    }
}
</script>

<style lang="scss">
    .v-cart-item{
        display: flex;
        font-weight: nowrap;
        justify-content: space-between;
        align-items: center;
        box-shadow:  0 0 8px 0 #e0e0e0;
        padding: $padding*2;
        margin-bottom: $margin*2;
        &__image {
            max-width: 50px;
        }
    }
    .quantity__btn{
        cursor: pointer;
    }

</style>