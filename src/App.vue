<script>
import InputTag from './components/InputTag.vue';

export default {
  components: {
    InputTag,
  },
  methods: {
    handleTagschange(tags) {
      console.log(tags)
    }

  },
}
</script>

<template>
  <h1>Tag input</h1>
  <h2>Add your custom tag ;)</h2>
<div class="container">
  <InputTag @onTagsChange="handleTagschange" />
</div>
</template>

<style scoped>
h1 {
  text-align: center;
  padding: 10px;
}
.container{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  padding:25px;
}
</style>
