Interfaces são estruturas que permitem ao desenvolvedor especificar todos os métodos e propriedades que ele deseja que as classes que a implementem disponibilizem. 

Utilizando um interface, é possível separar completamente a definição/assinatura de métodos de suas respectivas implementações, ou seja, de um lado (interface) temos a definição dos mesmos e do outro (classe que implementa a interface), temos a implementação dos mesmos.

Podemos entender uma interface como sendo uma espécie de contrato, ou seja, se uma classe X implementa uma interface Y, logo, Y garante que X disponibilizará todos os métodos definidos em Y. Caso este "contrato" seja quebrado, um erro será gerado.

Essas estruturas são de extrema importância, visto que nos permitem separar o "o que" do "como". Basicamente, ela não se preocupa com a forma que o método está sendo implementado e sim que ele estará disponível a todos os objetos que a implementarem. A Interface descreve a maneira como você deseja que o objeto seja utilizado ao invés da forma como ele foi implementado.

Outra importante justificativa para a utilização de interfaces em seu projetos .Net é que, assim como o Java, o C# não trabalha com herança múltipla entre classes de forma nativa. Implementar este recurso somente é possível através da utilização de interfaces, que você pode consultar melhor no artigo 3, onde falamos de heranças.

### Sintaxe da interface no CSharp

O trabalho com interfaces no C# é bem simples, e segue a seguinte estrutura de sintaxe:

```csharp
interface IExemplo
{
	void MetodoExemplo(string nameExemplo);
}
```

Algumas observações sobre esta estrutura são importantes:
- O corpo do método pode ser substituído por ';'
- O nome da interface deve sempre começar com i maiúsculo.
- Não se deve definir campos em uma interface, nem mesmo estáticos, pois são detalhes exclusivos de implementação de uma classe ou estrutura
- Assim como não deve-se definir campos, também não deve-se definir construtores e destrutores
- Não é possível trabalhar com estruturas aninhadas, como enumeradores, structs, etc
- Interfaces só podem herdar outras interfaces

### Implementando Interfaces

Para implementação de interfaces, é necessário ter uma classe ou struct que herde a interface criada e implemente todos os métodos definidos na interface (já que não deve ter quebra de contrato). Assim, levando-se em consideração o exemplo da interface IExemplo, a implementação pode ocorrer da seguinte forma:

```csharp
public class Exemplo : IExemplo
{
	void IExemplo.MetodoExemplo(string nameExemplo)
	{
		// comandos/comportamento do método de interface para a classe
	}
}
```

Assim como a criação, a implementação da interface requer os seguintes cuidados:

- O nome do método e tipo de retorno devem corresponder exatamente
- Quaisquer parâmetros, incluindo modificadores de palavras chave ref e out, tem que equivaler exatamente
- É uma boa prática se declarar explicitamente o método com o nome da interface (IExemplo.Metodo)
- Todos os métodos que implementam a interface devem ser publicamente acessíveis.

