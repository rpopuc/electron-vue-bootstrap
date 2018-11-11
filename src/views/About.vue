<template>
  <div class="container">
    <div class="row">
      <div class="col">
        <div class="card">
          <div class="card-header">
            Aplicação de Exemplo com
          </div>
          <div class="card-body">
            <article>
              <p>
                <img src="./../assets/electron-logo.png" width="40px" class="mr-2">
                <a href="https://electronjs.org/" @click.prevent="openLink">Electron</a>
              </p>
              <p>
                <img src="./../assets/vue-logo.png" width="40px" class="mr-2">
                <a  href="https://vuejs.org/" @click.prevent="openLink">Vuejs</a>
              </p>
              <p>
                <img src="./../assets/bootstrap-logo.png" width="40px" class="mr-2">
                <a href="https://getbootstrap.com/" @click.prevent="openLink">Bootstrap</a>
              </p>
            </article>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
    const {shell} = require('electron')
    export default {
        methods: {
          openLink(e) {
            shell.openExternal(e.target.href)
          }
        },
    }
</script>
