<template>
  <div>
    <div class="card shadow-sm product-card">
      <router-link
        type="button"
        class="container-product-card"
        :to="'/detalhes/' + produto.id"
      >
        <img
          v-bind:src="`${produto.fotoUrl}`"
          class="card-img-top product-image"
          v-bind:tag="`${produto.nome}`"
          v-bind:title="`${produto.nome}`"
        />
      </router-link>
      <div class="card-body">
        <h5 class="card-title text-left product-name">
          {{ produto.nome }}
        </h5>
        <p class="text-left product-price">
          <spam class="real">R$ </spam>{{ produto.preco.toLocaleString(2) }}
        </p>
        <router-link
          type="button"
          class="btn btn-primary btn-md product-button details"
          :to="'/detalhes/' + produto.id"
        >
          Adicionar
        </router-link>
      </div>
    </div>
  </div>
</template>
<script>
import { mapActions, mapState } from "vuex";
export default {
  name: "CardProduto",
  props: ["produto"],
  data() {
    return {
      quantidade: 1,
    };
  },
  computed: {
    ...mapState("produto", ["carrinho"]),
  },
  methods: {
    ...mapActions("produto", ["adicionarNoCarrinho", "removerDoCarrinho"]),
  },
  watch: {
    quantidade(val) {
      if (val <= 0) {
        this.quantidade = 1;
      }
    },
  },
};
</script>
<style>
.container-product-card p {
  color: #3d3f44;
  text-decoration: none;
}

.container-product-card:hover {
  color: #3d3f44;
  text-decoration: none;
}

.card .product-image {
  margin: auto;
  height: 140px;
  width: 140px;
  margin-top: 10px;
  height: fit-content;
}

.card .product-name {
  font-size: 0.9375rem;
}

.card .product-price {
  font-family: "Source Sans Pro", sans-serif !important;
  font-size: 1.5em;
  margin-top: 70px !important;
  padding: 0 !important;
  margin-bottom: 7px;
  font-weight: 700;
}

.card .product-price .real {
  font-size: 0.6em !important;
  vertical-align: 5px;
}

.btn.product-button {
  height: 35px !important;
  margin: auto;
  border-radius: 100px;
  border: 1px solid #008542;
  color: #008542;
  font-size: 0.9em;
  font-family: "Source Sans Pro", sans-serif;
  font-weight: 600;
  background-color: #fff;
}

.btn.product-button:hover {
  color: #fff;
  background-color: #008542;
}

.btn.product-button:active {
  color: #fff !important;
  background-color: #008542 !important;
  border: 1px solid #008542 !important;
}

.btn.product-button.details {
  padding-left: 35px;
  padding-right: 35px;
}

.card-title {
  color: black;
  font-size: 1.1em;
  font-weight: 900 !important;
  font-family: "Roboto", sans-serif !important;
  word-wrap: break-word;
  position: absolute;
}

.card.product-card {
  width: 175px !important;
}
</style>