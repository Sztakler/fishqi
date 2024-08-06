<template>
    <div class="rounded-md border-2 px-4 py-8" :class="highlightClasses">
        {{ answer }}
        <p>{{ highlightClasses }}</p>
        <p>selected: {{ selected }}</p>
        <p>correct: {{ correct }}</p>
        <p>{{ correctHighlighted }}</p>
    </div>
</template>

<script setup>
const { answer, correctHighlighted, selected, correct } = defineProps([
    "answer",
    "correctHighlighted",
    "selected",
    "correct",
]);

const highlightClasses = computed(() => {
    const classes = ["bg-white", "bg-red-200", "bg-indigo-200"];
    console.log("selected", selected);

    if (selected) {
        if (!correct && correctHighlighted) return classes[1];
        else return classes[2];
    } else return classes[0];
});
</script>
