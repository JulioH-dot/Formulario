<template>
    <div>
        <i :class="estrela.estilo" 
            v-for="estrela in estrelas" 
            :key="estrela.id" 
            @click="avaliacao(estrela.id)">
        </i>
       
    </div>
</template>

<script>
export default {
    name: 'InputEstrelas',
    data:()=>({
        estrelas:[],
        avaliacao1: 0
    }),
    props:{
        numeroEstrelas:{
            type: Number,
            required: true,

        }
    },
    created(){
        this.iniciarEstrelas()
    },
    methods:{
        iniciarEstrelas(){

            for(let i =0; i < this.numeroEstrelas; i++){
          
                this.estrelas[i] = {
                    id: i,
                    estilo: 'bi-star estrela'
                }
            }
        },
        avaliacao(qtd){

            this.iniciarEstrelas()

            this.avaliacao1 = qtd+1

            for (let i =0; i < this.avaliacao1; i++){
                this.estrelas[i].estilo = 'bi-star-fill estrela preenchida'
            }

            this.$emit('avaliar', this.avaliacao1)

        }
    }
}
</script>



<style>
.estrela{
    font-size: 1.5rem;
    color: #999;
    margin-left: 1px;
    margin-right: 1px;
}
.preenchida{
    color: #fc0
}
</style>