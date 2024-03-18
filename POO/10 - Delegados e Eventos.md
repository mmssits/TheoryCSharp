
Em C#, os **delegados** são tipos de dados que fazem referência a métodos. No geral, eles nos permitem que você trate métodos como objetos que podem ser atribuídos a variáveis, passados como parâmetros e chamados dinamicamente.

Para declara-lo, utilizamos como chave o termo **delegate**, como da seguinte forma:

```csharp
public delegate void DelegadoExemplo(string nome);
```

Da mesma forma, para realizar a chamada do delegado, podemos fazer da seguinte forma:

**Vamos usar o seguinte método para gerar a referencia pelo delegate:**

```csharp
public static void MetodoReferenciado(string nome) 
{ 
	Console.WriteLine(nome); 
}
```


**Instanciação de delegate:**

```csharp
DelegadoExemplo delegado = MetodoReferenciado;
delegado("João");
```


## E quanto aos eventos?

Os eventos, por sua vez, são mecanismos usados para notificar outros objetos quando algo de interessante acontece em um objeto. Eles são extremamente usados em aplicativos para permitir a comunicação entre objetos de maneira assíncrona.

Esses eventos seguem um padrão conhecido como Editor/Assinante. Nesse modelo, um objeto (editor) notifica outros objetos (assinantes) quando um evento ocorre.

Para declarar um evento, definimos o delegado que representa a **assinatura dos métodos de tratamento de eventos** e depois um evento que irá usar esse delegado. Por exemplo:

```csharp
public event DelegadoExemplo EventoExemplo;

// onde DelegadoExemplo contém a lista de métodos que serão chamados quando o evento acontecer
```

Assim, podemos ter ter os métodos de tratamento de eventos, que são associados através do operador +=. Isso irá adicionar um método à lista de métodos a serem chamados quando o evento ocorrer. Como o exemplo a seguir:

```csharp
publicador.EventoExemplo += MetodoTratamento;

// publicador é um objeto editor, e MetodoTratamento é o ou um dos métodos de tratamento que irá ser associado ao evento do objeto (EventoExemplo).
```

É importante ressaltar ainda que eventos que não possuem assinantes não podem ser acionados.

Para cancelar uma assinatura, no entanto, podemos apenas decrementar do evento, como da seguinte forma:

```csharp
publicador.EventoExemplo -= MetodoTratamento;
```







