<template>
    <div id="app">
        <app-header
            :quotesNumber="quotes.length"
            ></app-header>
        <app-quote-form
            @quoteWasAdded="quotes.push($event)"
            :quotesNumber="quotes.length"
            ></app-quote-form>
        <div id="quote-cards">
            <app-quote-card
            v-for="(quote, index) in quotes" :quote="quote"
            :quoteId="index"
            @cardWasClicked="quotes.splice($event, 1)"
            ><p>{{ quote }}</p></app-quote-card>
        </div>
        <app-footer></app-footer>
    </div>
</template>

<script>
    import Header from './components/Header.vue'
    import QuoteForm from './components/QuoteForm.vue'
    import QuoteCard from './components/QuoteCard.vue'
    import Footer from './components/Footer.vue'


    export default {
        data () {
            return {
                quotes: []
            }
        },
        components: {
            appHeader: Header,
            appQuoteForm: QuoteForm,
            appQuoteCard: QuoteCard,
            appFooter: Footer
        }
    }

</script>

<style lang="scss">
    #app {
        margin: 0 10%;
    }
    #quote-cards {
        margin-top: 20px;
    }
</style>
