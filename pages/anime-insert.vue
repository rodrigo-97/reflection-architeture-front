<template>
  <form class="columns" @submit="submit()">
    <div class="panel column is-6   ml-5">
      <div class="panel-heading">Cadastro de Anime</div>
      <div class="panel-block columns">
        <div class="main column is-12">
          <b-field
            label="Nome do anime"
            :type="nameInput.type"
            required
            :message="nameInput.message"
          >
            <b-input
              icon="television"
              size="lg"
              maxlength="30"
              placeholder="Digite o nome do anime"
              v-model="anime.name"
              @blur="validateName(anime.name), validateForm()"
            ></b-input>
          </b-field>

          <b-field
            label="Número de episódios"
            required
            :type="numEpInput.type"
            :message="numEpInput.message"
          >
            <b-input
              icon="counter"
              size="lg"
              maxlength="4"
              placeholder="Digite o número de episódios do anime"
              v-model="anime.numEp"
              @blur="validateNumEp(anime.numEp), validateForm()"
            ></b-input>
          </b-field>
        </div>
      </div>
      <div class="align colum is-12">
        <b-button
          native-type="submit"
          type="is-success"
          :disabled="isFormInvalid"
          >SALVAR</b-button
        >
      </div>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      anime: {
        id: '',
        name: '',
        numEp: '',
      },
      nameInput: {
        type: '',
        message: '',
        isOk: false,
      },
      numEpInput: {
        type: '',
        message: '',
        isOk: false,
      },
      isFormInvalid: true,
    }
  },

  methods: {
    validateName(name) {
      if (name.match(/^[A-ZÀ-Ÿ][A-zÀ-ÿ']/)) {
        this.nameInput.type = 'is-success'
        this.nameInput.message = 'Uffaaa. Tá tudo certo por aqui 👏'
        this.nameInput.isOk = true
        return true
      } else {
        this.nameInput.type = 'is-danger'
        this.nameInput.message =
          'Affz. Pelo amor de Deus, digita esse negócio direito 🙄'
        this.nameInput.isOk = false
        return false
      }
    },
    validateNumEp(numEp) {
      if (numEp.match(/^[-+]?[0-9]+$/)) {
        this.numEpInput.type = 'is-success'
        this.numEpInput.message = 'Você parece bom em cadastrar animes 😲'
        this.numEpInput.isOk = true
        return true
      } else {
        this.numEpInput.type = 'is-danger'
        this.numEpInput.message = 'Por favor algum 👽 me abduza daqui.'
        this.numEpInput.isOk = false
        return false
      }
    },

    validateForm() {
      if (this.nameInput.isOk && this.numEpInput.isOk) {
        this.isFormInvalid = false
      } else {
        this.isFormInvalid = true
      }
    },

    submit() {
      alert(this.anime.toString())
    },
  },
}
</script>

<style>
.align {
  display: flex;
  justify-content: flex-end;
}
</style>
