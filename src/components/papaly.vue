<template>
	<div id="papa">
		<div id="inputs">
			<h3>Ajouter un lien</h3>
			<input placeholder="Lien du site" type="text" v-model="link">
			<input placeholder="Nom de votre lien" type="text" v-model="linkname">
			<select name="" v-model="categorychoose">
				<option disabled value="">Aucune</option>
				<option v-for="link in category" :value="link">{{link}}</option>
			</select>
			<button @click="add">Ajouter un lien</button><br>
			<h3>Ajouter une catégorie</h3>
			<input placeholder="Nom de votre catégorie" type="text" v-model="categoryAdd">
			<button @click="create">Ajouter votre catégorie</button>
		</div>
		<div v-for="cat in category" :id="cat">
			<h2>{{cat}}</h2>
			<div v-for="link,index in prepareDom[cat]">
				<a  :href="link[0]" target="_blank">{{link[1]}}
					<br></a>
					<button v-model="index" :value="index" @click="supp(cat,index)">Supprimer ce lien</button>
				</div>
			</div>
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
					if(this.categorychoose==''){
						alert('Vous n\'avez pas choisi de catégories, veuillez en choisir une ou la créer')
					}
					if(!this.prepareDom[this.categorychoose]){
						this.prepareDom[this.categorychoose]=[[this.link,this.linkname]]
						this.link=''
						this.linkname=''
					}else{
						this.prepareDom[this.categorychoose].push([this.link,this.linkname])
						this.link=''
						this.linkname=''
					}
				},
				supp: function(cat,index){
					this.prepareDom[cat].splice(index,1)
					this.linkname=' '
					this.linkname=''
				}
			}
		}
	</script>