<template>
    <div
        class="rounded-md border-2 px-4 py-8"
        :class="{
            'bg-white-200 border-2 border-slate-200 hover:border-slate-400':
                !correctHighlighted && selected !== index,
            'bg-red-200 border-red-600':
                correctHighlighted &&
                selected !== correct &&
                selected === index,
            'bg-indigo-200 border-indigo-600': selected === index,
        }"
    >
        {{ answer }}
    </div>
</template>

<script setup>
const { answer, correctHighlighted, selected, correct, index } = defineProps([
    "answer",
    "correctHighlighted",
    "selected",
    "correct",
    "index",
]);
</script>
