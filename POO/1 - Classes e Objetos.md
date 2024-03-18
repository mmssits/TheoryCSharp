
A programação orientada a objetos é um paradigma de programação que se baseia no conceito de "objetos". Ou seja, no lugar de focar apenas em funções e procedimentos, organizamos o código em torno de entidades (classes) que podem conter dados e ações que operam esses dados.  

Mas, afinal, qual a diferença de objetos e classes?

Quando falamos de classes, estamos nos referindo a uma estrutura ou modelo que irá originar um objeto. Nela, temos definidas os membros (atributos/propriedades) e comportamentos (métodos) que o objeto poderá desempenhar.

Já um objeto, é uma instância de uma classe, ou seja, a realização do modelo. Basicamente, é uma entidade real, alocada na memória do computador, que possui características específicas (atributos) e ações específicas (métodos) de acordo com a definição da classe que o mesmo pertence.

##### Como declaramos uma classe?

Para a declaração de uma classe, devemos seguir algumas regras básicas:

- É necessário o uso da palavra chave ***class***
- O nome de uma classe deve começar com letra maiúsculas
- O nome de uma classe não deve conter espaços em branco ou caracteres especiais, exceto sublinhado.
- De preferência, utilizar substantivos
- Não denominar nomes no plural

É possível ainda, criar mais de uma classe no mesmo arquivo. No entanto, é uma boa prática que cada arquivo contenha uma classe.

Abaixo, temos um exemplo de declaração da classe Carro, com os conceitos que vimos até o momento.

```csharp
public class Carro
{
	// Propriedades/Membros
	public string Modelo;
	public string Cor;

	// Métodos
	public void Ligar()
	{
		// comando para ligar carro
	}
}
```

Se tratando de classes, ainda temos um método especial usado para inicializar um objeto assim que ele é criado. Chamamos esse método especial de **construtor**, onde ele recebe o mesmo nome da classe e não possui nenhum tipo de retorno.

```csharp
public class Carro
{
	// Propriedades/Membros
	public string Modelo;
	public string Cor;

	public Carro(string modelo, string cor)
	{
		Modelo = modelo;
		Cor = cor;
	}
}
```


##### Agora, como podemos criar um objeto?

Um objeto é criado a partir da instanciação de uma classe, e a palavra-chave principal que desencadeia a responsabilidade desse ação é o operador ***new***. 

```csharp
Carro carroExemplo = new Carro();
```

Essa criação aloca o objeto carroExemplo na memória e chama o construtor da classe, caso exista. 

Com o objeto carroExemplo instanciado, agora podemos acessar e manipular suas propriedades e métodos específicos, da seguinte forma:

```csharp
// Definindo propriedades do objeto
carroExemplo.Modelo = "Celta";
carroExemplo.Cor = "Preto";

// Executando método/comportamento do objeto
carroExemplo.Ligar();
```

O acesso às propriedades e métodos de uma classe podem variar de acordo com seus modificadores de acesso. No entanto, isso será abordado no conceito de um dos pilares de orientação a objetos, nomeado como encapsulamento.

##### Vamos falar de métodos?

Todos os métodos podem ser caracterizados em duas diferentes formas: os que retornam uma informação e os que não retornam uma informação.

**Para métodos que não retornam nada**, utilizamos a palavra ‘void’ (traduzido como vazio), como a seguir:

```csharp
public class Carro{
	
	public string Modelo;
	public string Cor;
	public bool LuzesInternas = false;

	public void AbrirPorta() {
			LuzesInternas = true;
		}

	public void FecharPorta() {
			LuzesInternas = false;
		}
}
```

**Para métodos que retornam um informação**, temos o seguinte exemplo:

```csharp
public class Carro{
	
	public string Modelo;
	public string Cor;
	public bool LuzesInternas = false;

	public string AcenderFarolAut() {
		return "Médio";
	}
}
```

É importante ressaltar que, todo método que retornar um valor deve conter a palavra-chave return, com o valor ou variável a ser retornada atendendo o tipo especificado na declaração do mesmo método.


