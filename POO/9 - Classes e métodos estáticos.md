
As **classes estáticas** são aquelas que contêm apenas membros estáticos, além de que elas não podem ser instanciadas, ou seja, não podemos criar objetos a partir delas. Elas são usadas no caso de não haver comportamento ou dados na classe que depende da identidade do objeto.

Para declararmos uma classe estática, utilizamos a palavra-chave ***static***, como no exemplo abaixo:

```csharp
public static class ClasseEstatica
{
	public static void MetodoEstatico()
	{
		// comandos
	}
}
```

Já quando falamos de **membros estáticos** estamos nos referindo a um método que pertence à classe em vez de instâncias individuas dessa classe. Eles são comumente usados para operações que não dependem do estado de uma instância específica da classe e podem ser invocados em qualquer lugar do código sem criar objetos.

Para declarar um método estático, temos o seguinte exemplo:

```csharp
public class ClasseExemplo
{
	public static void MetodoEstatico()
	{
		// comandos
	}
}
```

Além disso, um ponto importante é que os membros estáticos podem ser acessados diretamente usando o nome da classe, sem a necessidade de criar uma instância da classe, como a seguir:

```csharp
ClasseExemplo.MetodoEstatico();
```


## E quanto a classes seladas?

Apesar de existir uma relação entre classes seladas e classes estáticas, ambas possuem um propósito diferente, bem como comportamentos distintos sobre herança e instância.

Enquanto uma classe estática não pode ser instanciada nem herdada e é usada com a utilidade de agrupar dados que não dependam de um objeto, as classes seladas, apesar de também não serem herdadas, são utilizadas com o princípio de impedir que outras classes herdem da mesma, garantindo a integridade de uma classe que não precisa de extensão.

Podemos declarar uma classe estática utilizando a palavra-chave **sealed**, como a seguir:

```csharp
public sealed class ClasseSelada
{
	// propriedades e métodos
}
```

Um ponto importante sobre a relação entre esses dois tipos de classe é que uma classe estática é sempre selada implicitamente, visto que nunca pode ser herdada, sendo então selada por padrão.

