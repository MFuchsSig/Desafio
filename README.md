# DesafioJavascript
Ao começar a desenvolver que tinha como proposta desenvolver em Javascript receber o nome e o cpf de um pessoa, fazendo uma validação onde não poderia ser vazio tanto o nome quanto o cpf e depois alocar isso em uma tabela. Desenvolver código com a equipe foi bem interessante, devido a nossa interação. O desafio em si foi bacana tivemos algumas dificuldades e em grupo resolvemos todas.

### HTML
#### Nessa parte do código em HTML fizemos a criação dos campos que ficam na tabela, passando uma validação onde o cpf só pode ter 11 números , uma vez que o mesmo foi inserido como tipo "number" e também fizemos a inserção do nome por um tipo "text" e criamos através de um input o botão que ao clicar ira mandar para a tabela os dados inseridos.

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
  
  ## Javascript
 #### Nesta parte do código passamos uma variável que armazenaria a tabela dentro de um array e para pegar o valor que o usuário digitou transformamos o cpf e o nome em variáveis.
  		 var arrayTabela = [];
   		 function AdicionarLinha() {
		 var cpf = document.getElementById("txtCPF").value;
		 var nome = document.getElementById("txtNome").value; 
  <p>
#### Nessa parte do código criamos um condição "IF" para a validação onde se o nome ou o cpf estiver vazio ele entra na condição e imprime para o usuário através do "Window.alert" que está vazio, se o nome e o cpf não estiverem vazio ele entra no "Else" que vai armazenar dentro da tabela o nome e o cpf.
    
    
                        if (nome.trim() == "" || cpf == "") {
			window.alert("Insira um valor possivel!");
		}
		else {
			var tabela =
			{
				"id": arrayTabela.length,
				"nome": nome,
				"cpf": cpf
			} 
      
#### Continuando criamos uma variável chamada "javalidou" onde ela irá limpar a caixa de escrita se não estiver inserido na tabela um nome ou cpf igual onde o "for" faz essa validação pegando o nome que está para ser inserido na tabela e compara com o array, se for igual , ele irá testar no primeiro "if" se o cpf for igual, se for igual ele irá imprimir para o usuário que já "existe um cpf como esse cadastrado" e não irá limpar o a caixa de texto devido a variável “javalidou” retornar verdadeiro se o cpf for diferente ele passa para a próxima condição que irá verificar se o nome é igual ao que está dentro do array, se for igual ele irá imprimir uma mensagem dizendo "esse nome já está cadastrado" e também não irá limpar a caixa de texto.
	
			arrayTabela.push(tabela);
			console.log(arrayTabela);
			console.log(arrayTabela.length);
			var jaValidou = false;
			for (let i = 0; i < (arrayTabela.length - 1); i++) {
				var cpfTabela = tabela.cpf;
				var cpfArray = arrayTabela[i].cpf;
				var nomeTabela = tabela.nome;
				var nomeArray = arrayTabela[i].nome;
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
				

#### Se o nome e o cpf não estiverem dentro do array ai ele irá cair em um "IF" onde já validou é falso e irá fazer a limpeza da caixa de texto tanto do cpf quanto do nome.

			 if (!jaValido
			{
				document.getElementById("txtNome").value = "";
				document.getElementById("txtCPF").value = "";
			} 
							   
#### Criação da tabela 
			document.getElementById("tabelaClientes").innerHTML = constroiTabela();	
							       
#### Função criada para remover uma linha da tabela, onde através do "ID" dentro do array apaga tanto dentro do array quanto na impressão da tabela.	
							       
		function RemoverLinha(idLinha) {
		arrayTabela.splice(idLinha, 1);
		document.getElementById("linhaRemover" + idLinha).remove();
		console.log(arrayTabela);
		document.getElementById("tabelaClientes").innerHTML = constroiTabela();
	}
##### Função criada para a construção da tabela 
							       
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
#### Criação de um "for" que irá construir a tabela com o nome e o cpf recebidos no array e a criação do botão remover dentro da tabela.						      
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
