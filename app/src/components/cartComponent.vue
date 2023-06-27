<template>
    
</template>

<script>
export default {
  name: 'CartComponent',
  props: {
    cart: Array
  },
  computed: {
    canCheckout(){
        if(this.userData.phone.match(/^[0-9]+$/) != null & this.userData.name.match(/^[A-Za-z]+$/) != null){
            return true
        }
        return false
    },
  },
  methods:{
    removeFromCart(subject){
            this.$emit("remove-cart",JSON.stringify(subject))
        },
    submit_cart(){
        this.$emit("submit-cart")
    }
  },
  data(){
      return {
        cart_array:this.cart,
      userData:{
          name:"",
          phone:"",
      }
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
