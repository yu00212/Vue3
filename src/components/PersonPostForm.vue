<script setup lang="ts">
import {computed, ref} from 'vue';
const inpputtingName = ref<string>('')
const inpputtingAge = ref<number>(0)

const emit = defineEmits(['register'])

const register = () => {
  const person = { id: Math.random(), name: inpputtingName.value, age: inpputtingAge }
  emit('register', person)
}

const nameLengthLimit = 15

const isValidName = computed(() => {
  if(inpputtingName.value.length >= nameLengthLimit) {
    return false
  } else {
    return true
  }
});

const color = computed(() => {
  return isValidName.value ? 'white' : 'rgb(244, 194, 190)'
})

</script>

<template>
  <div class="form-container">
    <div class="input-container">
      <div class="inout-column">
        <span>name:</span>
        <input class="input-name" v-model="inpputtingName"/>
      </div>
      <span class="error-message" v-if="!isValidName">{{ nameLengthLimit }}文字以上はだめだよ！！</span>
      <div class="inout-column">
        <span>age:</span>
        <input class="input" v-model="inpputtingAge" type="number"/>
      </div>
    </div>
    <button :disabled="!isValidName" @click="register" class="register-button">register</button>
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

.input-name {
  background-color: v-bind(color);
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

.error-message {
  font-size: 12px;
  color: rgb(244, 194, 190);
}
</style>