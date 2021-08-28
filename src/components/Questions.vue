<template>
  <div class="questions-ctr">
        <div class="progress">
            <div class="bar" :style="{     
                width:`${(questionsAnsweered/questions.length ) * 100}%`
            }"></div>
            <div class="status">{{questionsAnsweered}} out of {{questions.Length}} questions answered</div>
        </div>
        <transition-group mode="in-out" name="fade"
>
        <div class="single-question" 
        v-for="(question, qi) in questions" :key="question.q"
        v-show="questionsAnsweered === qi">
            <div class="question">{{question.q}}</div>
            <div class="answers" 
            v-for="answer in question.answers"
            :key="answer.text">
                <div class="answer"
                @click.prevent="selectAnswer(answer.is_correct)"
                >{{ answer.text}}</div>
            </div>
        </div>
        </transition-group>
    </div>
</template>

<script>
export default {
    props: {
        questions: Array,
        questionsAnsweered: Number
    },
    emits:["question-answered"],
    methods:{
        selectAnswer (is_correct) {
            this.$emit('question-answered', is_correct)
        }
    }

}
</script>

<style>

</style>