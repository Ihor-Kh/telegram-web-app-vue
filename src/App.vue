<template>
	<div id="app">
		<div>
			<div>Типа имя <span>{{user?.username}}</span></div>
			<button @click="tgClose" class="btn-tg">Закрыть</button>
		</div>
		<h1>Тест приложения VUE в telegram bot</h1>

	</div>
</template>

<script>

import {useTelegram} from '@/hooks/useTelegram'
export default {
	name: "test",
	data(){
		return {
			tg: useTelegram.tg,
		}
	},
	methods: {
		tgClose(){
			this.useTelegram.onClose()
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
