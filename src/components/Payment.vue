<script setup lang="ts">
  let itemName1 = 'Desk';
  const itemName2 = 'Bike';

  const price1 = 40000;
  const price2 = 20000;

  const url1 = 'https://www.amazon.co.jp/ref=nav_logo';

  const buy = (itemName: string) => {
    alert(itemName + 'を購入しますか?')
  }

  const input = (e: any) => {
    console.log('e:', e.target.value);
    itemName1 = e.target.value;
  }


</script>

<template>
  <div class="container">
    <h1>Payment</h1>
    <input @input="input"/>
    <h1>最近の支出</h1>
    <div class="payment">
      <label>{{ itemName1 }}</label>
      <label>{{ price1 }}</label>
      <a :href="url1">bought at...</a>
      <button @click="buy(itemName1)">購入</button>
    </div>
    <div class="payment">
      <label>{{ itemName2 }}</label>
      <label>{{ price2 }}</label>
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
label {
  font-size: 20px;
  font-weight: bold;

}
</style>
