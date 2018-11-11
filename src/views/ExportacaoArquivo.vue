<template>
    <div class="container">
        <div class="row">
            <div class="col">
                <div class="card">
                    <div class="card-header">
                        Exportação de arquivo
                    </div>
                    <div class="card-body">
                        <div class="form-group">
                            <label for="email">Email</label>
                            <input v-model="email" type="email" class="form-control" id="email" aria-describedby="emailHelp" placeholder="Digite seu email">
                            <small id="emailHelp" class="form-text text-muted">Nunca compartilharemos seu email com terceiros.</small>
                        </div>
                        <div class="form-group">
                            <label for="password">Senha</label>
                            <input v-model="password" type="password" class="form-control" id="password" placeholder="Senha">
                        </div>
                        <div class="form-check">
                            <input type="checkbox" v-model="confirmacao" class="form-check-input" id="confirmation">
                            <label class="form-check-label" for="confirmation">Confirmo que os dados são verdadeiros.</label>
                        </div>

                        <hr/>

                        <div class="d-flex justify-content-start align-items-center">
                            <button @click.prevent="exportData" class="btn btn-primary">Exportar</button>
                            <div class="ml-4">Clique no botão para exportar o formulário.</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import { remote } from 'electron'
    export default {
        props: {

        },

        data() {
            return {
                email: '',
                password: '',
                confirmacao: '',
            };
        },

        methods: {
            exportData() {
                var dialog = remote.dialog;
                var fs = require('fs');
                let conteudo = `Email: ${this.email}\nSenha: ${this.password}\nConfirmação: ${this.confirmacao}`;

                dialog.showSaveDialog((arquivo) => {
                    if (arquivo === undefined){
                        // console.log("Nenhum arquivo definido");
                        return;
                    }

                    fs.writeFile(arquivo, conteudo, (err) => {
                        if (err) {
                            alert("Erro ao criar o arquivo "+ err.message)
                        }
                        alert("Arquivo salvo!");
                    });
                });
            },
        },
    }
</script>