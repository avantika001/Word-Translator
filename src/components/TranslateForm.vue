<template>
  <div id="translateForm" class="row">
    <form v-on:submit="formSubmit" class="col s12">
      <div class="row">
      <div class="input-field col s6 offset-s3">
      <textarea class="materialize-textarea center" type="text" v-model="textToTranslate" placeholder="enter a word" />
      <div class="input-field col s12">
      <select v-model="language" class="browser-default">
        <option value="ru">Russian</option>
        <option value="zh">Chinese</option>
        <option value="fr">French</option>
        <option value="es">Spanish</option>
        <option value="en">English</option>
        <option value="kn">Kannada</option>
      </select>
      </div>
      <input  type="submit" class="btn red" value="Translate">
      </div></div>
    </form>

  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data(){
    return {
      textToTranslate:'',
      language:''
    }
  },
  created(){
    this.language='ru';
  },
  methods: {
    formSubmit(e){
      this.$emit('formSubmit',this.textToTranslate,this.language);
      e.preventDefault();
      }
    }
}
</script>

<style>

</style>
