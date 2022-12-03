<script setup lang="ts">
    const props = defineProps({
        to: String,
        from: String,
        message: String,
        sentDate: String,
        letterGreeting: String,
        letterClosing: String,
    })
</script>
<template>
    <div class="mb-8 bg-white shadow-lg rounded">
        <div id="canvas-box" class="px-8 pt-6 pb-8">
            <p class="mb-6"><span v-if="letterGreeting" class="inline-block">{{letterGreeting}}</span><span class="inline-block	 ml-1">{{to}}</span></p>
            <p class="mb-2 whitespace-pre-wrap">{{message}}</p>
            <p class="mb-6">{{letterClosing}}</p>
            <p class="flex justify-between"><span>{{from}}</span><span>{{sentDate}}</span></p>
        </div>
    </div>
</template>
