<template>
  <div class="result">
    <div class="title">
      You got {{ totalCorrect }} out of {{ questionsAnswered }}
    </div>
    <div class="desc">
      <div v-if="totalCorrect === questionsAnswered">
        You got them all correct!
      </div>
      <div
        v-else-if="
          totalCorrect > questionsAnswered / 2 &&
          totalCorrect < questionsAnswered
        "
      >
        Not bad!
      </div>
      <div v-else>You need to practice more!</div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["questionsAnswered", "totalCorrect"],
};
</script>

<style></style>
