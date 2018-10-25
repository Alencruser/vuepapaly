<template>
	<div id="papa">
		<div id="inputs">
			<h3>Ajouter un lien</h3>
			<input type="text" v-model="link">
			<input type="text" v-model="linkname">
			<select name="">
				<option v-for="link in categorylist" :value="link">{{link}}</option>
			</select>
			<button>Ajouter un lien</button><br>
			<h3>Ajouter une catégorie</h3>
			<input type="text" v-model="categoryAdd">
			<button @click="create">Ajouter votre catégorie</button>
		</div>
		<div v-for="cat in categorylist" :id="cat"></div>
	</div>
</template>
<script>
	export default {
		name:"papaly",
		data:function(){
			return {
				category:[],
				categoryAdd:'',
				link:'',
				linkname:'',
				categorylist:[]
			}
		},
		methods: {
			create: function(){
				if(!this.category.includes(this.categoryAdd)){
					console.log('ajout de la category')
					this.category.push(this.categoryAdd)
					this.categorylist.push(this.categoryAdd)
				}else{
					alert('cette catégorie existe déjà robert')
				}
			}
		}
	}
</script>