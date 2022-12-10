<template>
  <button @click="$emit('CartPush')">Obten Carrito</button>

  <form action="" @submit.prevent="validateForm()">
    <table>
      <thead>
        <tr>
          <th>Index</th>
          <th>Name</th>
          <th>Photo</th>
          <th>Price</th>
          <th>Quantity</th>
          <th>Total</th>
          <th>Delete</th>
        </tr>
      </thead>
      <!--    {
            "uuid":"3",
            "name":"Vectorify",
            "description":"User Experience Design",
            "content":"Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.",
            "image":"https://github.com/ironhack-jc/mid-term-api/blob/main/3.jpg?raw=true",
            "purshased_at":"June 10, 2021",
          "price": 5.50,
          "quantity":1,
          "active": true
        }, 
   -->
      <tbody>
        <tr v-for="(item, index) of lineas" :key="index">
          <td>{{ index }}</td>
          <td>{{ item.name }}</td>
          <td><img :src="item.image" :alt="item.name" width="70" /></td>
          <td>{{ item.price }}€</td>
          <td>
            <button @click="decrementQuantity(item)" type="button">-</button>

            <input
              type="number"
              v-model.number="item.quantity"
              placeholder="0"
            />

            <button @click="++item.quantity" type="button">+</button>
          </td>
          <td>{{ priceLine(item) }}€</td>
          <td>
            <button @click="borrarElemento(index)" type="button">
              <i class="fa-solid fa-trash"></i>
            </button>
          </td>
        </tr>
      </tbody>

      <tfoot>
        <tr>
          <th colspan="6">Total: {{ precioTotal }}€</th>
        </tr>
      </tfoot>
    </table>
    <button type="submit">Confirmar compra</button>
  </form>
</template>

<script>
export default {
  // props: ["lineas", "precioTotal"],
  props: {
    lineas: Array,
    precioTotal: {
      type: Number,
      // required: false,
      default: 100,
    },
  },
  methods: {
    priceLine(item) {
      return item.price * item.quantity;
    },
    decrementQuantity(item) {
      if (item.quantity > 0) {
        --item.quantity;
      }
    },
    validateForm() {
      alert(`Hola`);
    },
    borrarElemento(pato) {
      this.$emit("borrar", pato);
    },
  },
};
</script>