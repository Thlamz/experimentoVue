<template>
    <div>
    <ListItems :unidades="unidades" @selected="selectedID=$event"></ListItems>
    <h4> 
        ID Selecionado: {{selectedID || "Nenhum"}}
    </h4>
    </div>
</template>

<script>
import axios from 'axios'
import ListItemsVue from './ListItems.vue';
export default {
    data: function(){
        return {
            unidades: [],
            loading: false,
            selectedID: 0,
        }
    },
    rules:
    {
        "no-console": "off"
    },
    components: {
        'ListItems': ListItemsVue,
    },
    methods: {
        getAllUnidades() {
            axios.get("http://localhost:8000/unidadeOp/")
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