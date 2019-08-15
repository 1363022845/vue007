<template>
	<div> 
		<input type="text" id="username" name="username"/>
		<input type="file" name="file"/>
		<input type="button" class="btn btn-default" v-on:click="upload" value="上传"/>
	</div>
</template>

<script>
	export default {
		name:'EmpUpload',
		methods:{
			upload:function(){
				var formdata = new FormData();
				formdata.append("file",document.querySelector('input[name=file]').files[0]);
				formdata.append("username",document.getElementById("username").value);
				
				var config = {
					headers:{
						"Content-type":"multipart/form-data"
					}
				};
				this.$http.post("http://localhost:8081/upload",formdata,config).then(
					function(result){
						alert(result.bodyText);
					},
					function(error){
						alert(error.body.message);
					}
				)
			}
		}
	}
	
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>