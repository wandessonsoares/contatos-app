<template>
  <div id="app">

    <nav>
      <div class="nav-wrapper blue darken-1">
        <a href="#" class="brand-logo center">Contatos App</a>
      </div>
    </nav>

    <div class="container">

      <form>

          <label>Nome</label>
          <input type="text" placeholder="Nome">
          <label>Quantidade</label>
          <input type="number" placeholder="QTD">
          <label>Valor</label>
          <input type="text" placeholder="Valor">

          <button class="waves-effect waves-light btn-small"><i class="far fa-save"></i> Salvar</button>

      </form>

      <table>

        <thead>

          <tr>
            <th>Nome</th>
            <th>Categoria</th>
            <th>Telefone(s)</th>
            <th>Opções</th>
          </tr>

        </thead>

        <tbody>

          <tr v-for="contato of contatos" :key="contato.id">

            <td>{{ contato.nome }}</td>
            <td>{{ contato.categoria }}</td>
            <div v-for="telefone of contato.telefones" :key="telefone.id">
                <td>{{ telefone.numeroTelefone }}</td>
            </div>
            <td>
              <button class="waves-effect btn-small blue darken-1"><i class="far fa-edit"></i></button>
              <button class="waves-effect btn-small red darken-1"><i class="far fa-trash-alt"></i></button>
            </td>

          </tr>

        </tbody>
      
      </table>

    </div>

  </div>
</template>

<script>

import Contato from './services/contatos'
var i;

export default {

  data(){
    return {
      contatos: [],
      telefones: []
    }
  },

  mounted(){
    Contato.listar().then(resposta => {
      this.contatos = resposta.data
      for(i = 0; i < 3; i++){
        console.log(this.contatos[i].telefones[0].numeroTelefone)
      }
      this.telefones = this.contatos.telefones
    })
  }
}

</script>

<style>

</style>
