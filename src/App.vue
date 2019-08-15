<template>
  <div id="app">
    <Header/>
    
    <QuestionBox v-if="questions.length"
    :question="questions[index]" :handleNext="next" 
    />
    
  </div>
</template>

<script>
import QuestionBox from './components/QuestionBox.vue'
import Header from './components/Header.vue'

export default {
  name: 'app',
  components: {
    QuestionBox,
    Header
  },
  // 
  data() {
    return {
      questions: [],
      index: 0
    }
  },
  methods: {
    next() {
      this.index++;
    }
  },
  mounted: function() {
    fetch('https://opentdb.com/api.php?amount=10', {
      method: 'get'
    }).then(function(res) {
      return res.json();
    }).then((data) => {
      this.questions = data.results;
    })
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
