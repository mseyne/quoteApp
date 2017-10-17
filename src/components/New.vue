
<template>
  <div class="form-group mt-3">
    <label for="Title" class="mt-1">Quote Title</label>
    <input type="text" class="form-control" id="Title" v-model="quote.title">
    <label for="newQuote" class="mt-1">New Quote</label>
    <textarea class="form-control noresize" id="newQuote" rows="2" v-model="quote.text"></textarea>
    <label for="Author" class="mt-1">Author</label>
    <input type="text" class="form-control" id="Author" v-model="quote.author">
    <label for="Source" class="mt-1">Source</label>
    <input type="text" class="form-control" id="Source" v-model="quote.source">
    <div class="d-flex justify-content-center mt-3"><button class="btn btn-primary" @click="addQuote">New Quote</button></div>
  </div>
</template>

<script>
export default {
  props: ['nbQuotes'],
  data: function() {
    return {
      quote: {
        title:'',
        text:'',
        author:'',
        source:''
      }
    }
  },
  methods: {
    addQuote: function() {
      const max = this.nbQuotes.max;
      const now = this.nbQuotes.now;
      if ( now < max ) {
        this.$emit('new', this.quote);
      } else {
        this.$emit('alert');
      }
    }
  }
}
</script>


<style scoped>

textarea {
    resize: none;
}

button {
  cursor: pointer;
}
</style>

