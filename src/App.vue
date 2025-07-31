<script setup>
import { ref } from 'vue';
const products = ref([
  {
    id: 1,
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    stock: 20,
    edit: false
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    stock: 30,
    edit: false
  },
  {
    id: 3,
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    stock: 15,
    edit: false
  },
  {
    id: 4,
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    stock: 10,
    edit: false
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    stock: 25,
    edit: false
  },
  {
    id: 6,
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    stock: 20,
    edit: false
  },
  {
    id: 7,
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    stock: 18,
    edit: false
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    stock: 20,
    edit: false
  }
])

function editProduct(product) {
  product.edit = true;
}

function saveProduct(product) {
  product.edit = false;
}
</script>

<template>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
        <th scope="col">操作</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="product in products" :key="product.id">
        <td v-if="!product.edit">{{ product.name }}</td>
        <td v-else><input type="text" v-model="product.name"></td>
        <td><small>{{ product.description }}</small></td>
        <td>{{ product.price }}</td>
        <td>
          <button @click="product.stock--" :disabled="product.stock <= 0">-</button>{{ product.stock }}<button @click="product.stock++">+</button>
        </td>
        <td>
          <button v-if="!product.edit" @click="editProduct(product)">編輯</button>
          <button v-else @click="saveProduct(product)">確定</button>
        </td>
      </tr> 
    </tbody>
  </table>
</template>

<style scoped>
</style>
