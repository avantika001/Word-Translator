<template>
<div class="row">
  <div class="col s6 offset-s3">
  <div id="app" class="center card-panel blue-grey darken-1">
  <div col s6 offset-s3 valign>
    <h1>Word Translator</h1>
    <h5 class="white-text">@Powered by Vue.js</h5>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
  </div>
  </div>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput';
export default {
  name: 'App',
  components: {
    TranslateForm,
    TranslateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods: {
    translateText:function(text,language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190117T061254Z.61a905e3e9b924a7.6b0e743b10423aafb5f573e2b26b6b5ab2ace9f9&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText=response.body.text[0];
        });
    }
  }
}
</script>
<style>
body{
background:Orange;
}
.card-panel{
margin-top:160px;
margin-bottom:140px;
}
</style>
