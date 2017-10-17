<template>
<div class="container">
    <h1 class="text-center mt-4">Quotes App</h1>
  <div class="row">
    <div class="col">
        <app-bar :nbQuotes="nbQuotes"></app-bar>
    </div>
  </div>
    <div class="row justify-content-center">
        <div class="col-6">
       <app-new :nbQuotes="nbQuotes" @new="createQuote" @alert="alert=true"></app-new>
        </div>
    </div>
    <div class="w-100"></div>
    <div class="row mb-3" id="quotesBox" >
        <template v-for="quote, index in quoteList">
            <app-quote :quote="quoteList[index]" @deleteQuote="deleteQuote(arguments)"></app-quote>
        </template>
    </div>
    <app-alert :alert="alert">
        <div slot="full" v-if="alert">The Quote box is full, please remove quote.</div>
        <div slot="info" v-else>Click on a quote to remove it.</div>
    </app-alert>
  </div>
</div>
</template>

<script>
import Bar from './components/Bar.vue';
import Quote from './components/Quote.vue';
import New from './components/New.vue';
import Alert from './components/Alert.vue';

export default {
    data: function() {
        return {
            currentId: 0,
            alert: false,
            nbQuotes: {
                max:8,
                now:0
            },
            quoteList:[]
        }
    },
    components: {
        appBar:Bar,
        appQuote:Quote,
        appNew:New,
        appAlert:Alert,
    },
    methods: {
        deleteQuote: function() {
            const id = arguments[0][0];
            this.nbQuotes.now--;
            this.quoteList = this.quoteList.filter( quote => {
                return quote.id !== id;
            });
            this.alert = false;
        },
        createQuote: function() {
            this.nbQuotes.now++;
            this.currentId++;
            const qData = arguments[0];
            const newQuote = {
                id:this.currentId, 
                title:qData.title, 
                text:qData.text,
                author:qData.author,
                source:qData.source
                };
            this.quoteList.push(newQuote);
        }
    }
}
</script>

<style>
</style>
