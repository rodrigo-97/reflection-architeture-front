<template>
  <transition name="home">
    <nav class="panel  ">
      <p class="panel-heading">Personagens</p>
      <div class="panel-block columns">
        <div class="column is-8">
          <div class="d-flex justify-end">
            <b-button type="is-success" tag="router-link" to="/characters-insert" icon-left="plus-circle" size="lg"
              >Adicionar</b-button
            >
            <hr>
          </div>
          <table style="width: 100%">
            <tr>
              <th>#</th>
              <th>Nome</th>
              <th>Nº de ep.</th>
              <th>Ações</th>
            </tr>
            <tr>
              <td>1</td>
              <td>Attack on Titan</td>
              <td>60</td>
              <td>
                <b-button type="is-primary" icon-left="pencil" size="lg"
                  >Alterar</b-button
                >
                <b-button type="is-danger" icon-left="delete" size="lg"
                  >Excluir</b-button
                >
              </td>
            </tr>
            <tr>
              <td>2</td>
              <td>Naruto</td>
              <td>500</td>
            </tr>
          </table>
        </div>
      </div>
    </nav>
  </transition>
</template>
