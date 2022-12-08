<template>
    <div class="container">
        <div class="row">
            <div class="col-6 bg-light">
                <span class="fs-4">ENTRADA DE DADOS</span>
                <hr>
                <form>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label" >Nome:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model="client.nome">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">E-mail:</label>
                        <div class="col">
                            <input type="email" class="form-control" v-model="client.email">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Senha:</label>
                        <div class="col">
                            <input type="password" class="form-control" v-model.trim="client.password">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Idade:</label>
                        <div class="col">
                            <input type="number" class="form-control" v-model.number="client.idade">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Gênero:</label>
                        <div class="col">
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="Feminino" v-model="client.genero">
                                <label class="form-check-label">
                                    Feminino
                                </label>
                            </div>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="Masculino" v-model="client.genero">
                                <label class="form-check-label">
                                    Masculino
                                </label>
                            </div>
                        </div>
                    </div>

                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Licença:</label>
                        <div class="col">
                            <div class="form-check form-switch">
                                <input class="form-check-input" type="checkbox" 
                                v-model="client.licenca"
                                true-value="SIM"
                                false-value="NÃO">
                                <label class="form-check-label">Li e aceito os termos</label>
                            </div>
                        </div>
                    </div>

                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Interesses:</label>
                        <div class="col">
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="JavaScript" v-model="client.interesses" >
                                <label class="form-check-label">
                                    JavaScript
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="VueJS" v-model="client.interesses">
                                <label class="form-check-label">
                                    VueJS
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="Angular" v-model="client.interesses">
                                <label class="form-check-label">
                                    Angular
                                </label>
                            </div>
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" value="NodeJS" v-model="client.interesses">
                                <label class="form-check-label">
                                    NodeJS
                                </label>
                            </div>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Telefone:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model="client.telefone" v-maska="'(##) # ####-####'">
                            <small class="text-muted">Formato: 11 97777-5555</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">CEP:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model="client.cep" v-maska="'#####-###'">
                            <small class="text-muted">Formato: 03610-256</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">RG:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model="client.rg" v-maska="'##.###.###-X'">
                            <small class="text-muted">Formato: Sem padrão</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">CNPJ/CPF:</label>
                        <div class="col">
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="cpf" v-model="client.cnpj_cpf">
                                <label class="form-check-label">
                                    CPF
                                </label>
                            </div>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="cnpj" v-model="client.cnpj_cpf">
                                <label class="form-check-label">
                                    CNPJ
                                </label>
                            </div>
                        </div>
                        <div v-show="client.cnpj_cpf == 'cnpj'">
                            <div class="mb-3 row">
                                <label class="col-3 col-form-label">CNPJ:</label>
                                <div class="col">
                                    <input type="text" class="form-control" v-model="client.cnpj" v-maska="'##.###.###/####-##'">
                                    <small class="text-muted">Formato: 00.000.000/0000-00</small>
                                </div>
                            </div>
                        </div>
                        <div v-show="client.cnpj_cpf == 'cpf'">
                            <div class="mb-3 row">
                                <label class="col-3 col-form-label">CPF:</label>
                                 <div class="col">
                                    <input type="text" class="form-control" v-model="client.cpf" v-maska="'###.###.###-##'">
                                    <small class="text-muted">Formato: 000.000.000-00</small>
                                </div>
                            </div>
                        </div>
                        
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Tipo Placa:</label>
                        <div class="col">
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="mercosul" v-model="client.tipoVeiculo">
                                <label class="form-check-label">
                                    Merco Sul
                                </label>
                            </div>
                            <div class="form-check form-check-inline">
                                <input class="form-check-input" type="radio" value="antigo" v-model="client.tipoVeiculo">
                                <label class="form-check-label">
                                    Antigo
                                </label>
                            </div>
                        </div>
                        <div v-show="client.tipoVeiculo == 'mercosul'">
                            <div class="mb-3 row">
                                <label class="col-3 col-form-label">Merco Sul:</label>
                                <div class="col">
                                    <input type="text" class="form-control" v-model="client.placaVeiculoMecoSul" v-maska="'AAA#A##'">
                                    <small class="text-muted">Formato: AAA0A00</small>
                                </div>
                            </div>
                        </div>
                        <div v-show="client.tipoVeiculo == 'antigo'">
                            <div class="mb-3 row">
                                <label class="col-3 col-form-label">Antigo:</label>
                                 <div class="col">
                                    <input type="text" class="form-control" v-model="client.placaVeiculo" v-maska="'AAA-####'">
                                    <small class="text-muted">Formato: AAA-0000</small>
                                </div>
                            </div>
                        </div>
                        
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Cartão:</label>
                        <div class="col">
                            <input type="text" class="form-control" v-model="client.cartaoCredito" v-maska="'####.####.####.####'">
                            <small class="text-muted">Formato: 0000.0000.0000.0000</small>
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Data:</label>
                        <div class="col">
                            <input type="date" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Data/hora local:</label>
                        <div class="col">
                            <input type="datetime-local" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Mês:</label>
                        <div class="col">
                            <input type="month" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Semana:</label>
                        <div class="col">
                            <input type="week" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Hora:</label>
                        <div class="col">
                            <input type="time" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Cor:</label>
                        <div class="col">
                            <input type="color" class="form-color">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Valor limite:</label>
                        <div class="col">
                            <input type="range" class="form-range" min="0" max="100" step="1">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Escondido:</label>
                        <div class="col">
                            <input type="hidden" class="form-control">
                        </div>
                    </div>
                    <div class="mb-3 row">
                        <label class="col-3 col-form-label">Upload:</label>
                        <div class="col">
                            <input type="file" class="form-control">
                        </div>
                    </div>
                    <hr>
                    <div class="mb-3 row">
                        <div class="col d-flex justify-content-between">
                            <button class="btn btn-secondary" type="reset">Limpar</button>
                            <button class="btn btn-success" type="button">Enviar (btn)</button>
                            <button class="btn btn-success" type="submit">Enviar (submit)</button>
                        </div>                        
                    </div>
                   
                </form>
            </div>

            
            <div class="col-6 text-white bg-secondary">
                <span class="fs-4">ESTADO DO OBJETO</span>
                <hr>
                <div class="mb-5 row">
                    <span>{{client}}</span>
                </div>

                <span class="fs-4">SAÍDA DE DADOS</span>
                <hr>
                <div class="mb-3 row">
                    <span>Nome: {{client.nome}}</span>
                </div>
                <div class="mb-3 row">
                    <span>E-mail: {{client.email}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Senha: {{client.password}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Idade: {{client.idade}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Gênero: {{client.genero}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Licença: {{client.licenca}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Interesses:</span>
                    <ul>
                        <li v-for="(tech, index) in client.interesses" :key="index">{{tech}}</li>
                    </ul>
                </div>
                <div class="mb-3 row">
                    <span>Telefone: {{client.telefone}}</span>
                </div>
                <div class="mb-3 row">
                    <span>CEP: {{client.cep}}</span>
                </div>
                <div class="mb-3 row">
                    <span>CNPJ: {{client.cnpj}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Cartão de Credito: {{client.cartaoCredito}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Placa Veiculo: {{client.placaVeiculo}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Placa Veiculo MecoSul: {{client.placaVeiculoMecoSul}}</span>
                </div>
                <div class="mb-3 row">
                    <span>RG: {{client.rg}}</span>
                </div>
                <div class="mb-3 row">
                    <span>Data/hora local:</span>
                </div>
                <div class="mb-3 row">
                    <span>Mês:</span>
                </div>
                <div class="mb-3 row">
                    <span>Semana:</span>
                </div>
                <div class="mb-3 row">
                    <span>Hora:</span>
                </div>
                <div class="mb-3 row">
                    <span>Cor:</span>
                </div>
                <div class="mb-3 row">
                    <span>Valor limite:</span>
                </div>
                <div class="mb-3 row">
                    <span>Escondido:</span>
                </div>
                <div class="mb-3 row">
                    <span>Upload:</span>
                </div>  
            </div>
        </div>

    </div>

</template>

<script>
export default {
    name: 'Formulario',
    data:()=>({
        
        client:{
            nome:'',
            email:'',
            password:'',
            idade:'',
            licenca: 'NÃO',
            interesses: [],
            genero:'',
            telefone: '',
            cep:'',
            cpf:'',
            cnpj:'',
            cnpj_cpf: '',
            cartaoCredito:'',
            placaVeiculo:'',
            placaVeiculoMecoSul:'',
            tipoVeiculo:'',
            rg:'',
        }
    })
}
</script>
