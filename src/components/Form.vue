<script setup lang="ts">
    const props = defineProps({
        to: String,
        from: String,
        message: String,
        sentDate: String,
        letterGreeting: String,
        letterClosing: String,
    })
    const emit = defineEmits(['update:to', 'update:from', 'update:sentDate', 'update:message', 'update:letterGreeting', 'update:letterClosing',]);
</script>
<template>
    <div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" label for="to">宛先</label>
            <input
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="to" type="text" :value="to" @input="$emit('update:to', $event.target.value)">
        </div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="from">送り主</label>
            <input
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="from" type="text" :value="from" @input="$emit('update:from', $event.target.value)">
        </div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="sent_date">送付時刻</label>
            <input
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="sent_date" type="text" :value="sentDate" @input="$emit('update:sentDate', $event.target.value)">
        </div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="message">本文</label>
            <textarea rows="6"
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="message" type="text" :value="message" @input="$emit('update:message', $event.target.value)"></textarea>
        </div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="letter_greeting">頭語</label>
            <input
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="letter_greeting" type="text" :value="letterGreeting" @input="$emit('update:letterGreeting', $event.target.value)">
        </div>
        <div class="mb-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="letter_closing">結語</label>
            <input
                class="block shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
                id="letter_closing" type="text" :value="letterClosing" @input="$emit('update:letterClosing', $event.target.value)">
        </div>
    </div>
</template>