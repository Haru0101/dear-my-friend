<script setup lang="ts">
import { ref } from 'vue'

const message = ref('The accounting department has recently informed me that your sales reports have consistently been submitted after the deadlines. Please respond to this email with reasons as to why you have failed to meet the deadlines.');

const to = ref('Simon');
const from = ref('MarkBorthwick');
const sentDate = ref('February 8, 8:59 A.M.');
const letterClosing = ref('Regards');
const letterGreeting = ref('Dear');

</script>

<template>
  <div>
    <p>{{letterGreeting}} {{to}},</p>

    <p>{{message}}

    {{letterClosing}},</p>

    <p>{{from}}</p>
    <p>{{sentDate}}</p>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
