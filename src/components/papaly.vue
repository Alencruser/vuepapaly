<template>
	<div id="papa">
		<div id="inputs">
			<h3>Ajouter un lien</h3>
			<input type="text" v-model="link">
			<input type="text" v-model="linkname">
			<select name="" v-model="categorychoose">
				<option disabled value="">Aucune</option>
				<option v-for="link in category" :value="link">{{link}}</option>
			</select>
			<button @click="add">Ajouter un lien</button><br>
			<h3>Ajouter une catégorie</h3>
			<input type="text" v-model="categoryAdd">
			<button @click="create">Ajouter votre catégorie</button>
		</div>
		<div v-for="cat in category" :id="cat"><h2>{{cat}}</h2><a v-for="link in prepareDom[cat]" :href="link[0]" target="_blank">{{link[1]}}<br></a></div>
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
				prepareDom:{},
				categorychoose:''
			}
		},
		methods: {
			create: function(){
				if(!this.category.includes(this.categoryAdd)){
					this.category.push(this.categoryAdd)
					this.categoryAdd=''
				}else{
					this.categoryAdd=''
					alert('Cette catégorie existe déjà robert')
				}
			},
			add: function(){
				if(!this.prepareDom[this.categorychoose]){
				this.prepareDom[this.categorychoose]=[[this.link,this.linkname]]
				this.link=''
				this.linkname=''
			}else{
				this.prepareDom[this.categorychoose].push([this.link,this.linkname])
				this.link=''
				this.linkname=''
			}
			}
		}
	}
</script>