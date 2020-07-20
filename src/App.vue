<template>
  <div class="container">
    <div class="row justify-content-md-center">
      <div class="col-md mt-4">
        <h1 class="text-center">The Super Quiz</h1>
        <hr>
      </div>
    </div>
    <div class="row justify-content-md-center">
      <div class="col-md-6 mt-4">
        <transition enter-class=""
                    enter-active-class="animate__animated animate__flipInY animate__fast"
                    leave-class="animate__animated "
                    leave-active-class="animate__animated animate__flipOutY animate__fast"
                    mode="out-in">
          <component :is="mode" @answered="answered($event)" @confirmed="mode = 'app-question'"></component>
        </transition>
      </div>
    </div>
  </div>
</template>

<script>
  import Anser from './components/Answer.vue';
  import Question from './components/Question.vue';

export default {
  data(){
    return {
      mode : 'app-question'
    };
  },
  methods: {
    answered (isCorrect){
      if (isCorrect) {
        this.mode = 'app-answer';
      } else {
        this.mode = 'app-question';
        alert('Wrong, try again!');
      }
    }
  },
  components : {
    appAnswer : Anser,
    appQuestion : Question,
  }
}
</script>

<style>

</style>
