<template>
	<div class="arm-menu">
		<ul class="menu-botoes">
			<li v-for="icone of icones" class="menu-botoes-item">
				<input v-on:click="icone.action" type="image" :alt="icone.titulo" :src="icone.url" class="botao" />
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		methods: {
			compile() {
				let formData = new FormData()
				formData.append('code', "testetesdsaaçsl")

				this.$http.post("http://localhost:5000/api/v1/code",)
					.then(res => res.json())
					.then(result => console.log(result), err => console.log(err))
			}
		},
		data() {
			return {
				icones: [
					/*
					{
						url: "src/assets/icons/save-button.svg",
						titulo: "save",
						action: ""
					},
					{
						url: "src/assets/icons/open-button.svg",
						titulo: "open",
						action: ""
					},
					*/
					{
						url: "src/assets/icons/compile-button.svg",
						titulo: "compile",
						action: "compile()"
					},
					{
						url: "src/assets/icons/play-button.svg",
						titulo: "play",
						action: ""
					},
					{
						url: "src/assets/icons/pause-button.svg",
						titulo: "pause",
						action: ""
					},
					{
						url: "src/assets/icons/next-button.svg",
						titulo: "next",
						action: ""
					},
					{
						url: "src/assets/icons/stop-button.svg",
						titulo: "stop",
						action: ""
					},
				],
			}
		},

		props: [
			"code"
		],
	}
</script>

<style lang="scss">
	.arm-menu {
		width: 96%;
		margin: 0 auto;
		padding: 0 auto;
	}

	.menu-botoes {
		list-style: none;
	}

	.menu-botoes .menu-botoes-item {
		display: inline-block;
		margin-left: 5%;
	}

	.menu-botoes .menu-botoes-item .botao {
		width: 100%;
		max-height: 50px;
		max-width: 50px;
		border: 2px solid black;
		padding: 5px;
		background-color: #F5E68F;
	}
</style>