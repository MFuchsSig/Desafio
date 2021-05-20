# DesafioJavascript
Ao começar a desenvolver que tinha como proposta desenvolver em Javascript receber o nome e o cpf de um pessoa, fazendo uma validação onde não poderia ser vazio tanto o nome quanto o cpf e depois alocar isso em uma tabela. Desenvolver código com a equipe foi bem interessante, devido a nossa interação. O desafio em si foi bacana tivemos algumas dificuldades e em grupo resolvemos todas.

### HTML
 Nessa parte do código em HTML fizemos a criação dos campos que ficam na tabela, passando uma validação onde o cpf só pode ter 11 números , uma vez que o mesmo foi inserido como tipo "number" e também fizemos a inserção do nome por um tipo "text" e criamos através de um input o botão que ao clicar ira mandar para a tabela os dados inseridos.
 
```
<h2>Desafio Javascript</h2>
<p>CPF: <input type="number" id="txtCPF" name="txtName" maxlength="11" />
NOME: <input type="text" id="txtNome" name="txtNome" />
<input type="button" id="buttonAdicionar" value="Adicionar" onclick="AdicionarLinha()" />


<table id="tabelaClientes" name="tabelaClientes" border="1">
<tr>
<td><strong>CPF</strong></td>
<td><strong>NOME</strong></td>
<td><strong>REMOVER</strong></td>
</tr>
</table> 
  
  ```
  
  ## Javascript
Nessa parte do código passamos uma variável que armazenaria a tabela dentro de um array e para pegar o valor que o usuário digitou transformamos o cpf e o nome em variáveis.

```

 var arrayTabela = [];
 function AdicionarLinha() {
 var cpf = document.getElementById("txtCPF").value;
 var nome = document.getElementById("txtNome").value; 
		 
		 
```		 
  
A seguir criamos uma condição "IF" para a validação onde se o nome ou o cpf estiver vazio ele entra na condição e imprime para o usuário através do "Window.alert" que está vazio, se o nome e o cpf não estiverem vazios ele entra no "Else" que vai armazenar dentro da tabela os mesmos respectivamente.
                    
```	    

if (nome.trim() == "" || cpf == "")
{
	window.alert("Insira um valor possivel!");
} 
else
{
var tabela = 
{
"id": arrayTabela.length,
"nome": nome,
"cpf": cpf
}

```
      
No decorrer do código, criamos uma variável chamada “javalidou” essa variável é responsável por limpar a caixa de texto inserida no HTML onde o usuário escreve o nome e o cpf para a tabela. Neste caso inicializamos a variável com o valor “False” para que a mesma não limpe os campos sem antes a validação de nome e cpf estejam corretas.	

```

var jaValidou = false;
			
```			
			
Adiante, utilizamos um looping “For” para fazer uma verificação onde o mesmo compara se o nome ou o cpf que já está inserido não e o mesmo que o usuário esta tendo inserir novamente evitando repetições. 

```

for (let i = 0; i < (arrayTabela.length - 1); i++) {
	var cpfTabela = tabela.cpf;
	var cpfArray = arrayTabela[i].cpf;
	var nomeTabela = tabela.nome;
	var nomeArray = arrayTabela[i].nome;
	
```				
				
Adiante, utilizamos um looping “For” para fazer uma verificação onde o mesmo compara se o nome ou o cpf que já está inserido não e o mesmo que o usuário esta tendo inserir novamente evitando repetições. No entanto se houver repetições o programa compara através da condição “if” emitindo um alerta “Já existe um nome com esse CPF cadastrado!” para o cpf e para o nome “Ja existe um nome como esse cadastrado!”.				

```

if (cpfTabela == cpfArray)
{
	jaValidou = true;
	window.alert("Ja existe um nome com esse CPF cadastrado!");
	arrayTabela.pop();
	break;
}
if (nomeTabela == nomeArray)
{
	jaValidou = true;
	window.alert("Ja existe um nome como esse cadastrado!");
	arrayTabela.pop();
} 

```				

 Se o nome e o cpf não estiverem dentro do array ele irá cair em um "IF" onde "javalidou" é falso desta forma, irá fazer a limpeza da caixa de texto tanto do cpf quanto do nome.

```

 if (!jaValidou)
{
	document.getElementById("txtNome").value = "";
	document.getElementById("txtCPF").value = "";
} 
							   
 ```
							       
Em seguida criamos uma função para remover uma linha da tabela, onde através do "ID" dentro do array faz a retirada de dentro do vetor e também da tabela visualizada pelo usuário.	

```

function RemoverLinha(idLinha) {
arrayTabela.splice(idLinha, 1);
document.getElementById("linhaRemover" + idLinha).remove();
console.log(arrayTabela);
document.getElementById("tabelaClientes").innerHTML = constroiTabela();
}

```

 Função criada para a construção da tabela.

```
function constroiTabela() {
var tabelaScript = "<tr>" +                                              
	"<td>" +
	"<strong>" +
	"CPF" +
	"</strong>" +
	"</td>" +
	"<td>" +
	"<strong>" +
	"NOME" +
	"</strong>" +
	"</td>" +
	"<td>" +
	"<strong>" +
	"REMOVER" +
	"<strong>" +
	"</td>" +
	"</tr>";
	
```	
	
Finalizando o código criamos uma estrutura de repetição que tem como função a construção da tabela com o nome e o cpf recebidos no array e a criação do botão remover dentro da tabela.	
	
```			
for (let i = 0; i < arrayTabela.length; i++) {
tabelaScript += "<tr id='linhaRemover" + i + "'>" +											                     
"<td>" +
arrayTabela[i].cpf +
"</td>" +
"<td>" +
arrayTabela[i].nome +
"</td>" +
"<td>" +
"<input type='button' id='buttonRemover" + i + "' value='Remover' onclick='RemoverLinha(" + i + ")' />" +
"</td>"
"</tr>";
}

return tabelaScript;
```
