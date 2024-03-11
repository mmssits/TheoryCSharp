O C# é uma linguagem fortemente tipada. Isso significa que, como regra, devemos declarar o tipo de uma variável que indica o valor que ela armazenará.

Além disso, uma das características entre tipos de dados e variáveis no C# é que, se uma variável nasce de um tipo, morre desse tipo. 
Existe uma interferência nisso através da conversão de variáveis, futuramente veremos que, apesar de podermos "trocar" o tipo de uma variável, essa característica continua sendo respeitada. No entanto, isso é papo para um outro momento.

Quando falamos de tipos de dados, podemos dividir eles em duas categorias: **dados por valor** e **dados por referência**.

# Tipos por Valor

Os tipos por valor armazenam seu conteúdo dentro de sua própria alocação de memória. 
Ou seja, quando criamos uma variável, estamos criando um espaço de alocação na memória para guardar uma informação. Quando essa variável se trata de um tipo por valor, o dado é armazenado diretamente nessa alocação de memória.

Em C# temos diferentes tipos de dados por valor, sejam os tipos simples/primitivos, enums, structs ou Nullables. A seguir, vamos definir melhor esses tipos.

#### Tipos simples

No quadro a seguir, iremos conhecer os tipos primitivos ou value types, bem como seus tamanhos e possíveis valor que podem armazenar quando declarado junto a uma variável:

![[Pasted image 20240306154145.png]]
*Créditos: Alura - Artigo: Variáveis e tipos primitivos.*

Para um breve resumo e descrição dessa tabela, podemos determinar da seguinte forma:

- **Tipo char:** Representa um único caractere Unicode.
- **Tipo bool**: Representa um valor booleano, sendo verdadeiro ou falso.
- **Tipos numéricos:**
	- **int:** Representa números inteiros, positivos ou negativos, sem parte decimal.
	- **float:** Representa números de pontos flutuante de precisão simples.
	- **double:** Representa números de ponto flutuante de precisão dupla.
	- **decimal:** Representa números decimais de alta precisão para cálculos financeiros e monetários.
	- **byte**, **short**, **long** e sua variações: Representam inteiros de diferentes tamanhos e faixas de valores.

#### Enums

Enums, também chamados de enumerados, são constantes fortemente tipadas que por sua vez devem sempre ser estáticas. Ou seja, não é possível nem preciso acessar os seus valores instanciando um objeto, somente utilizar a classe em que está contigo e seu nome.

Se você ainda não teve seu primeiro contato com orientação a objetos, a questão de instanciação de objeto pode ter ficado confusa. No entanto, como os enums NÃO necessitam dessa instanciação, podemos entender seu funcionamento pelo seguinte exemplo:

Primeiro, criamos o enum dentro de uma classe:

```csharp

public class ExemploEnum
{
	enum NomesEnum
	{
		"Maria",
		"João",
		"Ana", 
		"Lucas"
	};
}
```

Em seguida, chamamos o enum através do nome da classe e nome do enum onde ele deve ser executado:

```csharp
class Program
{
	static void Main(string[] args)
	{
		var valor = ExemploEnum.NomesEnum.Maria;

		Console.WriteLine(valor);
	}
}
```

Em breve, abordaremos sobre esse tipo em específico mais afundo.

#### Structs

Structs, ou estruturas, são um estrutura de dados que podem conter membros de dados e membros de função, sendo muito semelhantes a classes. 
Podemos, inclusive, definir elas como uma miniatura de uma classe, tendo suas próprias variáveis e métodos, mas geralmente sendo usadas para apresentar dados simples e em pequenas unidades.

Podemos definir uma estrutura através de sua palavra-chave ==struct==, como no exemplo a seguir:

```csharp
public struct PontoCartesiano
{
	public int eixoX;
	public int eixoY;
}
```

#### Nullable

O tipo nullable, como seu próprio nome sugere, consiste na atribuição de um valor nulo. Usar esse tipo de dado pode ser útil em situações onde você precisa lidar com valores que podem ser desconhecidos ou indefinidos, podendo realizar isso de maneira segura e fácil no código.

A definição de uma variável do tipo nullable é seguida sempre com o sinal de interrogação, como a seguir:

```csharp
int? idade = null;
```


# Tipos por referência

Os tipos de referência, quando declarados junto a uma variável, gravam na alocação de memória a referência (endereço) ao dado em questão. 

Como alocamos o endereço do dado e não o dados em si, não há cópia dos dados para a variável. Em vez disso, cria-se uma segunda cópia de referência.

Essas variáveis não ficam armazenada na parte *stack* da memória, como os tipos de valor, mas sim na parte *heap*, isso faz com que, quando uma variável desse tipo não é mais usada, ela possa ser marcada para o Garbage Collector (coletor de lixo). No entanto, abordaremos esse conceito de memória e descarte mais a frente.

Em C# temos diferentes tipos de dados por referência, como classes, strings e outros tipos mais complexos, que serão abordados mais a frente. A seguir, vamos definir melhor esses tipos.

#### Classes

Os tipos classe são como modelos usados para criar objetos. Assim, podemos pensar em uma classe como um conjunto de instruções sobre como construir algo.

Vamos supor que possuímos uma classe Carro, e nela temos as características (propriedades) do carro e suas ações/comportamentos (métodos). Os objetos a partir dele são, basicamente, modelos específicos de carro, que compartilham as mesmas características (portas, cor, marca) e comportamentos (ligar o carro, ligar o som, acelerar).

#### Strings

Podemos definir uma string como um conjunto de caracteres, sejam numeros, letras ou especiais, que serão armazenadas como texto. Uma string é extremamente útil para lidar com toda e qualquer informação que condiz com um texto.

