O polimorfismo é a funcionalidade em que objetos relacionados se comportam de maneiras distintas devido a capacidade de invocar métodos comuns que possuem comportamentos específicos para cada tipo de objeto.

Suponhamos que temos classe Animal, que será relacionado pelas seguintes classes: Cachorro e Gato.

```csharp
// Classe original
class Animal {
	
// Método original
	public void EmitirSom(){
		Console.Writeline("Som qualquer");
	}
}

// Classe relacionada
class Cachorro {

}

// Classe relacionada
class Gato {

}
```

No entanto, se formos reproduzir o som para as demais classes e querermos adaptar, devemos aplicar o polimorfismo pela função de **sobrescrita** e determinar o método como **virtual** para reescrevermos com a palavra chave **override**.


```csharp
// Classe original
class Animal {
	
// Método original
	public virtual void EmitirSom(){
		Console.Writeline("Som qualquer");
	}
}

// Classe relacionada
class Cachorro : Animal {
	public override void EmitirSom(){
		Console.Writeline("Auau");
	}
}

// Classe relacionada
class Gato : Animal {
	public override void EmitirSom(){
		Console.Writeline("Miau");
	}
}
```


Além disso, temos também a funcionalidade de **sobrecarga**, que condiz com a possibilidade de um método em ter vários métodos iguais com parâmetros de entrada diferentes. Como nos exemplos a seguir:

```csharp
// IMPLEMENTAÇÃO CORRETA

public void Exemplo(int numero){
	// bloco de código
}

public void Exemplo(int numero, int quantidade){
	// bloco de código
}

public void Exemplo(string name){
	// bloco de código
}

// IMPLEMENTAÇÃO INCORRETA

public void Exemplo(int numero){
	// bloco de código
}

public void Exemplo(int quantidade){
	// bloco de código
}

public void Exemplo(int quilometragem){
	// bloco de código
}
```