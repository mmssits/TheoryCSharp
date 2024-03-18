
O Encapsulamento é um dos pilares da Programação Orientada a Objetos e consiste em agrupar dados (propriedades e métodos) que fazem sentido estar juntos, ocultando também detalhes de um componente de uma classe e fornecendo uma interface pública para interagir com ela.

Em resumo, ele permite que os dados de uma classe sejam protegidos e acessados apenas por meio de métodos específicos da classe. Isso ajuda a garantir que os dados sejam manipulados de forma controlada e segura, reduzindo a possibilidade de erros e aumentando a segurança e a integridade do código.

# Modificadores de Acesso

Os modificadores de acesso controlam a visibilidade dos membros e comportamentos de uma classe. Alguns exemplos são:

- **Public**: é o modificador mais permissivo e indica que o membro é acessível de qualquer lugar, dentro ou fora da classe.
- **Private**: indica que o membro é acessível somente dentro da classe onde foi declarado. Ou seja, não pode ser acessado de fora da classe, nem mesmo por subclasses.
- **Protected**: é semelhante ao modificador private, mas permite que o membro seja acessado também também pelas subclasses. Ou seja, membros protegidos são visíveis dentro da classe onde foram declarados e em suas subclasses, mas não podem ser acessados de fora das mesmas.
- **Internal**: indica que o membro é acessível somente dentro do mesmo assembly (um arquivo de código-fonte compilado em conjunto). Assim, ele pode ser acessado por qualquer classe dentro do mesmo assembly.

# Getters x Setters

As propriedades de encapsulamento, conhecidas como getters e setters, são métodos especiais que permitem acessar e modificar valores de atributos de uma classe de maneira controlada. 

**Getter (Obter)**:

O getter é um método usado para obter o valor de um atributo privado da classe, e possui algumas regras:
- Geralmente possui a palavra-chave **get**
- Sua função é retornar o valor atual do atributo

```csharp
public class MinhaClasse
{
    private int meuAtributo;

    public int MeuAtributo
    {
        get
        {
            return meuAtributo;
        }
    }
}
```


**Setter (Definir)**:

O setter é um método usado para definir o valor de um atributo privado da classe, e também possui algumas regras:
- Geralmente possui a palavra-chave **set**
- Sua função é definir o valor do atributo com base no valor passado como parâmetro.

```csharp
public class MinhaClasse
{
    private int meuAtributo;

    public int MeuAtributo
    {
        get
        {
            return meuAtributo;
        }
        set
        {
	        meuAtributo = value;
        }
    }
}
```

A palavra-chave **value** é usada no setter para representar o valor que está sendo atribuído ao atributo. Assim, o valor passado como parâmetro para o setter é armazenado nessa mesma variável.

É muito comum declararmos propriedades autoimplementadas, utilizando esses métodos get e set da seguinte forma:

```csharp
public class Usuario
{
	public string Nome {get; set;}
}
```

No exemplo acima, Nome é uma propriedade autoimplementada. Assim, o compilador do C# cria automaticamente um campo privado para armazenar o valor da propriedade. Resumidamente, é como se estivesse sido escrito um código para um campo privado e métodos **get** e **set** correspondentes. No entanto, isso é feito de forma transparente e simplificada.





