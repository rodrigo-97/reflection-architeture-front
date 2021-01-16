<template>
  <form class="columns" @submit="submit()">
    <div class="panel column is-6   ml-5">
      <div class="panel-heading">Cadastro de personagens</div>
      <div class="panel-block columns">
        <div class="main column is-12">
          <b-field label="Anime" :type="anime.type" :message="anime.message">
            <b-select @blur="validateAnime" placeholder="Selecione um character" v-model="character.anime">
              <option value="0" disable>Selecione um anime</option>
              <option
                v-for="anime in animes"
                :value="anime.id"
                :key="anime.id"
              >
                {{ anime.name }}
              </option>
            </b-select>
          </b-field>

          <b-field
            label="Nome do personagem"
            :type="nameInput.type"
            required
            :message="nameInput.message"
          >
            <b-input
              icon="account"
              size="lg"
              maxlength="30"
              placeholder="Digite o nome do personagem"
              v-model="character.name"
              @blur="validateName(character.name), validateForm()"
            ></b-input>
          </b-field>

          <b-field
            label="Idade do personagem"
            required
            :type="ageInput.type"
            :message="ageInput.message"
          >
            <b-input
              icon="counter"
              size="lg"
              maxlength="4"
              placeholder="Digite a idade do personagem"
              v-model="character.age"
              @blur="validateAge(character.age), validateForm()"
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
      character: {
        id: '',
        name: '',
        anime: '',
        age: '',
      },
      nameInput: {
        type: '',
        message: '',
        isOk: false,
      },
      ageInput: {
        type: '',
        message: '',
        isOk: false,
      },
      anime: {
        type: '',
        message: '',
        isOk: false,
      },
      isFormInvalid: true,
      animes: [
        { id: 1, name: 'Attack on Titan'},
        { id: 2, name: 'Naruto'},
        { id: 3, name: 'Bleach'},
        { id: 4, name: 'Fairy Tale'},
        { id: 5, name: 'One punch man'},
        { id: 6, name: 'Nanatsu'},
      ]
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
    validateAge(age) {
      if (age.match(/^[-+]?[0-9]+$/)) {
        this.ageInput.type = 'is-success'
        this.ageInput.message = 'Você parece bom em cadastrar characters 😲'
        this.ageInput.isOk = true
        return true
      } else {
        this.ageInput.type = 'is-danger'
        this.ageInput.message = 'Cansei cara. Aqui pra vc ÓOO 🖕'
        this.ageInput.isOk = false
        return false
      }
    },

    validateAnime (){
      if (this.character.anime <= 0){
        this.anime.type = "is-danger"
        this.anime.message = "Tá difícil selecionar um anime aqui em cima cara? 😭"
        this.anime.isOk = false
      }else{
        this.anime.type = "is-success"
        this.anime.message = "Parabéns por saber cadastrar um Personagem. 🤙"
        this.anime.isOk = true
      }
    },

    validateForm() {
      if (this.nameInput.isOk && this.ageInput.isOk && this.anime.isOk) {
        this.isFormInvalid = false
      } else {
        this.isFormInvalid = true
      }
    },

    submit() {
      alert(this.character.toString())
    },
  }
}
</script>

<style>
.align {
  display: flex;
  justify-content: flex-end;
}
</style>
