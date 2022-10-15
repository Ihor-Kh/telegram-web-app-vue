<template>
	<div id="app">
		<h1>Тест приложения VUE в telegram bot</h1>
		<br>
		<div>
			<div>Типа имя <span>{{tg.initDataUnsafe?.user?.username}}</span></div>
			<button @click="tgClose" class="btn-tg">Закрыть</button>
		</div>


	</div>
</template>

<script>

export default {
	data(){
		return {
			tg: window.Telegram.WebApp
		}
	},
	methods: {
		tgClose(){
			this.tg.close()
		}
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
}

.btn-tg {
	padding: 10px 15px;
	background: var(--tg-theme-button-color);
	color: var(--tg-theme-button-text-color);
	border: none;
	outline: none;
	cursor: pointer;
}

nav {
	padding: 30px;
}

nav a {
	font-weight: bold;
	color: #2c3e50;
}

nav a.router-link-exact-active {
	color: #42b983;
}
</style>
