<template class="container">
  <div id="app" class="row">
    <h1>在线翻译</h1>
    <h5>简单 / 易用 / 便捷</h5>
    <translateIn v-on:translateInText='translateIntext' class='col-xs-'></translateIn>
    <translateOut v-text='translatedWords'></translateOut>
  </div>
</template>


<!-- 第一步：首先要拿到表单里面的数据，并且传递到父组件，传递给翻译软件api（由子组件传给父组件$emit） -->
<!-- 第一步：获得已经翻译好的数据传递给translateOut（由父组件传给子组件props）-->

<script>
import translateIn from './views/translateIn.vue'
import translateOut from './views/translateOut.vue'

export default {
  name: 'app',
  data(){
    return {
      translatedWords:''
    }
  },
  components: {
    translateIn,translateOut
  },
  methods:{
    translateIntext:function(text,lang){
      //console.log(text); //words就是从translateIn.vue拿过来的words
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20181124T113905Z.654dff765f849379.027c5573c11c29ea2ebffd410490dc642e9fc164&lang='+lang+'&text='+text)
          .then(function(response){
            //console.log(response.body.text[0]);
            this.translatedWords=response.body.text[0]
          })
    }
  }
}
</script>

<style>
h1,h5{
  text-align: center;
}

</style>
