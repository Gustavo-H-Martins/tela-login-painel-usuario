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

## Tópicos do desafio : 
* O Associado se autentica pelo seu CPF :bookmark: e sua placa :oncoming_automobile:
* O Associado visualiza todos os seus dados mas só pode alterar o endereço.
Foi muito divertido para mim esta experiência, gostaria de repetir, caso tenha alguma sugestão de melhoria, ou desafios, me mantenhoa disposição.    
