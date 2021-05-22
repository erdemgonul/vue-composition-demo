<template>
  <div>
    <h1>Vue Options API (Traditional Vue Approach)</h1>
    <label>Word Count:</label>
    <div>
      <input type="number" v-model="wordCount" />
      <br />
      <input
        type="button"
        @click="generateSentence"
        value="Generate Random Sentences"
      />
      <input type="button" @click="clear" value="Clear" />
    </div>
    <h1>Generated Sentence:</h1>
    <h1>{{ sentence }}</h1>

    <h3>Total Generated Sentence:</h3>
    <h3>{{ totalSentence }}</h3>
  </div>
</template>

<script>
export default {
  name: "TraditionalVueComponent",
  //Case: Props
  props: {
    sampleWords: [String],
  },
  //Case: Data
  data() {
    return {
      sentence: "",
      wordCount: 3,
      totalSentence: "",
    };
  },
  //Case: Methods
  methods: {
    generateSentence() {
      let tempSentence = "";
      for (let i = 0; i < this.wordCount; i++) {
        tempSentence +=
          this.sampleWords[
            Math.floor(Math.random() * this.sampleWords.length)
          ] + " ";
      }
      this.sentence = tempSentence;
    },
    clear() {
      this.totalSentence = "";
    },
  },
  //Case: Watch
  watch: {
    sentence(oldValue, newValue) {
      this.totalSentence += newValue;
    },
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
input {
  margin: 10px 0 0;
}
input[type="button"] {
  padding: 10px;
  margin-right: 20px;
  border-radius: 10px;
}
</style>
