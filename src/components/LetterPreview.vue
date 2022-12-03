<script setup lang="ts">
    const props = defineProps({
        to: String,
        from: String,
        message: String,
        sentDate: String,
        sentDatePosition: String,
        letterGreeting: String,
        letterGreetingPosition: String,
        letterClosing: String,
        letterClosingPosition: String,
    })
</script>
<template>
    <div class="mb-8 bg-white shadow-lg rounded">
        <div id="canvas-box" class="px-8 pt-6 pb-8">
            <p v-if="sentDate && sentDatePosition === 'above'" class="mb-2 text-right">{{sentDate}}</p>
            <p class="mb-4"><span v-if="letterGreeting && letterGreetingPosition === 'side'" class="inline-block mr-1">{{letterGreeting}}</span><span class="inline-block">{{to}}</span></p>
            <p v-if="letterGreetingPosition === 'below'" class="mb-4">{{letterGreeting}}</p>
            <p class="mb-4 whitespace-pre-wrap">{{message}}</p>
            <p :class="[letterClosingPosition === 'left' ? 'text-left' : 'text-right', 'mb-2']">{{letterClosing}}</p>
            <p v-if="sentDate && sentDatePosition === 'below'" class="mb-2">{{sentDate}}</p>
            <p class="text-right">{{from}}</p>
        </div>
    </div>
</template>
