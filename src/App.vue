<script setup lang="ts">
import { ref } from 'vue'

const message = ref('How are you doing? Sorry it took me too long to long to write back. How has summer been? What have you been doing during the summer? On my part, I have been traveling around the country with my family. I made new friends and new memories. I miss you. I cannot wait to go back to school and see you again. I also want to tell you about all my travel experiences when we are back in school. I will send you some of my pictures. I hope all is well with you. Send your family my love. See you soon.');

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
  <div class="max-w-2xl mx-auto">
    <div class="mb-8 bg-white shadow-lg rounded px-8 pt-6 pb-8">
      <p class="mb-6">{{letterGreeting}} {{to}},</p>

      <p class="mb-2">{{message}}</p>
      <p class="mb-6">{{letterClosing}},</p>

      <p class="flex justify-between"><span>{{from}}</span><span>{{sentDate}}</span></p>
    </div>
    <div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" label for="to">宛先</label>
        <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="to" type="text" v-model="to">
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="from">送り主</label>
        <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="from" type="text" v-model="from">
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="sent_date">送付時刻</label>
        <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="sent_date" type="text" v-model="sentDate">
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="message">本文</label>
        <textarea rows="6" class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="message" type="text" v-model="message"></textarea>
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="letter_greeting">頭語</label>
        <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="letter_greeting" type="text" v-model="letterGreeting">
      </div>
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="letter_closing">結語</label>
        <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="letter_closing" type="text" v-model="letterClosing">
      </div>
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
</style>
