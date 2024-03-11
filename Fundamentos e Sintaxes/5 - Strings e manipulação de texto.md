
Em C#, uma string é um objeto que representa texto imutável como uma sequência de caracteres Unicode (letras, dígitos, pontuação, etc.). As instâncias de uma String são definidas através de aspas duplas `""`, como abaixo:

```csharp
string fruit = "Apple";
```

Várias strings podem ser concatenadas (adicionadas). A maneira mais simples de conseguir isso é concatenando com o operador `+`:

```csharp
string name = "Thayna";

Console.WriteLine("Hello, " + name + "!");

// Impressão do console: Hello, Thayna!

```

Novas atualizações do .Net, no entanto, possibilitaram uma nova concatenação através de ***interpolação de strings***, onde a strings possui como prefixo o símbolo de dólar `$` e usa variáveis em seu interior através de chaves `{}`.

```csharp
string name = "Thayna";

Console.WriteLine($"Hello, {name}!")

// Impressão do console: Hello, Thayna!
```

# Métodos de String

As strings são manipuladas chamando seus métodos, já que são um objeto variável de uma classe também nomeada String. Isso pode ter ficado meio confuso, mas, basicamente, existe uma classe nativa no C# que recebe o nome de String, onde, quando declaramos uma variável do tipo string, estamos basicamente instanciando um objeto dessa mesma classe.

Assim, quando queremos manipular caracteres ou partes de uma string, utilizamos métodos dessa primeira classe, onde cada método possui um comportamento específico.

Vamos conhecer alguns dos métodos mais utilizados na manipulação de string.

#### Lenght

Esse método é responsável por retornar a quantidade de caracteres em uma string.

```csharp
string texto = "Hello, world!"; 
int comprimento = texto.Length; // comprimento agora é igual a 13
```

#### Substring

Retorna uma parte da string com base no índice inicial e na quantidade de caracteres a retornar, ambos passados respectivamente no parâmetro
do método.

```csharp
string texto = "Hello, world!"; 
string parte = texto.Substring(7, 5); // parte agora é "world"
```

#### ToUpper e ToLower

Converte todos os caracteres da string para maiúsculas ou minúsculas.

```csharp
string texto = "Hello, world!"; 
string maiusculas = texto.ToUpper(); // maiusculas agora é "HELLO, WORLD!"
string minusculas = texto.ToLower(); // minusculas agora é "hello, world!"
```

#### Replace

Substitui todas as ocorrências de um caractere especificado e substitui por outra.

```csharp
string texto = "Hello, world!"; 
string novoTexto = texto.Replace("Hello", "Hi"); // novoTexto agora é "Hi, world!"
```

#### Trim

Remove os espaços em branco do início e do final da string.

```csharp
string texto = " Hello, world! "; 
string textoSemEspacos = texto.Trim(); // textoSemEspacos agora é "Hello, world!"
```

#### Split

Divide a string em partes com base em um caractere delimitador, criando um array com seu resultado.

```csharp
string texto = "apple,banana,orange";
string[] frutas = texto.Split(','); // frutas agora é um array contendo {"apple", "banana", "orange"}
```

Além desses métodos, existem muitos outros que podem ser visualizados na documentação oficial da Microsoft:

> https://learn.microsoft.com/pt-br/dotnet/api/system.string?view=net-8.0

