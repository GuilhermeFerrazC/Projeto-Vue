<template>
  <div class="container">
    <h1>Cadastro de Jogos</h1>

    <!-- Formulário para adicionar jogos -->
    <div class="input-container">
      <input 
        v-model="novoJogo.nome" 
        placeholder="Nome do jogo" 
        @input="validarCampos"
      />
      <input 
        v-model="novoJogo.genero" 
        placeholder="Gênero do jogo" 
        @input="validarCampos"
      />
      <input 
        v-model="novoJogo.plataforma" 
        placeholder="Plataforma do jogo" 
        @input="validarCampos"
      />
      <button 
        @click="adicionarJogo" 
        :disabled="!isValido"
      >
        Cadastrar Jogo
      </button>
    </div>

    <!-- Lista de jogos -->
    <div v-if="jogos.length > 0">
      <ul>
        <li v-for="(jogo, index) in jogos" :key="index">
          {{ jogo.nome }} - {{ jogo.genero }} ({{ jogo.plataforma }})
          <button @click="removerJogo(index)">Deletar</button>
        </li>
      </ul>
    </div>
    <div v-else>
      <p>Nenhum jogo cadastrado ainda.</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      novoJogo: {
        nome: '',
        genero: '',
        plataforma: ''
      },
      jogos: [],
      isValido: false
    };
  },
  methods: {
    adicionarJogo() {
      if (this.isValido) {
        this.jogos.push({ ...this.novoJogo });
        this.limparCampos();
      }
    },
    removerJogo(index) {
      this.jogos.splice(index, 1);
    },
    validarCampos() {
      this.isValido =
        this.novoJogo.nome.trim() !== '' &&
        this.novoJogo.genero.trim() !== '' &&
        this.novoJogo.plataforma.trim() !== '';
    },
    limparCampos() {
      this.novoJogo = { nome: '', genero: '', plataforma: '' };
      this.isValido = false;
    }
  }
};
</script>

<style scoped>
.container {
  max-width: 500px;
  margin: 0 auto;
  text-align: center;
}

.input-container {
  margin-bottom: 20px;
}

input {
  display: block;
  margin: 5px auto;
  padding: 8px;
}

button {
  margin: 10px 5px;
  padding: 10px 20px;
  cursor: pointer;
}
</style>
