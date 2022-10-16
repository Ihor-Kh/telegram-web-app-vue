<template>
	<div id="app">
		<h1>Тест приложения VUE в telegram bot</h1>
		<br>
		<div>
			<div>Типа имя <span>{{tg.initDataUnsafe?.user?.username}}</span></div>
			<button @click="tgClose" class="btn-tg">Закрыть</button>
		</div>
		<div>
			<input v-model="text1" type="text" placeholder="Напиши тут что-то">
			<input v-model="text2" type="text" placeholder="И тут тоже">
		</div>
		<div>{{test}}</div>
		<br>
		<br>
		<div>Проверке валидации</div>
		<div>{{ useTgButton ? 'Валидация поройдена' : 'Заполните поля'}}</div>

	</div>
</template>

<script>

export default {
	data(){
		return {
			tg: window.Telegram.WebApp,
			text1: '',
			text2: '',
			//useTgButton: this.text1 == true && this.text2 == true,
			test: ''
		}
	},
	methods: {
		tgClose(){
			this.tg.close()
		},
		sendformTgInput(){
			this.test = 'Главная кнопка нажата!'
		}
	},
	mounted() {
		this.tg.MainButton.setParams({
			text: 'Отправить данные!'
		})

		Telegram.WebApp.onEvent('mainButtonClicked', this.sendformTgInput)
	},
	watch: {
		useTgButton(val){
			if(val === true) {
				this.tg.MainButton.show()
			} else {
				this.tg.MainButton.hide()
			}
		}
	},
	computed: {
		useTgButton(){
			return  this.text1 != '' && this.text2 != ''
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
