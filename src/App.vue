<template>
  <div class="ctr">
    <transition name="fade" mode="out-in" appear>
      <questions 
      :questions="questions"
      :questionsAnsweered="questionsAnsweered"
      @question-answered="questions_Answeered"
      v-if= "questionsAnsweered < questions.length"></questions>
      <results v-else
      :totalCorrect="totalCorrect"
      :results="results"></results>
    </transition>

    <button type="button" class="reset-btn"
     v-if="questionsAnsweered >= questions.length" 
     @click.prevent="reset"
     >Reset</button>

  </div>
</template>

<script>
import Results from './components/Results.vue';
import Questions from './components/Questions.vue'
// document.getElementById("app").appendChild(Questions)
export default {
  components: { Results,
  Questions },
  name: "App",
  
  data () {
    return {
    questionsAnsweered: 0,
    totalCorrect: 0,
    questions: [
        {
            q: 'What is 2 + 2?', 
            answers: [
                {
                    text: '4',
                    is_correct: true
                },
                {
                    text: '3',
                    is_correct: false 
                },
                {
                    text: 'Fish',
                    is_correct: false 
                },
                {
                    text: '5',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'How many letters are in the word "Banana"?', 
            answers: [
                {
                    text: '5',
                    is_correct: false
                },
                {
                    text: '7',
                    is_correct: false 
                },
                {
                    text: '6',
                    is_correct: true 
                },
                {
                    text: '12',
                    is_correct: false 
                }
            ] 
        },
        { 
            q: 'Find the missing letter: C_ke', 
            answers: [
                {
                    text: 'e',
                    is_correct: false
                },
                {
                    text: 'a',
                    is_correct: true 
                },
                {
                    text: 'i',
                    is_correct: false 
                }
            ] 
        },
    ],
    results: [
        {
            min: 0,
            max: 2,
            title: "Try again!",
            desc: "Do a little more studying and you may succeed!"
        },
        {
            min: 3,
            max: 3,
            title: "Wow, you're a genius!",
            desc: "Studying has definitely paid off for you!"
        }
    ]
}
  },
  methods: {
    questions_Answeered (is_correct) {
      if (is_correct){
        this.totalCorrect++
      }
      this.questionsAnsweered += 1
    },
    reset (){
        this.questionsAnsweered = 0
        this.totalCorrect = 0

    }
  }
  }
</script>

<style>
</style>
