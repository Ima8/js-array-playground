<template lang="html">
  <div>
    <h1 class="title is-3">
      <b>{{ content.title }}</b>
      <span v-if="content.type === 'pure'" class="tag is-warning is-medium">Pure</span>
      <span v-if="content.type === 'impure'" class="tag is-danger is-medium">Impure</span>
    </h1>
    <p>
      {{ content.description }}
    </p>

    <div v-for="example in examples">
      <textarea v-model="example.code" class="hljs javascript input-code" rows="2"></textarea>
      <div class="button-group">
        <run-button :code="example.code" :run="run"></run-button>
      </div>
      <br>
    </div>

  </div>
</template>

<script>
import RunButton from './RunButton'

export default {
  data () {
    return {
    }
  },
  props: ['content', 'run'],
  // mounted () {
  //   this.inputCodes = this.content.examples
  // },
  computed: {
    examples () {
      return this.content.examples
    }
  },
  components: {
    RunButton
  }
}
</script>

<style lang="css">
textarea {
  resize: none;
  white-space: pre;
  overflow-wrap: normal;
  overflow-x: scroll;
}
.button-group {
  background-color: #282c34;
  padding: 8px;
  border-radius: 0px 0px 3px 3px;
}
.input-code {
  width: 100%;
  max-width: 100%;
  min-width: 100%;
  border-radius: 3px 3px 0px 0px;
  border: 0px;
  font-family: "Inconsolata", "Consolas", "Monaco", monospace;
  font-size: 14px;
}
</style>
