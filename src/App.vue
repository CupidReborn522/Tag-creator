<script>
import InputTag from './components/InputTag.vue';

export default {
  components: {
    InputTag,
  },
  data(){
    return {
      tagsLength: 0
    }
  },

  methods: {
    handleTagschange(tags) {
      console.log(tags)
      this.tagsLength = tags.length
    }

  },
}
</script>

<template>
  <h1>Tag input</h1>
  <div class="container">
  <h2 id="mssg" v-if="this.tagsLength == 0">Add your custom tag ;)</h2>
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
