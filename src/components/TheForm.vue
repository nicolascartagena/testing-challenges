<template>
  <form>
    <div class="input-container">
      <label for="name">Name</label>
      <input type="text" id="name" name="name" />
    </div>
    <div class="input-container">
      <label for="email">Email</label>
      <input type="email" id="email" name="email" />
    </div>
    <div class="input-container">
      <label for="message">Mensaje</label>
      <textarea id="message" name="message"></textarea>
    </div>
    <div v-if="errors.length">
      debe rellenar su:
      <ul>
        <li v-for="error in errors" :key="error">{{ error }}</li>
      </ul>
      <br/>
    </div>
    <button type="button" @click="validateForm()">Send</button>
  </form>
</template>
<script setup lang="ts">
import { ref, type Ref } from 'vue';

const errors: Ref<Array<string>> = ref([]);
const name = ref('');
const email = ref('');
const message = ref('');

const validateForm = () => {
  errors.value = [];
  if (!name.value) {
    errors.value.push('Nombre');
  }
  if (!email.value) {
    errors.value.push('Email');
  }
  if (!message.value) {
    errors.value.push('Mensaje');
  }
};
</script>
<style scoped lang="scss">
form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 300px;
  .input-container {
    display: flex;
    flex-direction: column;
    margin-bottom: 1rem;
    label {
      margin-bottom: 0.5rem;
    }
    input,
    textarea {
      padding: 0.5rem;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  }
  button {
    padding: 0.5rem 1rem;
    border-radius: 5px;
    border: none;
    background: blue;
    color: white;
    cursor: pointer;
  }
}
</style>