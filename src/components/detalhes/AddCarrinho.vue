<template>
  <div class="row mt-4">
    <div class="col-3">
      <label class="sr-only" for="inlineFormInputName2">Quantidade</label>
      <input
        type="number"
        v-model="quantidade"
        class="form-control mb-2 mr-sm-2"
      />
    </div>
    <button
      v-if="Object.keys(fornecedor).length === 0"
      @click.stop="adicionarNoCarrinho({ produto, quantidade })"
      type="button"
      class="btn btn-primary btn-lg btn-block col-7"
    >
      Adicionar no carrinho
    </button>
    <router-link
      v-if="Object.keys(fornecedor).length !== 0"
      type="button"
      class="btn btn-primary btn-lg btn-block col-7"
      style="padding: 10px; width: 50%"
      :to="'/editarProduto/' + this.$route.params.idProduto"
    >
      Editar
    </router-link>
  </div>
</template>
<script>
import { mapActions, mapState } from "vuex";
export default {
  props: ["produto"],
  data() {
    return {
      quantidade: 1,
    };
  },
  computed: {
    ...mapState("produto", ["carrinho"]),
    ...mapState("usuario", ["fornecedor"]),
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
  mounted() {
    console.log(this.$route.params.idProduto);
  },
};
</script>
<style>
</style>