# tela-login-painel-usuario :mortar_board::lock: :key:

## Tela de Login e Painel de Usuário Teste Front-end
Foi adicionado uma tela inicial chamada Login-usuario.html
o ponto principal desta tela é o validador de CPF, pois não quis firular demais na estruturação e interatividade da página.
### Eis o código.
        <script>
      function mascara_cpf(i){
   
        var v = i.value;
        
        if(isNaN(v[v.length-1])){
           i.value = v.substring(0, v.length-1);
           return;
        }
        
        i.setAttribute("maxlength", "14");
        if (v.length == 3 || v.length == 7) i.value += ".";
        if (v.length == 11) i.value += "-";
     
     }
    </script>
    <input id="CPF" oninput="mascara_cpf(this)" type="text" placeholder="CPF do titular">
    
## Já na segunda página, após validar o usuário, como no teste pedia que o usuário tivesse a permissão de somente alterar o endereço, utilizei uma api free
do site ViaCEP que deu uma elegância ao projeto.
    https://viacep.com.br/exemplo/javascript/
### Eis a API
            
    function limpa_formulário_cep() {
            //Limpa valores do formulário de cep.
            document.getElementById('rua').value=("");
            document.getElementById('bairro').value=("");
            document.getElementById('cidade').value=("");
            document.getElementById('uf').value=("");
            document.getElementById('ibge').value=("");
    }

    function meu_callback(conteudo) {
        if (!("erro" in conteudo)) {
            //Atualiza os campos com os valores.
            document.getElementById('rua').value=(conteudo.logradouro);
            document.getElementById('bairro').value=(conteudo.bairro);
            document.getElementById('cidade').value=(conteudo.localidade);
            document.getElementById('uf').value=(conteudo.uf);
            document.getElementById('ibge').value=(conteudo.ibge);
        } //end if.
        else {
            //CEP não Encontrado.
            limpa_formulário_cep();
            alert("CEP não encontrado.");
        }
    }
        
    function pesquisacep(valor) {

        //Nova variável "cep" somente com dígitos.
        var cep = valor.replace(/\D/g, '');

        //Verifica se campo cep possui valor informado.
        if (cep != "") {

            //Expressão regular para validar o CEP.
            var validacep = /^[0-9]{8}$/;

            //Valida o formato do CEP.
            if(validacep.test(cep)) {

                //Preenche os campos com "..." enquanto consulta webservice.
                document.getElementById('rua').value="...";
                document.getElementById('bairro').value="...";
                document.getElementById('cidade').value="...";
                document.getElementById('uf').value="...";
                document.getElementById('ibge').value="...";

                //Cria um elemento javascript.
                var script = document.createElement('script');

                //Sincroniza com o callback.
                script.src = 'https://viacep.com.br/ws/'+ cep + '/json/?callback=meu_callback';

                //Insere script no documento e carrega o conteúdo.
                document.body.appendChild(script);

            } //end if.
            else {
                //cep é inválido.
                limpa_formulário_cep();
                alert("Formato de CEP inválido.");
            }
        } //end if.
        else {
            //cep sem valor, limpa formulário.
            limpa_formulário_cep();
        }
    };

## Tópicos do desafio : 
        * O Associado se autentica pelo seu CPF :bookmark: e sua placa :oncoming_automobile:
        * O Associado visualiza todos os seus dados mas só pode alterar o endereço.

Foi muito divertido para mim esta experiência, gostaria de repetir, caso tenha alguma sugestão de melhoria, ou desafios, me mantenhoa disposição.    
