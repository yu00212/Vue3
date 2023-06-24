<script setup lang="ts">
import {ref, reactive, computed, watch, toRefs} from 'vue'

  const itemName1 = ref<string>('Desk');
  const itemName2 = 'Bike';

  const item1 = reactive({
    name: 'Desk',
    price: 4000,
  });

  const price1 = 40000;
  const price2 = 20000;

  const url1 = 'https://www.amazon.co.jp/ref=nav_logo';

  const buy = (itemName: string) => {
    alert(itemName + 'を購入しますか?')
  }

  const budget = 50000;

  // const priceLabel = computed(() => {
  //   return item1.price > budget ? '値段が高すぎます！' : item1.price + ' yen';
  // });

const clear = () => {
    item1.name = ''
    item1.price = 0
}

const priceLabel = ref<string>(item1.price + ' yen')
const { price } = toRefs(item1);
watch(price, () => {
  return price.value > budget ? priceLabel.value = '値段が高すぎます。'
      : priceLabel.value = price.value + ' yen';
})

</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input v-model="item1.name" />
    <input v-model="item1.price" />
    <button @click="clear">Clear</button>
    <h1>最近の支出</h1>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel }}</label>
      <a :href="url1">bought at...</a>
      <button @click="buy(itemName1)">購入</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}円</label>
      <a :href="url1">bought at...</a>
      <button @click="buy(itemName2)">購入</button>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.payment {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  width: 400px;
  background-color: aliceblue;
}

input {
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;

}
</style>
