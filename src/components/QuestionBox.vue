<template>
  <div>
  <b-jumbotron>

    <template slot="lead">
      {{ question.question }}
    </template>

    <hr class="my-4">

    <p>
      Lisf of answer
    </p>

    <b-button variant="primary" href="#">Submit</b-button>
    <b-button variant="success" href="#">Next</b-button>
  </b-jumbotron>
</div>
</template>


<script>
export default {
  props: {
    question: Object
  }
}
</script>
