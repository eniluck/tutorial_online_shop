<template>
    <div class="v-cart-item">
        <img class="v-cart-item__image" :src="require('../assets/images/' + cart_item_data.image)" alt="img">
        <div class="v-cart-item__info">
            <p class="v-cart-item__info-name">{{cart_item_data.name}}</p>
            <p class="v-cart-item__info-price">{{cart_item_data.price}}</p>
            <p class="v-cart-item__info-article">{{cart_item_data.article}}</p>
        </div>
        <div class="v_cart_item__info__quantity">
            <p>Qty:</p>
            {{cart_item_data.quantity}}
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
        }
    }
    // ,
    // mounted(){
    //     this.$set(this.cart_item_data, 'quantity',1)            
    // }
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

</style>