<template>
<div>
    {{titre}}
    {{type}}
    {{prix}}
    {{contact}}
</div>
  
</template>

<script>
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
            type: String,
            required: true
        },
        contact: {
            type: String,
            required: true
        },
    }
}
</script>

<style>

</style>