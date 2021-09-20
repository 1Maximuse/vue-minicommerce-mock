<template>
  <div class="cart">
    <h1>Carts</h1>
    <div class="product-wrapper">
        <table>
          <tbody>
            <tr class="row" v-for="(product, index) in carts" :key="index">
              <td>
                <img src="https://via.placeholder.com/50">
              </td>
              <td>
                <p>{{ product.title }}</p>
              </td>
              <td>
                <h5>{{ product.price }}</h5>
              </td>
              <td>
                  <div @click="deleteFromCart(index)" class="product-delete">hapus</div>
              </td>
            </tr>
          </tbody>
          <tfoot>
            <tr >
              <td colspan="4">
                <button @click="checkout()">Checkout</button>
              </td>
            </tr>
          </tfoot>
        </table>

    </div>
  </div>
</template>

<style scoped lang="scss">
$orange: #f37021;
$white: #fff;

// layout
.product-wrapper {
  margin: 0 auto;
  padding: 1em;
  width: 75%;

  table {
    margin: 0 auto;
    width: 70%;

    .row {
      border-bottom: #ccc 1px;

      .product-delete {
        cursor: pointer;
      }
    }

    button {
      padding: 1em;
      background: $orange;
      color: $white;
      border: none;
      font-size: 1em;
      font-weight: bold;
      width: 100px;
      cursor: pointer;
      float: right;
    }
  }


}
</style>

<script>
import {mapActions, mapGetters} from "vuex";

export default {
  name: 'Cart',
  methods: {
    checkout() {
      return this.$router.push('/checkout')
    },
    ...mapActions([
        'getCart',
        'deleteFromCart'
    ])
  },
  computed: {
    ...mapGetters([
        'carts'
    ])
  },
  created() {
    this.getCart()
  }
}
</script>
