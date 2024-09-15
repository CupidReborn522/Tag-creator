<script>
import InputTag from './components/InputTag.vue';

export default {
  components: {
    InputTag,
  },
  methods: {
    handleTagschange(tags) {
      console.log('equisde');
    }

  },
}
</script>

<template>
  <h1>Hello world!!</h1>

  <InputTag :onTagsChange="handleTagschange" />
</template>

<style scoped>
h1 {
  text-align: center;
  padding: 10px;
}
</style>
