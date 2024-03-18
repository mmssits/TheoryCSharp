
As **classes abstratas** são um tipo de classe especial que não podem ser instanciadas, apenas herdadas. Dessa forma, elas não podem gerar objetos, mas podem ter subclasses.

Elas são utilizadas quando queremos definir um conjunto de métodos e propriedades comuns que devem ser implementados pelas classes derivadas. Esses métodos que não são implementados são chamados de **métodos abstratos**.

Os **métodos abstratos** são métodos que não possuem corpo, ou seja, não são implementados. Quando declaramos um método como abstrato, estamos, de alguma forma, **obrigando** o desenvolvedor a redefinir esses métodos em todas as subclasses para as quais desejar criar objetos.

É importante destacar, ainda, que uma classe que contém um ou mais métodos abstratos deve ser declarada explicitamente como abstrata. No entanto, essa classe também pode ter métodos concretos (não abstratos).

Além disso, outro detalhe importante sobre as classes abstratas é que, quando herdada por uma classe derivada, o método abstrato existe nessa subclasse ainda que não seja redefinido (implementado) na mesma. Dito isso, como sempre que houver um método abstrato a classe que ele estiver contido deve também ser explicitamente declarada como abstrata. 

A palavra-chave utilizada para a criação dos componentes abstratos é a ***abstract***, e veremos como é sua declaração a seguir:

```csharp
public abstract class ClasseAbstrata
{
	// Métodos concretos
	public void MetodoUm()
	{
		// comandos
	}

	public void MetodoDois()
	{
		// comandos
	}

	// Método abstrato
	public abstract void MetodoTres();
}
```

Conforme o exemplo dado, podemos entender que, ainda que haja somente um método abstratos e todos os outros concretos, a classe deve ser abstrata.

## Classes Abstratas x Interfaces

Apesar de serem parecidas com as interfaces, por serem apenas herdadas e seus métodos serem implementados pelas subclasses, uma diferença significativa quando falamos dessa relação é que a interface continua sendo uma espécie de contrato, que obriga o desenvolvedor a implementar todos os métodos da interface herdade. 

Já as classes abstratas, permitem que apenas os métodos necessários, concretos ou abstratos, sejam implementados pelas classes derivadas.


## Quando usar classes abstratas?

Com essa diferença entre as duas estruturas, podemos definir quando usar cada uma:

Em casos de implementação de apenas alguns métodos pela classe derivada, utilizamos **classes abstratas**. Já em casos de implementação do contrato como um todo, utilizamos **interfaces**.
