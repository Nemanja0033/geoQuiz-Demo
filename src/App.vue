vue
<script setup>
import { ref, computed } from 'vue';

const questions = ref([
  {
    question: ' What is the name of the tallest mountain in the world?',
    answer: 0,
    options: [
      'Everest',
      'Alps',
      'Ural',
    ],
    selected: null
  },
  {
    question: 'What is the name of the longest river in Africa?',
    answer: 0,
    options: [
      'Nile',
      'Amazon',
      'Volga',
    ],
    selected: null
  },
  {
    question: ' What is the name of the largest ocean in the world?',
    answer: 2,
    options: [
      'Atlantic',
      'Indian',
      'The Pacific',
    ],
    selected: null
  },
  {
    question: 'How many time zones does Russia have?',
    answer: 1,
    options: [
      '10',
      '11',
      '12',
    ],
    selected: null
  },
  {
    question: 'What is the only country that borders the United Kingdom?',
    answer: 1,
    options: [
      'France',
      'Irelnad',
      'Scotland',
    ],
    selected: null
  },
  {
    question: 'What is the name of the world’s largest island?',
    answer: 0,
    options: [
      'Greenland',
      'Australia',
      'Japan',
    ],
    selected: null
  },
  {
    question: 'What country are the Great Pyramids of Giza located in?',
    answer: 0,
    options: [
      'Egypt',
      'Tunis',
      'Sudan',
    ],
    selected: null
  },
  {
    question: 'What is the capital city of Australia?',
    answer: 0,
    options: [
      'Canberra',
      'Sydney',
      'Melbourne',
    ],
    selected: null
  },
  {
    question: 'Which continent is known as the “Dark Continent”?',
    answer: 0,
    options: [
      'Africa',
      'Asia',
      'South America',
    ],
    selected: null
  },
  {
    question: 'Which river is the longest in South America?',
    answer: 1,
    options: [
      'Orinoco',
      'Amazon',
      'Parana',
    ],
    selected: null
  },
  {
    question: 'Which country has the most islands?',
    answer: 0,
    options: [
      'Sweden',
      'Canada',
      'Norway',
    ],
    selected: null
  },
  {
    question: 'What is the smallest country in the world by land area?',
    answer: 1,
    options: [
      'Monaco',
      'Vatican City',
      'San Marino',
    ],
    selected: null
  },
  {
    question: 'Which desert is the largest in the world?',
    answer: 1,
    options: [
      'Kalahari',
      'Sahara',
      'Gobi',
    ],
    selected: null
  },
  {
    question: 'Which country is known as the Land of the Rising Sun?',
    answer: 0,
    options: [
      'Japan',
      'China',
      'South Korea',
    ],
    selected: null
  },
  {
    question: 'Which U.S. state is the largest by area?',
    answer: 0,
    options: [
      'Alaska',
      'Texas',
      'California',
    ],
    selected: null
  },
  {
    question: 'Which mountain range separates Europe and Asia?',
    answer: 0,
    options: [
      'Ural',
      'Himalayas',
      'Andes',
    ],
    selected: null
  },
  {
    question: 'Which city is known as the City of Canals?',
    answer: 1,
    options: [
      'Amsterdam',
      'Venice',
      'Bruges',
    ],
    selected: null
  },
  {
    question: 'Which is the largest country by population?',
    answer: 0,
    options: [
      'China',
      'India',
      'USA',
    ],
    selected: null
  },
  {
    question: 'Which ocean is the smallest?',
    answer: 1,
    options: [
      'Atlantic',
      'Arctic',
      'Indian',
    ],
    selected: null
  },
  {
    question: 'Which island nation is located in the Indian Ocean?',
    answer: 0,
    options: [
      'Maldives',
      'Haiti',
      'Fiji',
    ],
    selected: null
  },
  {
    question: 'What is the name of the strait that separates Europe and Africa?',
    answer: 1,
    options: [
      'Bering Strait',
      'Gibraltar Strait',
      'English Channel',
    ],
    selected: null
  },
  {
    question: 'Which city is the capital of Canada?',
    answer: 1,
    options: [
      'Toronto',
      'Ottawa',
      'Vancouver',
    ],
    selected: null
  },
  {
    question: 'What is the capital city of Brazil?',
    answer: 0,
    options: [
      'Brasília',
      'São Paulo',
      'Rio de Janeiro',
    ],
    selected: null
  },
  {
    question: 'Which country is known for having the most volcanoes?',
    answer: 1,
    options: [
      'Japan',
      'Indonesia',
      'Philippines',
    ],
    selected: null
  },
  {
    question: 'Which mountain is known as the “Matterhorn of the Alps”?',
    answer: 0,
    options: [
      'Matterhorn',
      'Mont Blanc',
      'Eiger',
    ],
    selected: null
  },
  {
    question: 'What is the official language of Egypt?',
    answer: 0,
    options: [
      'Arabic',
      'French',
      'English',
    ],
    selected: null
  },
  {
    question: 'Which country is known as the Land of Fire and Ice?',
    answer: 0,
    options: [
      'Iceland',
      'Norway',
      'Greenland',
    ],
    selected: null
  },
  {
    question: 'Which river flows through Cairo?',
    answer: 0,
    options: [
      'Nile',
      'Tigris',
      'Euphrates',
    ],
    selected: null
  },
  {
    question: 'Which African country has the most pyramids?',
    answer: 0,
    options: [
      'Sudan',
      'Egypt',
      'Morocco',
    ],
    selected: null
  },
  {
  question: 'Which country is known for having the world’s largest coral reef system?',
  answer: 0,
  options: [
    'Australia',
    'Belize',
    'Philippines',
  ],
  selected: null
}
]);

const quizCompleted = ref(false);
const currentQuestion = ref(0);

const score = computed(() => {
  return questions.value.reduce((value, q) => {
    return value + (q.selected === q.answer ? 1 : 0);
  }, 0);
});

const getCurrentQuestion = computed(() => {
  return {
    ...questions.value[currentQuestion.value],
    index: currentQuestion.value
  };
});

const SetAnswer = (evt) => {
  questions.value[currentQuestion.value].selected = Number(evt.target.value); // Convert to number
};

const NextQuestion = () => {
  if (currentQuestion.value < questions.value.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
};
</script>

<template>
  <main class="app">
    <h1>GeoQuiz</h1>
    <section class="quiz" v-if="!quizCompleted">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
        <span class="score">Score {{ score }}/{{ questions.length }}</span>
      </div>
      <div class="options">
        <label v-for="(option, index) in getCurrentQuestion.options" :key="index" :class="`option ${
          getCurrentQuestion.selected === index
            ? index === getCurrentQuestion.answer
              ? 'correct'
              : 'wrong'
            : ''
        } ${
          getCurrentQuestion.selected != null && index !== getCurrentQuestion.selected
            ? 'disabled'
            : ''
        }`">
          <input 
            type="radio" 
            :name="`question-${getCurrentQuestion.index}`" 
            :value="index" 
            :disabled="getCurrentQuestion.selected !== null"
            @click="SetAnswer"
          />
          <span>{{ option }}</span>
        </label>
      </div>
      <button
        @click="NextQuestion"
        :disabled="getCurrentQuestion.selected === null">
        {{ 
          getCurrentQuestion.index === questions.length - 1 
            ? 'Finish'
            : 'Next Question'
        }}
      </button>
    </section>
    <section v-else>
      <h2>You have finished the quiz</h2>
      <p>Your score is {{ score }} / {{ questions.length }}</p>
    </section>
  </main>
</template>

<style scoped>
</style>