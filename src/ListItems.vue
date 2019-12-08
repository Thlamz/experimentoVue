<template>
    <ul>
        <li v-for="unidade in unidades" :key="unidade.id" @click="$emit('selected',unidade.id)">
            {{unidade.nome}} ID: {{unidade.id}}
        </li>
    </ul>
</template>

<script>

export default {
    data: function(){
        return {
        }
    },
    props: {
        unidades: Array,
    }
    ,
    rules:
    {
        "no-console": "off"
    },
    methods: {
        //passSelectedUnidade(id) {
        //    $emit('selected',id);
        //}
    }, 
}
</script>