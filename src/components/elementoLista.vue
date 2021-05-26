<template>
  <div>
    <h5>
      {{tituloList}} 
      <span class="badge bg-info">{{ items.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" :key="item">
            <div class="row">
              <div class="col-md col">
                {{ item }}
              </div>
              <div class="col-md col">
                <button
                  class="btn btn-info text-white"
                  style="float: right"
                  @click="deleteItem(item)"
                >
                  <span class="fa fa-trash"></span>
                </button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input
            type="text"
            placeholder="Digite o prefixo"
            class="form-control"
            v-model="item"
            @keyup.enter="addItem(item)"
          />
          <div class="input-group-append">
            <button
              type="button"
              class="btn btn-info text-white"
              v-on:click="addItem(item)"
            >
              <span class="fa fa-plus"></span>
            </button>
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
  name: "elementoLista",
  data(){
    return {
      item: ""
    }
  },
  props: {
    tituloList: String, 
    items: Array
  },

  methods: {
    addItem(item){
      if(this.item == null || this.item == ""){alert("Preencha o campo com dado válido!")}
      else{
        this.$emit("addItem", item),
        this.item = ""
      }
    },
    deleteItem(item){
      this.$emit("deleteItem", item)
    }
  }
}
</script>


