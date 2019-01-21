<template>
  <div class="container">
		<div class="row">
			<div class="col-12">
				<label class="intro__Label">Bedankt voor het invullen van de formulier!</label>
				<p class="intro__text">
					Hieronder zie je de top 3 bedrijven die het
					meest matchen met wat jij van een bedrijf verwacht. Wil je weten welke bedrijven dat
					zijn en wat voor een persoon je bent? De Yacht recruiter zal het in alle detail uitleggen
					tijdens jullie introductiegesprek. Hij/zij zal jou binnenkort contacteren.
				</p>
			</div>
		</div>
		<div class="row">
			<Match 
			v-for="(result,index) in results.sort(function(res1,res2){return res2.totalMatch-res1.totalMatch}).splice(0,3)"
			:key="index"
			:companyName="result.companyName"
			:matchPercentage="result.totalMatch"
			/>
		</div>
  </div>
</template>

<script>
import Match from "../../Components/Match/Match";
export default {
  components: {
    Match: Match
  },
  props:['results']
};
</script>

<style scoped>
	.intro__Label{
		font-size:20px;
	}
	.intro__text {
		font-size:20px;
		color:#57606f;
	}
</style>
