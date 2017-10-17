<template>
<div class="col-6 col-sm-3">
    <div class="card" @click="deleteQuote">
    <div class="card-body">
        <h3 class="card-title">{{ quote.title }}</h3>
    <p class="mb-0"> "{{ quote.text }}" </p>
    <footer class="blockquote-footer mt-1">{{ quote.author }} in <cite title="Source Title">{{ quote.source }}</cite></footer>
    </div>
    </div>
</div>

</template>

<script>
export default {
    props:['quote'],
    methods:{
        deleteQuote(){
            this.$emit('deleteQuote', this.quote.id);
        }
    }
}
</script>

<style>
.card {
    background-color: #eeeeee;
    margin-top: 20px;
}

.card:hover { 
    cursor: pointer;
    background-color: #ffbab2;
}
</style>

