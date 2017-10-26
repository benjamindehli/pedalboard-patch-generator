<template>
	<div id="app">
		<main-navigation></main-navigation>
		<main id="mainContent">
			<div class="main-content">
				<div class="box">
					<div class="content">
						<h1>Pedalboard Patch Generator</h1>
						<div class="row">
							<effect-item v-for="(effect, effectIndex) in effects" v-bind:effect-index="effectIndex" v-bind:effect="effect" v-bind:effects="effects" class="col-xs-12 col-sm-6 col-md-4">
							</effect-item>
							<div class="clearfix"></div>
						</div>
					</div>
				</div>				
				
			</div>
			<main-footer></main-footer> 
		</main>
	</div>
</template>

<script>
import * as quark from 'quark-gui';
import MainNavigation from './MainNavigation.vue';
import MainFooter from './MainFooter.vue';
import EffectItem from './EffectItem.vue';

function loadJSON(callback, path) {
	var xobj = new XMLHttpRequest();
	xobj.overrideMimeType("application/json");
	xobj.open('GET', path, false);
	xobj.onreadystatechange = function () {
		if (xobj.readyState == 4 && xobj.status == "200") {
			callback(xobj.responseText);
		}
	};
	xobj.send(null);
	return JSON.parse(xobj.responseText);
}

function getJsonFile(path) {
	var response = loadJSON(function (response) {
		var jsonResponse = JSON.parse(response);
	}, path);
	return response;
}



export default {
	name: 'app',
	components: {
		mainNavigation: MainNavigation,
		mainFooter: MainFooter,
		effectItem: EffectItem
	},
	data: function () {
		return {
			selectedEffects: [
			{
				"id": "electro-harmonix-deluxe-memory-man",
				"name": "Electro-Harmonix Deluxe Memory Man"
			},
			{
				"id": "origin-effects-cali76",
				"name": "Origin Effects Cali 76"
			},
			{
				"id": "diamond-memory-lane-2",
				"name": "Diamond Memory Lane 2"
			}
			],
		};
	},
	methods: {
		getJsonData: function (path) {
			var jsonData = loadJSON(function (response) {
				var jsonResponse = JSON.parse(response);
			}, path);
			return jsonData;
		}
	},
	computed: {
		effects: function(){
			var effects = [];
			this.selectedEffects.forEach(function(selectedEffect){
				effects.push(this.getJsonData("src/json/effects/" + selectedEffect.id + ".json"));
			}.bind(this));
			return effects;
		}
	}
}
</script>

<style>

</style>
