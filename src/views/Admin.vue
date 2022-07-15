<template>
	<div><h1>LJMA GAMES</h1></div>
	<div>
		<table>
			<thead>
				<tr>
					<th scope="col"></th>
					<th scope="col">Title</th>
					<th scope="col">Category</th>
					<th scope="col">description</th>
					<th scope="col">Company</th>
					<th scope="col">Price</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="product of products" :key="product.id">
					<td scope="row"><img v-bind:src="product.image" alt="" /></td>
					<td>{{ product.title }}</td>
					<td>{{ product.category }}</td>
					<td>{{ product.description }}</td>
					<td>{{ product.company }}</td>
					<td>{{ product.price }}</td>
					<td><button @click="deleteProduct(product.id)">Delete</button></td>
					<td><UpdateModal :product="product" /></td>
				</tr>
			</tbody>
		</table>
	</div>
</template>
<script>
	import UpdateModal from "../components/UpdateModal.vue";
	export default {
		components: {
			UpdateModal,
		},

		mounted() {
			this.$store.dispatch("ShowProducts");
		},
		computed: {
			products() {
				return this.$store.state.products;
			},
		},
		methods: {
			deleteProduct(id) {
				return this.$store.dispatch("deleteProduct", id);
			},
		},
	};
</script>
<style scoped>
	h1 {
		background: -webkit-linear-gradient(rgb(5, 202, 156), rgb(184, 14, 184));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
			sans-serif;
		display: flex;
		letter-spacing: 20px;
		justify-content: center;
		border-color: black;
		border-width: 10px;
		font-size: 50px;
		color: white;
		text-shadow: 3px 3px 15px black;
	}
	th {
		background: -webkit-linear-gradient(rgb(5, 202, 156), rgb(184, 14, 184));
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS",
			sans-serif;
		font-size: 20px;
		color: white;
		text-shadow: 3px 3px 15px black;
	}
	td {
		border: 2px solid white;
		width: auto;
		font-weight: bold;
	}

	@keyframes gloski {
		0% {
			box-shadow: -5px -5px 30px 5px crimson, 5px 5px 30px 5px blue;
		}
		50% {
			box-shadow: 5px 5px 30px 5px yellow, -5px -5px 30px 5px purple;
		}
		100% {
			box-shadow: -5px -5px 30px 5px red, 5px 5px 30px 5px blue;
		}
	}

	@media only screen and (max-width: 760px),
		(min-device-width: 768px) and (max-device-width: 1024px) {
		/* Force table to not be like tables anymore */
		table,
		thead,
		tbody,
		th,
		td,
		tr {
			display: flex;
			flex-direction: column;
			flex-wrap: wrap;
			justify-content: center;
			align-content: center;
		}
		th {
			padding-bottom: 10%;
		}
		tbody {
			display: flex;
			flex-direction: column;
			flex-wrap: wrap;
			justify-content: center;
			align-items: center;
		}
		/* Hide table headers (but not display: none;, for accessibility) */
		thead tr {
			display: none;
		}

		td {
			width: 30%;
		}
	}
	img {
		width: 10vw;
		height: 15vh;
	}
</style>
