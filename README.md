# DesafioJavascript
Ao começar a desenvolver que tinha como proposta desenvolver em Javascript receber o nome e o cpf de um pessoa, fazendo uma validação onde nao poderia ser vazio tanto o nome quanto o cpf e depois alocar isso em uma tabela. Desenvolver codigo com a equipe foi bem interessante, devido a nossoa intereção. O desafio em si foi bacana tivemos algumas dificuldade e em grupo resolvemos todas <p>
### HTML
  Nessa parte do codigo em HTML fizemos a criação dos campos que ficam na tabela, passando uma validação onde o cpf so pode ter 11 números , uma vez que o mesmo foi insiserido como tipo "number" e tambem fizemos a insercção do nome por um tipo "text" e criamos atravez de um imput o botção que ao clicar ira mandar para a tabela os dados inseridos.<p>
`<h2>Desafio Javascript</h2>
	<p>CPF: <input type="number" id="txtCPF" name="txtName" maxlength="11" />
		NOME: <input type="text" id="txtNome" name="txtNome" />
		<input type="button" id="buttonAdicionar" value="Adicionar" onclick="AdicionarLinha()" />
	</p> `
  
  `<table id="tabelaClientes" name="tabelaClientes" border="1">
		<tr>
			<td><strong>CPF</strong></td>
			<td><strong>NOME</strong></td>
			<td><strong>REMOVER</strong></td>
		</tr>
	</table> `
  
  ## Javascript
 Nesta parte do código passamos uma variável que armazenaria a tabela dentro de um array e para pegar o valor que o usuário digitou transformamos o cpf e o nome em variáveis.<p>
  ` var arrayTabela = [];
    function AdicionarLinha() {
		var cpf = document.getElementById("txtCPF").value;
		var nome = document.getElementById("txtNome").value; `
  <p>
Nessa parte do código criamos um condição "IF" para a validação onde se o nome ou o cpf estiver vazio ele entra na condição e imprime para o usuário através do	"Window.alert" que está vazio, se o nome e o cpf não estiverem vazio ele entra no "Else" que vai armazenar dentro da tabela o nome e o cpf.
    <p>
    
 `if (nome.trim() == "" || cpf == "") {
			window.alert("Insira um valor possivel!");
		}
		else {
			var tabela =
			{
				"id": arrayTabela.length,
				"nome": nome,
				"cpf": cpf
			} `
      <p>
       Continuando criamos uma variavel chamada "javalidou" onde ela ira limpar a caixa de escrita se não estiver inserido na tabela um nome ou cpf igual onde o "for" faz essa validação pegando o nome que esta para ser inserido na tabela e compara com o array, se for igual , ele ira testar no primeiro "if" se o cpf for igual, se for igual ele ira imprimir para o usuario que ja "existe um cpf como esse cadastrado" e nao ira limpar o a caixa de texto devido a variavel ja validou retornar verdadeiro se o cpf for diferente ele passa para a proxima condição que ira verificar se o nome é igual ao que esta dentro do array, se for igual ele ira imprirmir uma mensagem dizendo "esse nome ja esta cadstrado" e tambem não ira limpar a caixa de texto, se o nome e o cpf 
       <p>
			`arrayTabela.push(tabela);
			console.log(arrayTabela);
			console.log(arrayTabela.length);
			var jaValidou = false;
			for (let i = 0; i < (arrayTabela.length - 1); i++) {
				var cpfTabela = tabela.cpf;
				var cpfArray = arrayTabela[i].cpf;
				var nomeTabela = tabela.nome;
				var nomeArray = arrayTabela[i].nome;
				if (cpfTabela == cpfArray) {
					jaValidou = true;
					window.alert("Ja existe um nome com esse CPF cadastrado!");
					arrayTabela.pop();
					break;
				}
				if (nomeTabela == nomeArray) {
					jaValidou = true;
					window.alert("Ja existe um nome como esse cadastrado!");
					arrayTabela.pop();
				}
			}
			if (!jaValidou) {
				document.getElementById("txtNome").value = "";
				document.getElementById("txtCPF").value = "";
			}
			document.getElementById("tabelaClientes").innerHTML = constroiTabela();
		}
	} `
  
