<template>
    <div class="flex flex-col p-4">
        <h2 class="text-4xl mb-8 text-slate-800">Your flashcards</h2>
        <div class="flex flex-col gap-2 justify-center">
            <Flashcard
                v-for="(flashcard, index) in flashcards"
                :key="index"
                :flashcard="flashcard"
                :correctHighlighted="correctHighlighted"
            />
            <button class="button" @click="toggleCorrect($event)">
                <span>Show correct</span>
            </button>
        </div>
    </div>
</template>

<script setup>
const correctHighlighted = ref(false);
const flashcards = ref([
    {
        question:
            "W wypadku niedostatecznie przygotowanej/przygotowanego do egzaminu studentki/studenta najlepszym rozwiązaniem z punktu widzenia oceny byłoby wejść na egzamin ustny",
        answers: [
            "po studentce/studencie bardzo dobrze przygotowanym",
            "po studentce/studencie średnio przygotowanym",
            "po studentce/studencie nieprzygotowanym",
        ],
        correctAnswer: 2,
        selectedAnswer: null,
    },
    {
        question:
            "Który z wymiarów tożsamości grupowej najsilniej wiąże się z postawą obywatelską?",
        answers: [
            "podporządkowanie",
            "ważność",
            "zaangażowanie",
            "poczucie wyższości",
        ],
        correctAnswer: 2,
        selectedAnswer: null,
    },
    {
        question: "Czy rywalizacja obniża motywacje twórczą?",
        answers: ["nie", "tak"],
        correctAnswer: 1,
        selectedAnswer: null,
    },
]);

function toggleCorrect() {
    correctHighlighted.value = !correctHighlighted.value;
    console.log(correctHighlighted.value);
}
</script>
