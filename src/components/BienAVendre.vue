<template>
<div>
    {{titre}}
    {{type}}
    {{prix}}
    {{contact}}
    <input type="checkbox" :checked="vendu" v-on:change="miseAJour">
</div>
  
</template>

<script>
import axios from 'axios'
export default {
    name: 'BienAVendre',
    //props: ['titre', 'type', 'prix', 'contact']
    props:{
        titre: {
            type: String,
            required: true
        },
        type: {
            type: String,
            required: true
        },
        prix: {
            type: Number,
            required: true
        },
        contact: {
            type: String,
            required: true
        },
        vendu:{
            type: Boolean,
            required: true
        },
        id:{
            type: Number,
            required: true
        },
    },
    methods:{
        miseAJour(){
            axios.put(`http://localhost:3000/biens/${this.id}`, {
                "titre": this.titre,
                "type": this.type,
                "prix": this.prix,
                "contact": this.contact,
                "vendu": !this.vendu
            })
            this.$emit('mise-a-jour', {
                vendu: !this.vendu
            })
        }
    }
}
</script>

<style>

</style>