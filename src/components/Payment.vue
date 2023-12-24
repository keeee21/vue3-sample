<script setup lang="ts">
  import { computed, reactive, ref, toRefs, watch } from 'vue';

  const itemName1 = ref<string>('Desk')

  const item1 = reactive({
    name: 'Desk',
    price: 400
  })

  const buy = (itemName: string) => {
    alert(itemName + '購入しました');
  }

  const clear = () => {
    item1.name = '';
    item1.price = 0;
  }

  const budeget = ref<number>(1000);

  // const priceLabel = computed(() => {
  //   return item1.price > budeget.value ? 'too expensive' : item1.price;
  // })

  const priceLabel = ref<string>(item1.price + '円');
  const { price } = toRefs(item1);
  watch(price, () => {
    if (item1.price > budeget.value) {
      priceLabel.value = 'too expensive';
    } else {
      priceLabel.value = item1.price + '円';
    }
  })
</script>

<template>
  <div class="container">
    <h1>最近の支出</h1>
    <input v-model="item1.name" >
    <input v-model="item1.price">
    <button v-on:click="clear">Clear</button>
    <div class="payment">
      <label>{{ item1.name }}</label>
      <label>{{ priceLabel }}</label>
      <button v-on:click="buy(itemName1)">BUY</button>
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
  height: 80px;
  width: 400px;
  background-color: aliceblue;
  align-items: center;
  margin-bottom: 8px;
}

input {
  margin-bottom: 8px;
}

label {
  font-size: 20px;
  font-weight: bold;
}
</style>