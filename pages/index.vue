<template>
  <transition name="home">
    <div class="section">
      <div class="columns">
        <div class="column is-6">
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
                <b-button type="is-primary">Alterar</b-button>
                <b-button type="is-danger">Excluir</b-button>
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
    </div>
  </transition>
</template>