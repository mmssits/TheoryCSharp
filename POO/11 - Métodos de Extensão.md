A partir da versão 3.0 do C#, foi disponibilizado a funcionalidade Extension Methods (traduzidos como métodos de extensão), que permite adicionar novos métodos para tipos existentes, sem a necessidade de criar um novo tipo derivado, recompilação ou até modificação do método original.

Os Extension Methods são métodos estáticos que podem ser chamados como se fosse métodos originais de um tipo de dado ou uma classe pré-existente. 

Suponhamos que necessitamos realizar uma fórmula ou cálculo em nosso projeto. Assim, esse cálculo é utilizado em diferentes partes do projeto, podendo ser reaproveitado, e é na necessidade de reaproveitar um bloco de código que realiza uma ação utilizada muitas vezes que usamos essas **extension methods**.

#### Criação de Extension Method

Para a criação de uma Extension Method, ela deve ser *static* e envolvida por uma classe também *static*, como no exemplo a seguir:

```csharp
public static class CalculadoraExtensions
{
	public static int SomarExtension(this int numero1, int numero2)
	{
		return numero1 + numero2;
	}
}
```

É uma boa prática incluir o sufixo Extension(s) ao fim do nome tanto da classe como do método de extensão, por questão de organização principalmente. 

Quando utilizamos o primeiro parâmetro com a palavra-chave *this*, estamos informando que qualquer número int pode chamar este método, contanto que ele esteja aplicado no ambiente. Como na chamada do método de extensão no seguinte exemplo:

```csharp
public class Program
{
	static void Main(string[] args)
	{
		int numero1 = 10;
		int numero2 = 20;

		int resultado = numero1.SomarExtension(numero2);
	}
}
```

Quando não utilizamos o *this*, no entanto, devemos usar a chamada informando o nome da classe que a Extension Method está contida e nome do método desejado, como por exemplo:

```csharp
// Classe e metodo de extensão
public static class CalculadoraExtensions
{
	public static int SomarExtension(int numero1, int numero2)
	{
		return numero1 + numero2;
	}
}

// Classe de chamada
public class Program
{
	static void Main(string[] args)
	{
		int numero1 = 10;
		int numero2 = 20;

		int resultado = CalculadoraExtensions.SomarExtension(numero1, numero2);
	}
}
```

