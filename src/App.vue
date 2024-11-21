<template>
  <div class="min-h-screen bg-gray-200 flex items-center justify-center">
      <h2 class="text-3xl font-semibold text-gray-800 mb-8 text-center">Cadastro de Empresa</h2>

      <form @submit.prevent="submitForm" class="space-y-6">
        <!-- Grids para campos lado a lado -->
        <div class="grid grid-cols-1 gap-6 md:grid-cols-2 md:gap-10">
          <!-- Nome -->
          <div class="mb-6">
            <label for="nome" class="block text-gray-500 font-medium">Nome da Empresa</label>
            <input type="text" id="nome" v-model="formData.nome" class="input-field" required>
          </div>

          <!-- Rua -->
          <div class="mb-6">
            <label for="rua" class="block text-gray-500 font-medium">Rua</label>
            <input type="text" id="rua" v-model="formData.rua" class="input-field" required>
          </div>

          <!-- Número -->
          <div class="mb-6">
            <label for="numero" class="block text-gray-500 font-medium">Número</label>
            <input type="text" id="numero" v-model="formData.numero" class="input-field" required>
          </div>

          <!-- Bairro -->
          <div class="mb-6">
            <label for="bairro" class="block text-gray-500 font-medium">Bairro</label>
            <input type="text" id="bairro" v-model="formData.bairro" class="input-field" required>
          </div>

          <!-- Estado -->
          <div class="mb-6">
            <label for="estado" class="block text-gray-500 font-medium">Estado</label>
            <input type="text" id="estado" v-model="formData.estado" class="input-field" required>
          </div>

          <!-- WhatsApp -->
          <div class="mb-6">
            <label for="whatsapp" class="block text-gray-500 font-medium">Número de WhatsApp</label>
            <input type="text" id="whatsapp" v-model="formData.whatsapp" class="input-field" required>
          </div>

          <!-- CNPJ -->
          <div class="mb-6">
            <label for="cnpj" class="block text-gray-500 font-medium">CNPJ</label>
            <input type="text" id="cnpj" v-model="formData.cnpj" class="input-field" required>
          </div>

          <!-- Segmento -->
          <div class="col-span-2 mb-6">
            <label for="segmento" class="block text-gray-500 font-medium">Segmento</label>
            <select id="segmento" v-model="formData.segmento" class="input-field" required>
              <option value="">Selecione um segmento</option>
              <option value="Tecnologia">Tecnologia</option>
              <option value="Esporte">Esporte</option>
              <option value="Saúde">Saúde</option>
            </select>
          </div>
        </div>

        <!-- Botão de Enviar -->
        <div class="text-center">
          <button type="submit" class="submit-button">
            Cadastrar Empresa
          </button>
        </div>
      </form>

      <!-- Mensagem de Sucesso ou Erro -->
      <p v-if="successMessage" class="mt-4 text-green-500 text-center">{{ successMessage }}</p>
      <p v-if="errorMessage" class="mt-4 text-red-500 text-center">{{ errorMessage }}</p>
    </div>
</template>

<script>
export default {
  data() {
    return {
      formData: {
        nome: '',
        rua: '',
        numero: '',
        bairro: '',
        estado: '',
        whatsapp: '',
        cnpj: '',
        segmento: ''
      },
      successMessage: '',
      errorMessage: ''
    };
  },
  methods: {
    // Método para submeter o formulário
    submitForm() {
      // Exemplo de validação no frontend
      if (this.formData.nome && this.formData.rua && this.formData.numero && this.formData.bairro && this.formData.estado && this.formData.whatsapp && this.formData.cnpj && this.formData.segmento) {
        // Se todos os campos estiverem preenchidos corretamente, exibe uma mensagem de sucesso
        this.successMessage = 'Empresa cadastrada com sucesso!';
        this.errorMessage = ''; // Limpar a mensagem de erro, se houver
        // Limpar o formulário
        this.formData = { nome: '', rua: '', numero: '', bairro: '', estado: '', whatsapp: '', cnpj: '', segmento: '' };
      } else {
        // Se algum campo estiver vazio, exibe uma mensagem de erro
        this.errorMessage = 'Por favor, preencha todos os campos obrigatórios.';
        this.successMessage = ''; // Limpar a mensagem de sucesso, se houver
      }
    }
  }
};
</script>

<style scoped>
/* Estilos personalizados */
.input-field {
  width: 100%;
  padding: 1rem;
  margin-top: 0.5rem;
  border-radius: 8px;
  border: 1px solid rgb(233, 35, 35);
  background-color: #fafaf6;
  font-size: 1rem;
  transition: border-color 0.3s ease, background-color 0.3s ease;
}

.input-field:focus {
  outline: none;
  border-color: #6366F1;
  background-color: #E0E7FF;
}

.submit-button {
  padding: 1rem 2rem;
  background-color: #f16363;
  color: white;
  font-weight: bold;
  border-radius: 8px;
  border: none;
  transition: background-color 0.3s ease;
}

.submit-button:hover {
  background-color: #4F46E5;
}

.submit-button:focus {
  outline: none;
}

h2 {
  font-family: 'Arial', sans-serif;
  font-size: 2rem;
  color: #f20b0b;
}

p {
  font-size: 1rem;
  font-weight: bold;
}

.grid {
  display: grid;
  gap: 30px;  /* Aumentando o espaçamento entre as colunas */
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
}

@media (min-width: 768px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

.mb-6 {
  margin-bottom: 0.5rem;  /* Aumentando o espaçamento inferior entre os campos */
}

.md\:gap-10 {
  gap: 2.8rem;  /* Aumentando o espaçamento entre as colunas em telas médias */
}
</style>
