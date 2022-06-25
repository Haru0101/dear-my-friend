<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup

const message = 'The accounting department has recently informed me that your sales reports have consistently been submitted after the deadlines. Please respond to this email with reasons as to why you have failed to meet the deadlines.';

const to = 'Simon';
const from = 'MarkBorthwick';
const sentDate = 'February 8, 8:59 A.M.';
const letterClosing = 'Regards';
const letterGreeting = 'Dear';
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
