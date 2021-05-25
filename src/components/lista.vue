<template>
  <div class="container-fluid p-5" id="listaNomes">
    <div class="container">
      <div class="row">
        <div class="col-md mt-3">
          <h5>Prefixos <span class="badge bg-info">{{prefixos.length}}</span></h5>
          <div class="card">
            <div class="card-body">
                <ul class="list-group">
                    <li
                    class="list-group-item"
                    v-for="prefix in prefixos"
                    :key="prefix"
                    >
                    <div class="row">
                        <div class="col-md col">
                            {{ prefix }}
                        </div>
                        <div class="col-md col">
                            <button class="btn btn-info text-white" style="float: right" @click="deletePrefix(prefix)">
                                <span class="fa fa-trash"></span>
                            </button>
                        </div>
                    </div>
                    </li>
                </ul>
                <br>
                <div class="input-group">
                    <input type="text" placeholder="Digite o prefixo" class="form-control" v-model="prefix" @keyup.enter="addPrefix(prefix)">
                    <div class="input-group-append">
                        <button type="button" class="btn btn-info text-white" v-on:click="addPrefix(prefix)">
                            <span class="fa fa-plus"></span>
                        </button>
                    </div>
                </div>
            </div>
          </div>
        </div>
        <div class="col-md mt-3">
          <h5>Sufixos <span class="badge bg-info">{{sufixos.length}}</span></h5>
          <div class="card">
            <div class="card-body">
                <ul class="list-group">
                    <li
                    class="list-group-item"
                    v-for="sufix in sufixos"
                    :key="sufix"
                    >
                        <div class="row">
                            <div class="col-md col">
                                {{ sufix }}
                            </div>
                            <div class="col-md col">
                                <button class="btn btn-info text-white" style="float: right" @click="deleteSufix(sufix)">
                                    <span class="fa fa-trash"></span>
                                </button>
                            </div>
                        </div>
                    </li>
                </ul>
               <br>
                <div class="input-group">
                    <input type="text" placeholder="Digite o prefixo" v-model="sufix" class="form-control" @keyup.enter="addSufix(sufix)">
                    <div class="input-group-append">
                        <button type="button" class="btn btn-info text-white" v-on:click="addSufix(sufix)">
                            <span class="fa fa-plus"></span>
                        </button>
                    </div>
                </div>
            </div>
          </div>
        </div>
      </div>

      <!-- os dominios -->
      <div class="row mt-4">
        <div class="col-md-12">
          <h5>Domínios <span class="badge bg-info">{{dominios.length}}</span></h5>
            <div class="card">
                <div class="card-body">
                    <ul class="list-group">
                        <li class="list-group-item" v-for="dominio in dominios" :key="dominio">
                            
                            <div class="row">
                                <div class="col-md col">
                                    {{ dominio.name }}
                                </div>
                                <div class="col-md col">
                                    <a :href="dominio.linkCheckout" class="btn btn-info text-white" style="float: right" @click="alert('checkout')">
                                        <span class="fa fa-shopping-cart"></span>
                                    </a>
                                </div>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import "bootstrap/dist/css/bootstrap.css";
import "font-awesome/css/font-awesome.css";
export default {
    name: "lista",
    data: ()=>{
        return {
            prefix : "",
            sufix: "",
            prefixos: ["Home", "Finance"],
            sufixos: ["Tech", "Start"],
            // dominios: []
        };
    },

    methods: {
        addPrefix(prefix){
            this.prefixos.push(prefix)
            this.prefix = ""
        },

        addSufix(sufix){
            this.sufixos.push(sufix)
            this.sufix = ""
        },

        deletePrefix(prefix){
            this.prefixos.splice(this.prefixos.indexOf(prefix), 1)
        },

        deleteSufix(sufix){
            this.sufixos.splice(this.sufixos.indexOf(sufix), 1)
        },
    },

    computed:{
        dominios(){
            console.log('Gerando dominios...')
            const dominios = []
            for(const prefix of this.prefixos){
                for(const sufix of this.sufixos){
                    const name = prefix + sufix
                    const nameUrl = name.toLowerCase()
                    const linkCheckout = `https://checkout.hostgator.com.br/?a=add&sld=${nameUrl}&tld=.com.br`
                    dominios.push({
                        name,
                        linkCheckout
                    })
                }
            }
            return dominios
        }
    },
}
</script>
<style scoped>

</style>
