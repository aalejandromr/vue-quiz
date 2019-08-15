<template>
  <div>
  <b-jumbotron>

    <template slot="lead">
      {{ question.question }}
    </template>

    <hr class="my-4">

    <b-list-group>
      <b-list-group-item 
        v-for="(answer, index) in answers" :key="index"
        @click="selectAnswer(index)"
        :class="[ selectedAnwer === index && 'selected'] "
      >
        {{ answer }}
      </b-list-group-item>
    </b-list-group>

    <b-button variant="primary" href="#" >Submit</b-button>
    <b-button variant="success" href="#" @click="handleNext">Next</b-button>
  </b-jumbotron>
</div>
</template>


<script>
export default {
  props: {
    question: Object,
    handleNext: Function
  },
  data: () => {
    return {
      selectedAnwer: null
    }
  },
  computed: {
    answers() {
      let answers = [...this.question.incorrect_answers]
      answers.push(this.question.correct_answer);
      return answers;
    }
  },
  methods: {
    selectAnswer(index) {
      this.selectedAnwer = index;
    }
  }
}
</script>

<style scoped> 
/* scoped meaning it wont be global */

.list-group-item:hover {
  background-color: #EEE;
  cursor: pointer;
}

.selected {
  background-color: lightblue;
}

.correct-answer {
  background-color: lightgreen;
}

.incorrect-answer {
  background-color: lightcoral;
}

</style>