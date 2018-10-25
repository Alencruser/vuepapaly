<template>
	<div id="papa">
		<div id="inputs">
			<h3>Ajouter un lien</h3>
			<input type="text" v-model="link">
			<input type="text" v-model="linkname">
			<select name="" v-model="categorychoose">
				<option disabled value="">Status</option>
				<option v-for="link in category" :value="link">{{link}}</option>
			</select>
			<button @click="add">Ajouter un lien</button><br>
			<h3>Ajouter une catégorie</h3>
			<input type="text" v-model="categoryAdd">
			<button @click="create">Ajouter votre catégorie</button>
		</div>
		<div v-for="cat in category" :id="cat"><p v-for="link in prepareDom.cat">{{link}}</p></div>
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
				categorylist:[],
				prepareDom:{},
				categorychoose:''
			}
		},
		methods: {
			create: function(){
				if(!this.category.includes(this.categoryAdd)){
					this.category.push(this.categoryAdd)
				}else{
					alert('Cette catégorie existe déjà robert')
				}
			},
			add: function(){
				if(!this.prepareDom[this.categorychoose]){
				this.prepareDom[this.categorychoose]=[this.link]
			}else{
				this.prepareDom[this.categorychoose].push(this.link)
			}
			}
		}
	}
</script>