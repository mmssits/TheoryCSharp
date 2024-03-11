# Coleções

Em C#, uma coleção é uma estrutura de dados que permite armazenar e manipular grupos de elementos relacionados. 
Existem vários tipos de coleções disponíveis em C#, cada uma com suas próprias características e finalidades. Neste artigo, iremos abordar cada uma delas e exemplos de seu uso.

# Arrays

Um array é uma coleção ordenada de elementos do mesmo tipo. Ele tem um tamanho fixo que é definido quando o array é criado e não pode ser alterado depois. Além disso, seus elementos são usados acessando um índice numérico, representando sua posição no array


**Declaração do Array:**

```csharp
// tipo[] nomeArray = new tipo[] {valores}
string[] nomes = new string[] {"Ana", "Beatriz", "Flora"}

// tipo[] nomeArray = new tipo[3]
string[] nomes = new string[3];
```


**Atribuição do Array:**

```csharp
nomes[0] = "Ana";
nomes[1] = "Beatriz";
nomes[2] = "Flora";
```


**Impressão de Array:**

```csharp
foreach(var nome in nomes){
	Console.WriteLine(nome);	
}

/* Impressão do console:
Ana
Beatriz
Flora
*/
```


**Operações com Arrays:**

As operações com arrays ocorrem a partir de métodos. Abaixo, vamos destacar alguns dos métodos mais utilizados:

- IndexOf -> indica índice da primeira ocorrência da informação passada nos parâmetros.
- LasIndexOf ->indica índice da última ocorrência da informação passada nos parâmetros.
- Reverse -> inverte ordem do array.
- Resize -> redefine o tamanho do array.
- Sort -> ordena o array
- Copy -> realiza cópia de elementos do array
- Clone -> clona um array
- Clear -> limpa itens de um array

# Listas (List)

Uma lista é uma coleção dinâmica de elementos do mesmo tipo. Ao contrário dos arrays, o tamanho de uma lista pode ser alternado dinamicamente durante a execução do programa. 

**Declaração de lista:**

```csharp
// List<tipo> nomeLista = new List<tipo> {valores}
List<string> nomes = new List<string> {"Ana", "Beatriz", "Flora"}
// List<tipo> nomeLista = new List<tipo>()
List<string> nomes = new List<string>();
```


**Impressão de lista:**

```csharp
foreach(var nome in nomes)
{
	Console.WriteLine(nome);
}

/* Impressão do console:
Ana
Beatriz
Flora
*/

// Também é possível percorrer uma lista pelo for, mas não é tão performático.
```


**Atribuição da Lista:**

```csharp
nomes.Add("Carla");
```


**Operações em Listas:**

Assim como com os arrays, as operações em listas também se dão com diferentes métodos que podem ser usados. Veremos os mais usados a seguir:

- First -> acessa primeiro item da lista
- Last -> acessa último item da lista
- FirstOrDefault -> acessa primeiro item da lista ou retorna null caso não haja
- Reverse -> inverte ordem da lista
- RemoveAt -> remove pelo índice (posição) do item
- Sort -> ordena os itens da lista
- GetRange -> obtém/copia faixa de valores/itens de uma lista para outra

Além disso, podemos tanto criar listas de objetos (classes instanciadas) como listas apenas de leitura.

As listas apenas de leitura são generics e podem ser declaradas da seguinte forma:

```csharp
var readList = new ReadOnlyCollection<string>(nomes);
```

Acima, criamos uma lista de leitura de um exemplo de lista que já havíamos apresentado nos exemplos anteriores. No entanto, quando se trata de uma lista de leitura, usamos um IList no lugar de List. Além disso, é necessário um método de atribuição dentro da classe raiz.
Essa generic é utilizada com intuito de proteger as informações internas da classe de origem ou da lista que está sendo utilizadas, nesse caso, a lista nomes.

# Conjuntos (Sets)

Um conjunto é uma coleção que armazena elementos únicos, ou seja, não permite elementos duplicados. Além disso, eles não são mantidos em ordem específicas. Esses conjuntos oferecem métodos para adicionar, remover e verificar as existência de elementos.

**Declaração de Sets:**

```csharp
ISet<string> nomes = new HashSet<string>();
```


**Atribuição de Sets:**

```csharp
nomes.Add("Ana");
nomes.Add("Beatriz");
nomes.Add("Flora");
```


**Imprimindo Sets:**

```csharp
foreach(var nome in nomes)
{
	Console.WriteLine(nome)
}

/* Impressão do console:
Ana
Beatriz
Flora
*/
```

A principal diferença entre uma List e um Set, é que os Sets possuem mais agilidade quando se trata de consultas de itens. Além disso, HashSets possuem maior escabilidade, ou seja, desempenho com alta quantidade de itens.

Em falar de memória, o HashSet acaba ocupando mais espaço, perdendo para os List nesse quesito.

Quando se trata de conjuntos, temos algumas diferenças na relação de igualdade de elementos, através dos métodos Equals e GetHashCode;

- **Equals:** Este método é usado para comparar se dois objetos são iguais. No contexto de conjuntos, ele é usado para determinar se dois objetos são iguais em termos de conteúdo, ou seja, se contêm os mesmos elementos. Se você tiver dois conjuntos e quiser verificar se eles são iguais em termos de elementos, é possível usar o método "Set.Equals()".
- **GetHashCode:** Este método retorna um valor numérico (hash code) que representa exclusivamente um objeto. No contexto de conjuntos, o "**GetHashCode**" é usado para calcular a posição de um objeto dentro de um conjunto. Cada objeto em um conjunto tem um hash code exclusivo e o conjunto usa esses hash codes para determinar a posição de cada objeto.

Resumidamente, Equals é usado para comparar o conteúdo de dois conjuntos e determinar se são iguais, enquanto GetHashCode é usado internamente pelo conjunto para calcular a posição dos objetos dentro dele. Ambos desempenham papéis importantes ao lidar com conjuntos, garantindo que os elementos sejam armazenados e comparados corretamente.

# Dicionários

dicionários permitem associar uma chave a um valor, tonando buscas por chaves específicas mais eficientes.

**Declaração de Dicionários:**

```csharp
iDictionary<int, string> nomes = new Dictionary<int, string>();

int -> chave
string -> valor
```


**Atribuição de Dicionário:**

```csharp
nomes.Add(1, "Ana");
nomes.Add(2, "Beatriz");
nomes.Add(3, "Flora");
```


**Varredura/Busca em dicionário**

```csharp
// primeira maneira - não muito segura nem de boa prática
nomes[int] // int = chave a ser buscada

// segunda maneira - melhor prática
nomes.TryGetValue(int, out null) // int = chave que irá tentar procurar, null = oq será retornado caso não ache a chave
```

É importante destacarmos, ainda, que dicionários não permitem que haja chaves duplicadas ou repetidas. No entanto é possível substituir o valor de uma chave da seguinte forma:

```csharp
nomes[1] = "Jorge"
```

Assim como os HashSets, o dicionário também possui o código de dispersão para sua busca de valores de maneira interna.
