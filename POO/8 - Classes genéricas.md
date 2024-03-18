
As classes genéricas são conhecidas por serem classes que permitem o uso de tipos genéricos em sua declaração, ou seja, os tipos que são especificados quando a classe é instanciada. Dessa forma, é possível que o código dessa classe possa ser reutilizado com diferentes tipos de dados, proporcionando maior flexibilidade e reutilização de código.

Essa classe pode ser declarada da seguinte forma:

```csharp
public class ListaGenerica<T>
{
	// Implementação da classe
}
```

O parâmetro T utilizado na declaração dessa classe genérica é o que chamamos de ***parâmetro de tipo***, que, conforme a [documentação oficial da Microsoft](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/generics/generic-type-parameters), consiste em um espaço reservado para um tipo específico que um cliente especifica ao criar uma instância do tipo genérico. Ou seja, esse parâmetro condiz com o tipo que será passado ao realizar a instância da classe genérica, como no exemplo a seguir:

```csharp
ListaGenerica<string> nomes = new ListaGenerica<string>();
```

No código exemplificado, o parâmetro de tipo *T* é substituído pelo tipo de dado *string*, criando um objeto da classe genérica ocupando o espaço do tipo reservado.

Além das classes, ainda temos os **campos** e **métodos** genéricos.

Quando falamos de **campos genéricos**, estamos falando de campos que são declarados também com parâmetros de tipo, no entanto, é importante ressaltar que esses campos não podem ser inicializado. Podemos declarar eles da seguinte forma:

```csharp
public class ListaGenerica<T>
{
	public T item;
}
```


Já quando falamos de **métodos genéricos**, seguimos essa mesma linha de raciocínio com os parâmetros de tipo, sendo que agora ele pode estar presente no retorno de um método ou no parâmetro do mesmo, como a seguir:

```csharp
public class ListaGenerica<T>
{
	// Campo genérico
	public T item;

	// Método genérico retornando um parâmetro de tipo
	public T GetItem()
	{
		// implementação do método
	}

	// Método genérico obtendo um parâmetro de tipo como parâmetro
	public void AddItem(int id, T item)
	{
		// implementação do método
	}
}
```

## Restrições Genéricas

O C# ainda possibilita que criemos restrições para os tipos genéricos, sendo uma forma de permitir que apenas sejam aceitos apenas tipos de objetos definidos. 
Para estabelecer essa restrição, utilizamos em conjunto a palavra-chave **where** e o tipo de dado esperado, como por exemplo:

```csharp
public class ListaGenerica<T> where T: class
{
	// implementação da classe genérica
}
```

Assim, definimos uma restrição onde o parâmetro T só pode ser substituído por uma classe. É possível definir ainda outros dados nas restrições, como Enums, Structs, Delegates, entre outros. Para saber mais sobre como definir uma restrição sobre outros tipos, basta conferir a [documentação de restrição da Microsoft](https://learn.microsoft.com/pt-br/dotnet/csharp/language-reference/keywords/where-generic-type-constraint)

## E quando usar Generics?

Seguindo a definição dinâmica dos componentes genéricos, podemos definir que o uso de uma generic se encaixa em várias situações. Mas, especialmente, quando é necessário escrever um código que é flexível e reutilizável com diferentes tipos de dados.

Isso pode ir desde ao criar coleções genéricas, como exemplo de lista genérica que usamos nesse capítulo, até classes utilitárias e algoritmos genéricos, visando o princípio da "generalização" e flexibilidade entre manipulação de diferentes tipos de dados.
