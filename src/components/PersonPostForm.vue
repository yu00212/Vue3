<script setup lang="ts">
import { ref } from 'vue';
const inpputtingName = ref<string>('')
const inpputtingAge = ref<number>(0)

const emit = defineEmits(['register'])

const register = () => {
  const person = { id: Math.random(), name: inpputtingName.value, age: inpputtingAge }
  emit('register', person)
}

</script>

<template>
  <div class="form-container">
    <div class="input-container">
      <div class="inout-column">
        <span>name:</span>
        <input class="input" v-model="inpputtingName"/>
      </div>
      <div class="inout-column">
        <span>age:</span>
        <input class="input" v-model="inpputtingAge" type="number"/>
      </div>
    </div>
    <button @click="register" class="register-button">register</button>
  </div>
</template>

<style scoped>
.form-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(255, 241,226);
  padding: 24px 0;
  width: 50%;
  margin-bottom: 12px;
  border-radius: 4px;
}

.inout-column {
  width: 200px;
  display: flex;
  justify-content: space-between;
}

input {
  width: 120px;
  margin-bottom: 8px;
}

.input-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 50px;
  margin-bottom: 20px;
}

span {
  font-size: 20px;
  font-weight: bold;
}
</style>