<template>
  <div>
    <h1>Vue Composition API (Vue3 Approach)</h1>
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
import { ref, toRefs, watch } from "vue";

export default {
  name: "CompositionVueComponent",
  props: {
    sampleWords: [String],
  },
  setup(props) {
    // Case: Props
    const { sampleWords } = toRefs(props);

    // Case: Data
    let sentence = ref("");
    let totalSentence = ref("");
    let wordCount = ref(3);

    // Case: Watchers
    watch(sentence, (newValue) => (totalSentence.value += newValue));

    // Case: Methods
    function generateSentence() {
      let tempSentence = "";
      for (let i in wordCount) {
        tempSentence +=
          sampleWords.value[
            Math.floor(Math.random() * sampleWords.value.length)
          ] + " ";
      }
      sentence.value = tempSentence;
    }

    function clear() {
      totalSentence.value = "";
    }

    return {
      sentence,
      totalSentence,
      wordCount,
      generateSentence,
      clear,
    };
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
