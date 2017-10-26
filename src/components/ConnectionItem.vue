<template>
	<div>
		<select v-model="selectedConnection" v-on:change="makeConnection">
			<optgroup v-for="effectConnection in availableEffectConnections" v-bind:label="effectConnection.effectName">
				<option v-for="connection in effectConnection.connections" v-bind:value="connection">{{ connection.connectionName }}</option>
			</optgroup>
		</select>
		<label>
			{{ connection.name }}
		</label>
	</div>
</template>

<script>
export default {
	name: 'ConnectionItem',
	props: ['effectIndex', 'connectionIndex', 'connection', 'ioType', 'effects'],
	data: function () {
		return {
			selectedConnection: {
				connectionIndex: "",
				connectionName: "",
				effectIndex: ""
			}
		};
	},
	computed: {
		availableEffectConnections: function(){
			var availableEffectConnections = [];
			this.effects.forEach(function(effect, effectIndex){
				availableEffectConnections[effectIndex] = {'effectName': effect.brand + ' ' + effect.model, 'connections': []};
				var connectionArray = this.ioType == 'input' ? effect.outputs : effect.inputs;
				connectionArray.forEach(function(connection, connectionIndex){
					availableEffectConnections[effectIndex].connections.push({'effectIndex': effectIndex, 'connectionIndex': connectionIndex, 'connectionName': connection.name});
				});
			}.bind(this));
			return availableEffectConnections;
		}
	},
	methods: {
		makeConnection: function(){
			console.log(this.selectedConnection);
			console.log(this.connection);
			var effectIndex = this.selectedConnection.effectIndex;
			var connectionIndex = this.selectedConnection.connectionIndex;
			var connectionName = this.selectedConnection.connectionName;
			var effectConnections = this.$root.$children[effectIndex].$children;
			effectConnections.forEach(function(effectConnection){
				if (effectConnection.connection.name == connectionName){
					effectConnection.selectedConnection.connectionIndex = this.connectionIndex;
					effectConnection.selectedConnection.connectionName = this.connection.name;
					effectConnection.selectedConnection.effectIndex = this.effectIndex;
					/*effectConnection.selectedConnection = {
						connectionIndex: this.connectionIndex,
						connectionName: this.connection.name,
						effectIndex: this.effectIndex
					}*/
				}
			}.bind(this))
			//console.log(effectConnections);

		}
	}
}
</script>
