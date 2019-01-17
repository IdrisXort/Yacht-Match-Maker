<template>
	<div class="col-12 col-md-4 match__container">
		<div class="match__block">
			<div class="match">
				<img src="#" alt="company" class="match__background">
				<!-- results should always be showed now it goes trough the list till there is nothing,
				 this happens everytime the html is change  -->
				<h1>{{Math.round(parseInt(matchPercentage)/11*100)+'%'}}</h1>
				<h5>{{companyName}}</h5>
			</div>
		</div>
	</div>
</template>

<script>
export default {
  props: ["companyName", "matchPercentage"]
};
</script>

<style scoped>
	.match__container {
		margin-bottom: 20px;
	}
	.match__block {
		width: 100%;
		min-height: 150px;
		color: #192a56;
		border: 2px solid #192a56;
		border-radius: 10px;
		text-align: center;
		background-color:white;
		display: flex;
  	align-items: center;
		justify-content: center;
	}

	.match__background {
		-webkit-filter: blur(2px);
  	-moz-filter: blur(2px);
  	-o-filter: blur(2px);
  	-ms-filter: blur(2px);
  	filter: blur(2px); 
	}
	.match {
		margin: 0 auto;
 
	}
</style>
