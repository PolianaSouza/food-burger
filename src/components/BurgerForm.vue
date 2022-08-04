<template>
  <div class="q-pa-md flex flex-center">
    <q-form
      @submit.prevent="criateBurger"
      @reset="onReset"
      class="column q-gutter-xs"
      style="max-width: 400px"
    >
      <label id="label">Nome do Cliente:</label>
      <q-input
        outlined
        v-model="form.name"
        placeholder="Digite seu nome"
        lazy-rules
        :rules="[
          (val) => (val && val.length > 0) || 'Por favor digite seu nome!',
        ]"
      />
      <label id="label">Escolha o pão:</label>
      <q-select
        outlined
        v-model="form.bread"
        :options="breadOptions"
        emit-value
        map-options
        behavior="menu"
        option-label="tipo"
        option-value="tipo"
        lazy-rules
        :rules="[val => val && val.length > 0 || 'Escolha uma opção!']"
      />
      <label id="label">Escolha a carne do seu burger:</label>
      <q-select
        outlined
        v-model="form.meat"
        :options="meatOptions"
        emit-value
        map-options
        behavior="menu"
        option-label="tipo"
        option-value="tipo"
        lazy-rules
        :rules="[val => val && val.length > 0 || 'Escolha uma opção!']"
      />
      <label id="title-optional">Escolha os opcionais:</label>
      <div class="row flex justify-between">
        <span v-for="(option, index) in optionalGroup" :key="index">
          <q-checkbox
            v-model="form.optional"
            :label="option.tipo"
            :val="option.tipo"
          />
        </span>
      </div>
      <div class="q-mb-md q-mt-md flex flex-center">
        <q-btn 
          type="submit"
          label="Criar meu burger"/>
      </div>
    </q-form>
  </div>
</template>

<script>
import {api} from '../boot/axios'

export default {
  name: "BurgerForm",
  data() {
    return {
      form: {
        name: "",
        bread: "",
        meat: "",        
        optional: [],       
      },
      breadOptions: [],
      meatOptions: [],
      optionalGroup: [],
    };
  },
  methods: {
    async getIngredientes() {
      // url: http://localhost:3000/ingredientes

      try {
        const response = await api.get('ingredientes');
        
        const data = response.data

        this.breadOptions = data.paes;
        this.meatOptions = data.carnes;
        this.optionalGroup = data.opcionais;
        
      } catch (error) {
        console.log(error)
      }
    },
    async criateBurger(){
      try {
        await api.post('hamburgueres', this.form);
        this.$q.notify({
          type: 'positive',
          message: 'Hamburguer criado com sucesso!',
          color: 'green-10',
          timeout: 1000,
          textColor: 'white',
          position: 'center',
          icon: 'done_all'
        })

      } catch (error) {
        console.log(error)
      }
    }
  },
  mounted() {
    this.getIngredientes();
  },
};
</script>

<style scoped>
.q-btn {
  width: 300px;
  background-color: #15171d;
  color: rgb(230, 193, 48);
  font-size: 16px;
  font-weight: bold;
  border: 2px solid #15171d;
  padding: 10px;
  cursor: pointer;
  transition: 0.5s;
}
.q-btn:hover {
  background-color: #fff;
  color: #15171d;
}

#label,
#title-optional {
  font-weight: bold;
  font-size: 16px;
  color: #15171d;
  padding: 5px 10px;
  border-left: 4px solid #e6c130;
}

#title-optional {
  width: 100%;
}

.q-checkbox {
  font-weight: bold;
  margin-left: 6px;
}
</style>
