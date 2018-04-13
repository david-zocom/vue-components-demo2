<template>
	<div id="app">
		<h1>Welcome to Hackerbank, {{name}}</h1>
		<mitt-saldo
		 	v-bind:amount="monies"
			v-bind:name="name" />
		<gora-betalning
			v-on:send-payment="sendPayment"
			v-bind:kontosaldo="monies" />
		<p> {{paymentMessage}} </p>
	</div>
</template>

<script>
import Saldo from './Saldo.vue';
import Betalning from './Betalning.vue';
export default {
    name: 'app',
	components: {
		'mitt-saldo': Saldo,
		'gora-betalning': Betalning
	},
	data: function() {
		return {
			monies: 200000,
			name: 'Jonathan Hackerman',
			paymentMessage: ''
		}
	},
	methods: {
		sendPayment: function(obj) {
			/*{
				belopp: belopp,
				mottagareKonto: nr
			}*/
			// dra pengar
			this.monies -= obj.belopp;
			// informera användaren om att transaktion genomförts
			this.paymentMessage = `Du har skickat ${obj.belopp} kr till konto ${obj.mottagareKonto}.`;
		}
	}
}
</script>

<!-- CSS libraries -->
<style src="normalize.css/normalize.css"></style>

<!-- Global CSS -->
<style>
div {
	padding: 4px;
	margin: 4px;
}

  code {
    font-family: Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
    font-size: 0.9em;
    white-space: pre-wrap;
    color: #2c3e50;
  }

  code::before, code::after {
    content: '`';
  }
</style>

<!-- Scoped component css -->
<!-- It only affect current component -->
<style scoped>
  #app {
    background-color: #FF69B4;
    text-align: center;
    font-family: 'Comic Sans MS', 'Arial', sans-serif;
  }

  #app h1 {
    color: #fff;
    font-weight: 300;
    margin: 0;
  }

  .banner {
    height: 200px;
    background-color: #f6f6f6;
    padding: 50px 10px;
  }

  .bottom {
    padding: 80px 10px;
    font-size: 24px;
    font-weight: 300;
  }

  .fade {
    font-size: 14px;
  }

  .logo {
    animation: spin 4s 1s infinite linear
  }

  @keyframes spin {
    from {transform:rotate(0deg);}
    to {transform:rotate(360deg);}
  }
</style>
