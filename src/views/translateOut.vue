<template>
  <div class="translateOut" >
  	<h1>{{translatedWords}}</h1>
  </div>
</template>

<script>
export default {
  name: 'translateOut',
  props: ["translatedWords"]
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.translateOut{
	text-align: center;
	margin:10px auto;
}
</style>
