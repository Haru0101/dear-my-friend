<script setup lang="ts">
    const props = defineProps({
        to: String,
        from: String,
        message: String,
        sentDate: String,
        letterGreeting: String,
        letterGreetingPosition: String,
        letterClosing: String,
        letterClosingPosition: String,
    })
</script>
<template>
    <div class="mb-8 bg-white shadow-lg rounded">
        <div id="canvas-box" class="px-8 pt-6 pb-8">
            <p class="mb-6"><span v-if="letterGreeting && letterGreetingPosition === 'side'" class="inline-block mr-1">{{letterGreeting}}</span><span class="inline-block">{{to}}</span></p>
            <p v-if="letterGreetingPosition === 'below'">{{letterGreeting}}</p>
            <p class="mb-2 whitespace-pre-wrap">{{message}}</p>
            <p :class="[letterClosingPosition === 'left' ? 'text-left' : 'text-right', 'mb-6']">{{letterClosing}}</p>
            <p class="flex justify-between"><span>{{from}}</span><span>{{sentDate}}</span></p>
        </div>
    </div>
</template>
