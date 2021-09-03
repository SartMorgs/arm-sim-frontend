<template>
	<div class="arm-on-off-table">
		<button class="arm-table-btn" v-on:click="hideTable = !hideTable">
        	{{ title }}
		</button>
		<table class="arm-table" v-if="!hideTable">
			<tbody>
			<tr v-for="field in data_memmory_fields" class="table-column">
				<th v-for="index in 4" class="table-item">{{ field.value[index] }}</th>
			</tr>
			<tr v-for="field of data_memmory_fields" class="table-column">
				<th  v-for="index in 4" class="table-item">{{ field.value[index] }}</th>
			</tr>
			<tr v-for="field of data_memmory_fields" class="table-column">
				<th v-for="index in 4" class="table-item">{{ field.value[index] }}</th>
			</tr>
			</tbody>
		</table>
	</div>
</template>	

<script>
	export default {
		data() {
			return {
				data_memmory_fields: [
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    },
                    {
                        name: "teste",
                        value: "BBxBB"
                    }
                ],
				hideTable: false
			}
		},
		props: ['title']
	}
</script>

<style>
	.arm-table-btn {
		background-color: #F5E68F;
		border: none;
		color: #756E44;
		padding: 15px 32px;
		text-align: center;
		text-decoration: none;
		display: inline-block;
		font-size: 16px;
	}

	.arm-on-off-table {
		padding: 2% 2% 2% 2%;
        display: flex;
        flex-direction: row;
	}

	.table-column {
		display: flex;
		flex-direction: row;
	}

	.table-item {
		justify-content: space-around;
		margin: 1px;
		width: 70%;
		color: #756E44;
		border: 1px solid #F5E68F;
		box-shadow: 1px 2px #888888;
	}

	.arm-table {
		font-family: arial, sans-serif;
		border-collapse: collapse;
		width: 100%;
	}
</style>