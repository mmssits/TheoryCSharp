
A herança é um dos pilares da orientação a objetos e tem como conceito o relacionamento entre uma classe a outra, onde a classe-filha (também conhecida como subclasse ou classe derivada) herda propriedades e métodos da classe-pai (também conhecida como superclasse ou classe base). Isso evita que informações sejam reescritas, gerando duplicidade de código, e possibilita que novas funcionalidades sejam acrescentadas a classe-filha.

**Sintaxe de Declaração:**

```csharp
public classe Filho : Pai
{
	// métodos e classes
}
```

**Operadores:**

- **Operador :** -> Estende a classe para a classe pai, ou seja, indica que uma classe está herdando de outra
- **Operador base** -> Realiza uma referência direta para o método ou propriedade da classe base, a partir da classe derivada

# Tipos de Herança

A linguagem C# suporta alguns tipos de herança, sendo eles: Herança Simples, Herança Hierárquica, Herança Multinível e Herança Múltipla (implementação).

#### Herança Simples

É o tipo de herança padrão, em que há um classe base e uma classe derivada, como por exemplo:

**Classe base:**

```csharp
public class A
{
	public int Matricula {get; set;}
}
```

**Classe derivada:**

```csharp
public class ContaPoupanca : Conta
{
	public string Nome {get; set;}
}
```


#### Herança Hierárquica

É o tipo de herança em que existem várias classes derivadas de uma classe base. Esse tipo de herança é usado quando há um requisito de um recurso de classe necessário em várias classes, como por exemplo:

**Classe base:**

```csharp
public class A
{
 // propriedades e métodos
}
```

**Classes derivadas:**

```csharp
public class B : A
{
 // propriedades e métodos
}
```

```csharp
public class C : A
{
	// propriedades e métodos
}
```


#### Multinível

É o tipo de herança onde uma classe é derivada de outra classe derivada, realizando uma herança de ***vários níveis***.

**Classe base:**

```csharp
public class A
{
 // propriedades e métodos
}
```

**Classes derivadas:**

```csharp
public class B : A
{
 // propriedades e métodos
}
```

```csharp
public class C : B // classe derivada da classe derivada B
{
	// propriedades e métodos
}
```


#### Múltipla

Apesar do C# não suportar herança múltipla de classes, o que significa que uma classe não pode herdar diretamente de várias classes base. No entanto, o C# utiliza interfaces para alcançar um comportamento semelhante ao da herança múltipla.

As interfaces permitem que uma classe implemente funcionalidades de várias, o que permite que ela adquira comportamentos e características de várias fontes, porém veremos isso de maneira profunda quando falarmos exclusivamente dessa estrutura.

**Declaração de interface:**

```csharp
public interface IExemplo
{
	// propriedades e métodos
}
```

**Declaração de Classe base:**

```csharp
public class ClasseBase
{
	// propriedades e métodos
}
```

**Declaração de classe com herança múltipla:**

```csharp
public class ClasseMultipla : ClasseBase, IExemplo
{
	// propriedades e métodos
}
```

Vale ressaltar que a herança múltipla pode ser com uma classe e uma interface, duas interfaces ou mais. Isso permite que a herança seja ainda mais performática, dando muito mais poder a classes derivadas.


