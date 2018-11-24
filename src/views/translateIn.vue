<template>
	<div class="translateIn row">
	  	<form v-on:submit='getwords'  class="form-inline col-md-6 col-md-offset-3" role="form">
	  		<div class="form-group">
	  			<input type="text" name="" placeholder="请输入要翻译的内容" v-model='words' class ="form-control">
			  	<select v-model='lang' class ="form-control">
			  		<option value="en">English</option>
			  		<option value="ko">Korean</option>
			  		<option value="ja">Japanese</option>
			  		<option value="fr">French</option>
			  	</select>
			  	<input type="submit" name="" value="翻译" class="btn btn-success">
	  		</div>	  		
	  	</form>
  	</div>
</template>

<script>
export default {
  name: 'translateIn',
  data(){
  	return {
  		words:'',
  		lang:''
  	}
  },
  methods:{
  	getwords:function(e){
  		this.$emit('translateInText',this.words,this.lang);
  		e.preventDefault();
  	},

  },
  created:function(){
  	this.lang='en';
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form{
	background-color: #ccc;
	border:1px solid #ccc;
	border-radius: 5px;
	text-align: center;
}
</style>
