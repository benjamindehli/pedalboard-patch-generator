<template>
	<div>
		<div class="box primary z-1">
			<div class="box-header">
				<div class="content">
					<h3 class="box-title">{{ effect.brand }}<br/> <small>{{ effect.model }}</small></h3>
				</div>
			</div>
			<div class="content">
				<p>Inputs</p>
				<div v-for="(input, connectionIndex) in effect.inputs">
					<div class="input-group">
						<div is="connection-item" v-bind:effect-index="effectIndex" v-bind:connection-index="connectionIndex" v-bind:connection="input" v-bind:io-type="'input'" v-bind:effects="effects"></div>
					</div>
				</div>
				<p>Outputs</p>
				<div v-for="(output, connectionIndex) in effect.outputs">
					<div class="input-group">
						<div is="connection-item" v-bind:effect-index="effectIndex" v-bind:connection-index="connectionIndex" v-bind:connection="output" v-bind:io-type="'output'" v-bind:effects="effects"></div>
					</div>
				</div>
				<div v-if="effect.parameters.switches">
					<p>Switches</p>
					<div v-for="dial in effect.parameters.switches">
						<div class="input-group">
							<select>
								<option v-for="option in dial.options">{{ option }}</option>
							</select>
							<label>{{ dial.name }}</label>
						</div>
					</div>
				</div>
				<p>Potentiometers</p>
				<div v-for="potentiometer in effect.parameters.potentiometers">
					<div class="input-group">
						<input type="range" min="0" max="100" /><label>{{ potentiometer.name }}</label>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import ConnectionItem from './ConnectionItem.vue';

export default {
	name: 'EffectItem',
	props: ['effectIndex', 'effect', 'effects'],
	components: {
		connectionItem: ConnectionItem
	},
	data: function () {
		return {
			
		};
	},
	methods: {
	}
}
</script>
