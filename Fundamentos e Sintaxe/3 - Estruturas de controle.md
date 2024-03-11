# Estruturas de Controle

Assim como em outras linguagens, o C# possui estruturas de controle que possibilitam o controle de fluxo de execução do código. Essas estruturas permitem que você tome decisões e repita terminadas ações conforme uma condição apresentada.

De maneira simples, podemos assumir essas estruturas de controle como um conjunto de instruções que informamos ao nosso programa para que ele siga diferentes caminhos (ações) dependendo de determinada situação (condições).

Essas estruturas de controle são dividas em três tipos: **estruturas de decisão**, **estruturas de repetição** e **estruturas de controle de fluxo**. Neste artigo, veremos mais a fundo cada uma delas.

# Estruturas de decisão

Permitem que o programa faça uma escolha entre dois ou mais caminhos, dependendo de uma determinada condição. Nesse tipo de estrutura, trabalhamos com o bloco de código **if** ou **if/else**.

A seguir, vamos ver um exemplo de uso apenas do bloco if, que indica que uma ação deve ser feita *se, e somente se* a condição for atendida.

**Bloco IF:**

```csharp
double saldo = 100.0;
double valorSaque = 10.0;

if (saldo >= valorSaque)
{			
	saldo = saldo - valorSaque;
	MessageBox.Show("Saque realizado com sucesso");
}
```

No exemplo acima, estabelecemos uma condição para um determinada ação. Ou seja, *se, e somente se,* o valor do saldo for maior ou igual ao valor de saque, o código para sacar o dinheiro é realizado.

A seguir, vamos ver o bloco de código if/else, que indica que, caso a condição não for satisfeita, terá uma outra ação.

**Bloco IF/ELSE:**

```csharp
double saldo = 100.0;
double valorSaque = 10.0;

if (saldo >= valorSaque)
{			
	saldo = saldo - valorSaque;
	MessageBox.Show("Saque realizado com sucesso");
}
else
{
	MessageBox.Show("Saque não pode ser realizado!");
}
```

Nesse exemplo, estabelecemos uma condição para saque como o exemplo anterior, porém, dessa vez, seguimos o conceito de que *se* o valor do saldo for maior ou igual ao valor de saque, ele realiza o código para sacar o dinheiro. *Senão*, ele informa que a ação não pode ser realizada.

É possível, ainda, incluir mais de uma condição, seguindo a ordem de if-elseif:

```csharp
double saldo = 100.0;
double valorSaque = 10.0;

if (saldo > valorSaque)
{			
	saldo = saldo - valorSaque;
	MessageBox.Show("Saque realizado com sucesso");
}
else if (saldo == valorSaque)
{
	saldo = saldo - valorSaque;
	MessageBox.Show("Saque realizado com sucesso, porém valor de saldo foi zerado.");
}
else
{
	MessageBox.Show("Saque não pode ser realizado!");
}
```

Nesse caso, a mensagem de que o saque não pode ser realizado aparece apenas se nenhuma das condições anteriores for satisfeita.

Ainda falando sobre o bloco IF/ELSE, temos o uso do **if ternário**, que consiste, basicamente, em uma abreviação da estrutura IF:

```csharp
double saldo = 100.0;
double valorSaque = 10.0;

// se o saldo for maior ou igual ao valor de saque, diminui o valor, senao retorna o valor de saldo inicial (100.0)

saldo = (saldo >= valorSaque) ? saldo - valorSaque : saldo;

// se o valor for menos que 100.0, informa que o saque foi realizado, senao, informa que o saque nao pode ser realizado
MessageBox.Show((saldo < 100.0) ? "Saque realizado com sucesso" : "Saque não pode ser realizado!");
```

# Estruturas de repetição

As estruturas de repetição permitem que o programa repita um conjunto de instruções várias vezes, até que uma condição seja atendida. Basicamente, criamos um looping que, enquanto a 
condição for atendida, executa o bloco de ação proposto.

Quando falamos de estruturas de repetição, podemos trabalhar com três tipos de estruturas distintas: **While**, **Do While** e **For**.

**Bloco While:**

Executa um bloco de código enquanto uma condição especificada for verdadeira. Por exemplo:

```csharp
int contador = 0;
while(contador < 5)
{
	Console.WriteLine("Contagem: " + contador);
	contador++;
}
```

Nesse caso, enquanto o contador for estritamente menor que 5, o bloco de código é executado.


**Bloco Do While:**

Simular ao loop While, porém a condição é executada após a execução do bloco de código, garantindo que o código seja executado pelo menos uma vez.

```csharp
int contador = 0;

do
{
	Console.WriteLine("Contagem: " + contador);
	contador++;
}
while(contador < 5)
```


**Bloco For:**

Executa um bloco de código em um número específico de vezes, e é muito útil quando sabemos exatamente quantas vezes desejamos repeti-lo.

```csharp
for (int i = 0; i < 5; i++)
{
    Console.WriteLine("Contagem: " + i);
}
```

Declaramos, no próprio bloco for, a variável i como do tipo int e inicializada como zero, e utilizamos a condição de que, enquanto i for estritamente menor que 5, iremos realizar o comando especificado, ou seja, o Console.WriteLine.

Importante notar também que é de extrema importância que essa variável de controle, no caso o i, seja sempre incrementado. Caso contrário, o loop se torna infinito até um determinado momento, onde possa ter o estouro de memória.

Temos, ainda, o tipo de estrutura de repetição **foreach**, que parece muito com o for e é usada para iterar sobre elementos de uma coleção, como arrays, listas, dicionários, entre outros. No entanto, abordaremos melhor sobre ele quando estivermos falando sobre coleções.

# Estrutura de Controle de Fluxo

Por último, mas não menos importantes, temos a estrutura de controle de fluxo através do bloco **switch/case**. Ele permite que você execute diferentes blocos de código com base no valor de uma expressão específica.

Resumidamente, é como uma série de escolhas que o programa decide qual bloco vai ser executado conforme o valor de uma variável passada.

```csharp
int diaSemana = 3; // Exemplo de valor para o dia da semana 

switch (diaSemana) 
{ 
	case 1: 
		Console.WriteLine("Segunda-feira"); 
		break; 
	case 2: 
		Console.WriteLine("Terça-feira"); 
		break; 
	case 3: 
		Console.WriteLine("Quarta-feira"); 
		break; 
	case 4: 
		Console.WriteLine("Quinta-feira"); 
		break; 
	case 5: 
		Console.WriteLine("Sexta-feira"); 
		break; 
	case 6: 
		Console.WriteLine("Sábado"); 
		break; 
	case 7: 
		Console.WriteLine("Domingo"); 
		break; 
	default: 
		Console.WriteLine("Dia inválido"); 
		break; 
}
```

No exemplo acima, dependendo do valor da variável 'diaSemana', o programa decide qual mensagem exibir no console usando a estrutura 'switch/case'. Se 'diaSemana' for 3, por exemplo, a mensagem "Quarta-feira" será exibida. Já caso não corresponda a nenhum dos número dos casos, será exibido "Dia inválido", conforme o caso Default.
