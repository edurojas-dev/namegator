<template>
  <div class="container-fluid p-5" id="listaNomes">
    <div class="container">
      <div class="row">
        <div class="col-md mt-3">
            <elemtoLista  tituloList="Prefixos" :items.sync="prefixos"></elemtoLista>
        </div>
        <div class="col-md mt-3">
            <elemtoLista  tituloList="Sufixos" :items.sync="sufixos"></elemtoLista>
        </div>
      </div>

      <!-- os dominios -->
      <div class="row mt-4">
        <div class="col-md-12">
          <h5 class="text-white">
            Domínios <span class="badge bg-info">{{ dominios.length }}</span>
          </h5>
          <div class="card">
            <div class="card-body">
              <ul class="list-group">
                <li
                  class="list-group-item"
                  v-for="dominio in dominios"
                  :key="dominio"
                >
                  <div class="row">
                    <div class="col-md col">
                      {{ dominio.name }}
                    </div>
                    <div class="col-md col">
                      <a
                        :href="dominio.linkCheckout"
                        class="btn btn-info text-white"
                        style="float: right"
                        @click="alert('checkout')"
                      >
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
import elemtoLista from "./elementoLista.vue"
export default {
  components: {
    elemtoLista,
  },
  name: "lista",
  data: () => {
    return {
      prefixos: ["Home", "Finance"],
      sufixos: ["Tech", "Start"],
    };
  },
  computed: {
    dominios() {
      console.log("Gerando dominios...");
      const dominios = [];
      for (const prefix of this.prefixos) {
        for (const sufix of this.sufixos) {
          const name = prefix + sufix;
          const nameUrl = name.toLowerCase();
          const linkCheckout = `https://checkout.hostgator.com.br/?a=add&sld=${nameUrl}&tld=.com.br`;
          dominios.push({
            name,
            linkCheckout,
          });
        }
      }
      return dominios;
    },
  },
};
</script>
<style scoped></style>
