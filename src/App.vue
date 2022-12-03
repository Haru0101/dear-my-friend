<script setup lang="ts">
import { ref } from 'vue'
import html2canvas from 'html2canvas'
import LetterPreview from './components/LetterPreview.vue';

const message = ref('How are you doing? Sorry it took me too long to long to write back. How has summer been? What have you been doing during the summer? On my part, I have been traveling around the country with my family. I made new friends and new memories.\n\nI miss you. I cannot wait to go back to school and see you again. I also want to tell you about all my travel experiences when we are back in school. I will send you some of my pictures.\n\nI hope all is well with you. Send your family my love. See you soon.');

const to = ref<string>('Simon,');
const from = ref<string>('Michael');
const today: Date = new Date(Date.now());
const monthsFullSpell: string[] = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
const monthsIndex: number = today.getMonth();
const month: string = monthsFullSpell[monthsIndex];
const date: number = today.getDate();
const sentDate = ref<string>(`${month} ${date}`);
const letterClosing = ref<string>('Regards,');
const letterClosingPosition = ref<string>('left');
const letterGreeting = ref<string>('Dear');

const download = () => {
  // @ts-ignore
  html2canvas(document.querySelector("#canvas-box")).then((canvas: { toDataURL: (arg0: string) => string; }) => {
    let downloadEle = document.createElement("a");
    downloadEle.href = canvas.toDataURL("image/png");
    downloadEle.download = "letter.png";
    downloadEle.click();
  });
}
</script>
<template>
  <div class="p-6">
    <div class="w-full mx-auto max-w-3xl">
      <LetterPreview
        :to="to"
        :from="from"
        :sentDate="sentDate"
        :message="message"
        :letterGreeting="letterGreeting"
        :letterClosing="letterClosing"
        :letterClosingPosition="letterClosingPosition"
      ></LetterPreview>
      <div class="text-center mb-8">
        <button class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded inline-flex items-center" @click="download">
          <svg class="fill-current w-4 h-4 mr-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20"><path d="M13 8V2H7v6H2l8 8 8-8h-5zM0 18h20v2H0v-2z"/></svg>
          <span>Download</span>
        </button>
      </div>
      <div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" label for="to">頭語</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="to" type="text" v-model="letterGreeting">
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" label for="to">宛先</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="to" type="text" v-model="to">
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="message">本文</label>
          <textarea rows="6" class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="message" type="text" v-model="message"></textarea>
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="letter_closing">結語</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="letter_closing" type="text" v-model="letterClosing">
          <div class="mt-2 pl-1 flex align-center">
            <input v-model="letterClosingPosition" value="left" type="radio" name="letterClosingPosition" id="left" class="inline-block mr-1"><label for="left" class="text-sm">左寄せ</label>
            <input v-model="letterClosingPosition" value="right" type="radio" name="letterClosingPosition" id="right" class="inline-block mr-1 ml-2"><label for="right" class="text-sm">右寄せ</label>
          </div>
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="from">送り主</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="from" type="text" v-model="from">
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="sent_date">送付時刻</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="sent_date" type="text" v-model="sentDate">
        </div>
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
