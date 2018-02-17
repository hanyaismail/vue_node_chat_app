<template>
	<div>
		<p v-if="isConnected">We're connected to the server</p>
		<p v-else>We're not connected to the server</p>
		<p>Message from the server: {{socketMessage}}</p>
		<button @click="pingServer">Ping Server</button>
	</div>
</template>

<script>
export default {
	data () {
		return {
			isConnected: false,
			socketMessage: ''
		}
	},

	sockets: {
		connect() {
			this.isConnected = true
		},

		disconnect() {
			this.isConnected = false
		},

		messageChannel(data) {
			this.socketMessage = data
		}
	},

	methods: {
		pingServer: function() {
			this.$socket.emit('pingServer', 'ping')
		}
	}
}
</script>

<style>
	
</style>