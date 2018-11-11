<template>
  <div id="app">
    <nav class="navbar navbar-expand-md navbar-light navbar-laravel">
        <div class="container">
            <router-link class="navbar-brand" to="/">
              <img src="./assets/electron-logo.png" width="30px"> +
              <img src="./assets/vue-logo.png" width="30px"> +
              <img src="./assets/bootstrap-logo.png" width="30px">
            </router-link>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <!-- Left Side Of Navbar -->
                <ul class="navbar-nav mr-auto">
                  <li class="nav-item" :class="{active: $router.currentRoute.name == 'exportacao'}">
                    <router-link class="nav-link" to="/exportacao">
                      Exportação
                    </router-link>
                  </li>
                  <li class="nav-item" :class="{active: $router.currentRoute.name == 'about'}">
                    <router-link class="nav-link" to="/about">
                      Sobre
                    </router-link>
                  </li>
                </ul>

                <!-- Right Side Of Navbar -->
                <ul class="navbar-nav ml-auto">
                    <li class="nav-item dropdown">
                        <a id="navbarDropdown" class="nav-link dropdown-toggle" href="#" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" v-pre>
                          Usuário <span class="caret"></span>
                        </a>

                        <div class="dropdown-menu dropdown-menu-right" aria-labelledby="navbarDropdown">
                          <a href="#" class="dropdown-item" @click.prevent="sair">
                            Sair
                          </a>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </nav>

    <main class="py-4">
      <router-view/>
    </main>
  </div>
</template>

<style lang="scss">
  @import './scss/app.scss';
</style>

<script>
  const remote = require('electron').remote;
  export default {
    name: 'App',
    mounted() {
      this.$nextTick().then(() => {
        this.$router.push({ path: `/` });
      });
    },
    methods: {
      sair() {
        remote.getCurrentWindow().close();
      }
    }
  }
</script>
