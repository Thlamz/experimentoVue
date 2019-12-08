<template>
    <ul>
        <li v-for="unidade in parsedNames" :key="unidade.id">
            {{unidade}}
        </li>
    </ul>
</template>

<script>
import axios from 'axios'
export default {
    data: function(){
        return {
            unidades: [],
            loading: false,
        }
    },
    rules:
    {
        "no-console": "off"
    },
    methods: {
        getAllUnidades() {
            axios.get("http://localhost:9000/unidadeOp/")
            .then((response) => {
            this.unidades = response.data;
      })
      .catch((err) => {
       this.loading = false;
       throw new Error(err);
      })
        }
    },
    mounted: function(){
        this.getAllUnidades();
    },
    computed: {
        parsedNames() {
            let names = [];
            this.unidades.forEach(element => {
                names.push(element.nome + " ID:" + element.id);
            });
            return names;
        }
    }
    
}
</script>