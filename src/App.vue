<script setup lang="ts">
import { ref } from 'vue'
import html2canvas from 'html2canvas'
import LetterPreview from './components/LetterPreview.vue';

const message = ref('凛とした冷たい空気に、風花美しく輝くこの頃、佐藤様にはご清祥のことと存じます。\n\nさて、先日は素敵なお花をありがとうございました。おかげさまでとても思い出に残る誕生日となりました。大変お忙しいとは思いますが、お仕事が落ち着きましたらまたぜひお食事に行きましょう。\n\n季節の変わり目で体調を崩しやすい季節ですので、どうかご自愛ください。');

const to = ref<string>('佐藤様');
const from = ref<string>('高橋 太郎');
const today: Date = new Date(Date.now());
const year: number = today.getFullYear();
const month: number = today.getMonth() + 1;
const date: number = today.getDate();
const sentDate = ref<string>(`${year}年${month}月${date}日`);
const sentDatePosition = ref<string>('below')
const letterGreeting = ref<string>('拝啓');
const letterGreetingPosition = ref<string>('below')
const letterClosing = ref<string>('敬具');
const letterClosingPosition = ref<string>('right');

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
        :sentDatePosition="sentDatePosition"
        :message="message"
        :letterGreeting="letterGreeting"
        :letterGreetingPosition="letterGreetingPosition"
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
          <div class="mt-2 pl-1 flex align-center">
            <input v-model="letterGreetingPosition" value="below" type="radio" name="letterGreetingPosition" id="below" class="inline-block mr-1"><label for="below" class="text-sm">宛名の下</label>
            <input v-model="letterGreetingPosition" value="side" type="radio" name="letterGreetingPosition" id="side" class="inline-block mr-1 ml-2"><label for="side" class="text-sm">宛名の横</label>
          </div>
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
            <input v-model="letterClosingPosition" value="right" type="radio" name="letterClosingPosition" id="right" class="inline-block mr-1"><label for="right" class="text-sm">右寄せ</label>
            <input v-model="letterClosingPosition" value="left" type="radio" name="letterClosingPosition" id="left" class="inline-block mr-1 ml-2"><label for="left" class="text-sm">左寄せ</label>
          </div>
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="from">送り主</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="from" type="text" v-model="from">
        </div>
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="sent_date">送付時刻</label>
          <input class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="sent_date" type="text" v-model="sentDate">
          <div class="mt-2 pl-1 flex align-center">
            <input v-model="sentDatePosition" value="below" type="radio" name="sentDatePosition" id="below" class="inline-block mr-1"><label for="below" class="text-sm">下部</label>
            <input v-model="sentDatePosition" value="above" type="radio" name="sentDatePosition" id="above" class="inline-block mr-1 ml-2"><label for="above" class="text-sm">上部</label>
          </div>
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
