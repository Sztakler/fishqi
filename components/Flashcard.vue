<template>
    <div class="flex flex-col shadow-md w-1/2 p-4 gap-4">
        <h3 class="font-medium text-lg mb-4">{{ flashcard.question }}</h3>
        <p class="font-bold text-slate-500">Wybierz poprawną odpowiedź</p>
        <ol class="grid grid-cols-2 gap-4">
            <Answer
                v-for="(answer, index) in flashcard.answers"
                :key="index"
                @click="selectAnswer(index)"
                :answer="answer"
                :correctHighlighted="correctHighlighted"
                :selected="flashcard.selectedAnswer"
                :correct="flashcard.correctAnswer"
                :index="index"
            />
        </ol>
    </div>
</template>

<script setup>
const { flashcard, correctHighlighted } = defineProps([
    "flashcard",
    "correctHighlighted",
]);

const selected = ref(false);
const correct = ref(flashcard.correctAnswer === selected.value);

const emit = defineEmits(["select-answer"]);

function selectAnswer(index) {
    flashcard.selectedAnswer = index;
    emit("select-answer", index);
}

function assignHighlightClasses(index) {
    const classes = ["bg-white", "bg-red-200", "bg-indigo-200"];
    return computed(() => {
        console.log("computed");
        if (flashcard.selectedAnswer === index) {
            if (
                flashcard.selectedAnswer !== flashcard.correctAnswer &&
                correctHighlighted
            )
                return classes[1];
            else return classes[2];
        } else return classes[0];
    });
}
</script>

<style scoped>
/* styles for simple list design */
/* ol {
    counter-reset: list;
}
ol > li {
    list-style: none;
}
ol > li:before {
    content: counter(list, lower-alpha) ") ";
    counter-increment: list;
} */
</style>
