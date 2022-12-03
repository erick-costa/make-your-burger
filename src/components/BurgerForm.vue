<template>
  <div>
    <p>Msg</p>
    <div>
      <form id="burger-form">
        <div class="input-container">
          <label for="name">Nome do cliente</label>
          <input
            type="text"
            id="name"
            name="name"
            v-model="name"
            placeholder="Digite o seu nome"
          />
        </div>
        <div class="input-container">
          <label for="bread">Escolha o pão:</label>
          <select name="bread" id="bread" v-model="bread">
            <option value="">Selecione o seu pão</option>
            <option v-for="bread in breads" :value="bread.tipo">
              {{ bread.tipo }}
            </option>
          </select>
        </div>
        <div class="input-container">
          <label for="meat">Escolha a carne do seu burger:</label>
          <select name="meat" id="meat" v-model="meat">
            <option value="">Selecione o tipo de carne</option>
            <option v-for="meat in meats" :value="meat.tipo">
              {{ meat.tipo }}
            </option>
          </select>
        </div>
        <div id="extras-container" class="input-container">
          <label id="extras-title" for="extras">Selecione os opcionais:</label>
          <div class="checkbox-container" v-for="extra in extrasdata">
            <input
              type="checkbox"
              name="extras"
              v-model="extras"
              :value="extra.tipo"
            />
            <span>{{ extra.tipo }}</span>
          </div>
        </div>
        <div class="input-container">
          <input type="submit" class="submit-btn" value="Criar meu Burger!" />
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: "BurgerForm",
  data() {
    return {
      breads: null,
      meats: null,
      extrasdata: null,
      name: null,
      bread: null,
      meat: null,
      extras: [],
      status: "Solicitado",
      msg: null,
    }
  },
  methods: {
    async getIngredients() {
      const req = await fetch("http://localhost:3000/ingredientes")
      const data = await req.json()

      this.breads = data.paes
      this.meats = data.carnes
      this.extrasdata = data.opcionais
    },
  },
  mounted() {
    this.getIngredients()
  },
}
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222;
  padding: 5px 10px;
  border-left: 4px solid #fcba03;
}

input,
select {
  padding: 5px 10px;
  width: 300px;
}

#extras-container {
  flex-direction: row;
  flex-wrap: wrap;
}

#extras-title {
  width: 100%;
}

.checkbox-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.checkbox-container span,
.checkbox-container input {
  width: auto;
}

.checkbox-container span {
  margin-left: 6px;
  font-weight: bold;
}

.submit-btn {
  background-color: #222;
  color: #fcba03;
  font-weight: bold;
  border: 2px solid #222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  background-color: transparent;
  color: #222;
}
</style>
