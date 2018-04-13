<template>
	<div>
		<h3>Göra betalning</h3>
		Till vilket konto?
		<input v-model="kontonr" />
		<br />
		Hur mycket pengar?
		<input v-model="belopp" />
		<br />
		Skicka {{belopp}} kr till konto {{kontonr}}?
		<br />
		<button v-on:click="sendPayment">Ja!</button>
	</div>
</template>

<script>
export default {
	props: ['kontosaldo'],
	data: function() {
		return {
			kontonr: '1337',
			belopp: 0
		}
	},
	methods: {
		sendPayment: function(event) {
			// Kontrollera att betalningen är ok
			// Kontonummer ska vara vanliga tal
			let nr = Number(this.kontonr);
			let belopp = Number(this.belopp);
			let fail = false;
			if( isNaN(nr) || nr <= 0 ) fail = true;
			if( isNaN(belopp) || belopp <= 0 ) fail = true;
			if( belopp > this.kontosaldo ) fail = true;
			if( fail ) {
				// visa felmeddelande och avbryt
				return;
			}
			this.$emit('send-payment', {
				belopp: belopp,
				mottagareKonto: nr
			});
		}
	}
};
</script>

<style scoped>
div {
	background-color: powderblue;
}
</style>
