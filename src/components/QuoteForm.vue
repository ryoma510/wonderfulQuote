<template>
    <div id="quote-form">
        <h3>Quote</h3>
        <textarea rows="3" v-model="inputQuote"></textarea>
        <button @click="addQuote">Add Quote</button>
    </div>
</template>

<script>
    export default {
        props: ['quotesNumber'],
        data () {
            return {
                inputQuote: ''
            }
        },
        methods: {
            addQuote () {
                if (this.inputQuote !== '') {
                    if (this.quotesNumber < 10) {
                        this.$emit('quoteWasAdded', this.inputQuote)
                        this.inputQuote = ''
                    } else {
                        alert('Quotes was already added over 10. Please delete some quotes with cliclking')
                    }
                } else {
                    alert('Pleade tyoe wonderful quote!')
                }
            }
        }
    }
</script>

<style scoped lang="scss">
    #quote-form {
        width: 60%;
        margin: 0 auto;
        text-align: center;
        textarea {
            width: 100%;
            font-size: 24px;
        }
    }
    button {
        font-size: 20px;
        margin-top: 10px;
        position: relative;
        display: inline-block;
        padding: 0.25em 0.5em;
        text-decoration: none;
        color: #FFF;
        background: #03A9F4;/*色*/
        border: solid 1px #0f9ada;/*線色*/
        border-radius: 4px;
        box-shadow: inset 0 1px 0 rgba(255,255,255,0.2);
        text-shadow: 0 1px 0 rgba(0,0,0,0.2);
        cursor: pointer;
        &:active {
            border: solid 1px #03A9F4;
            box-shadow: none;
            text-shadow: none;
        }
    }
</style>
