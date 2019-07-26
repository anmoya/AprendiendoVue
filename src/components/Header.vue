<template>
  <div>
    <b-nav tabs>
      
      <b-nav-item disabled><b>Quiz</b></b-nav-item>
      <b-nav-item disabled>Counter: {{ currentIndex+1 }}/{{ totalQuestions }}</b-nav-item>
    </b-nav>
  </div>
</template>

<script>
export default {
  props: {
    totalQuestions: Number,
    currentIndex: Number
  }

}
</script>

