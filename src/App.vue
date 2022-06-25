<script setup lang="ts">
import { ref } from 'vue'

const message = ref('The accounting department has recently informed me that your sales reports have consistently been submitted after the deadlines. Please respond to this email with reasons as to why you have failed to meet the deadlines.');

const to = ref('Simon');
const from = ref('MarkBorthwick');
const today = new Date(Date.now());
const monthsFullSpell = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const monthsIndex = today.getMonth();
const month = monthsFullSpell[monthsIndex];
const date = today.getDate();
const sentDate = ref(`${month} ${date}`);
const letterClosing = ref('Regards');
const letterGreeting = ref('Dear');

</script>

<template>
  <div class="mb-8 max-w-2xl mx-auto">
    <p class="mb-4">{{letterGreeting}} {{to}},</p>

    <p class="mb-2">{{message}}</p>
    <p class="mb-4">{{letterClosing}},</p>

    <p class="flex justify-between"><span>{{from}}</span><span>{{sentDate}}</span></p>
  </div>
  <div>
    <div>
      <label label for="to">宛先</label>
      <input id="to" type="text" v-model="to">
    </div>
    <div>
      <label for="from">送り主</label>
      <input id="from" type="text" v-model="from">
    </div>
    <div>
      <label for="sent_date">送付時刻</label>
      <input id="sent_date" type="text" v-model="sentDate">
    </div>
    <div>
      <label for="message">本文</label>
      <textarea id="message" type="text" v-model="message"></textarea>
    </div>
    <div>
      <label for="letter_greeting">頭語</label>
      <input id="letter_greeting" type="text" v-model="letterGreeting">
    </div>
    <div>
      <label for="letter_closing">結語</label>
      <input id="letter_closing" type="text" v-model="letterClosing">
    </div>
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
label {
  display: block;
}
input {
  display: block;
}
</style>
