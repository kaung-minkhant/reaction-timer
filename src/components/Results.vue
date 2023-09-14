<template>
  <div class="result">
    <h1>Reaction Time Result</h1>
    <p>{{ score }} ms</p>

    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
export default {
  mounted() {
    if (this.score < 250) {
        this.rank = 'Ninja Fingers'
    } else if (this.score < 400) {
        this.rank = 'Rapic Reflexes'
    } else {
        this.rank = 'Snail Pace...'
    }
  },
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
};
</script>

<style scoped>
h1,
p {
  text-align: center;
  margin: 0;
  padding: 0;
}

h1 {
  color: red;
}

p {
  font-size: 2rem;
}

.result {
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: aqua;
  width: 400px;
  height: 200px;
  margin: 20px auto;
  border-radius: 2rem;
}

.rank {
    margin-top: 1rem;
    font-weight: bold;
}
</style>