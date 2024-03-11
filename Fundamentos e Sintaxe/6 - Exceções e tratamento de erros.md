# Exceções e Tratamento de Erros

Quando falamos de exceções estamos nos referindo a erros ou falha no tratamento de dados que não são o que é esperado pelo trecho de código requerido.

Suponhamos que estamos criando um método que solicita o saque de um determinado valor de uma determinada conta vigente. Esse método deve fazer diferentes verificações do valor de saque digitado para, por fim, informar se a ação pode ser executada ou não. 

Para manipular exceções nesse e outros cenários, usamos o bloco try-catch-finally, onde:

**Try:**
	Bloco composto pelo bloco de código perigoso, ou seja, que pode gerar alguma exceção ao não atender os requisitos necessários para ser executado

**Catch:**
	Bloco que trata a exceção, ou seja, quando alguma exceção pode ser capitada, ele trata a mesma geralmente para comunicá-la ao usuário de maneira personalizada, por um MessageBox, por exemplo.

**Finally:**
	Bloco que finaliza o try-catch, tendo ocorrido uma exceção ou não, geralmente utilizado para limpar cache, fechar arquivos, com intuito de liberar memória, por exemplo.

Agora, vamos colocar em prática o exemplo da ação de um saque, atribuindo o conceito de manipulação de exceções:

```csharp
public void buttonSaca_click(object sender, EventArgs e)
{
	public contaAtual = new Conta();
	string textoValorSaque = valorOperacao.Text;
	double valorSaque = Convert.ToDouble(textoValorSaque);

	// Bloco try-catch
	try 
	{
		contaAtual.Saca(valorSaque);
		MessageBox.Show("Dinheiro liberado");
	}
	catch (ArgumentException e)
	{
		MessageBox.Show("ATENÇÃO: Não é possível sacar um valor negativo!");
	}
	catch (SaldoInsuficienteException e)
	{
		MessageBox.Show("ATENÇÃO: Não é possível sacar valor maior que o saldo em conta!");
	}
}
```

Em primeiro momento, temos o objeto contaAtual instanciado para trabalhar com variáveis que recebem o valor de alguns campos MVC, como do campo de texto chamado valorOperacao. 

Colocando o conceito de manipulação de exceções, usamos a chamada do método Saca, do objeto contaAtual instanceado pela classe Conta, dentro do bloco try, visto que ele pode gerar uma exceção.


```csharp
// Classe principal - Conta

public class Conta
{
	public double Saldo {get; protected set;}

	public void Saca(double valor)
	{
		if (valor < 0.0)
		{
			throw new ArgumentException(); // lança exceção com argumento de exception
		}
		else if (valor > this.Saldo)
		{
			throw new SaldoInsuficienteException(); // lança exceção de classe personalizada herdando a própria classe exception
		}
		else 
		{
			this.Saldo -= valor; // decrementa valor
		}
	}
}
```

No exemplo acima, porém, analisamos agora a classe Conta com seu método Saca, visualizando as exceções que ele pode retornar, em decorrência de algumas condições estabelecidas. 

Temos, no entanto, uma exceção personalizada chamada SaldoInsuficienteException. Essas exceções personalizadas devem, por regra, sempre herdar da classe Exception.

Abaixo, temos um exemplo de uma declaração de uma exception personalizada, herdando da classe Exception.

```csharp
public class SaldoInsuficienteException : Exception
{
	// comandos
}
```
