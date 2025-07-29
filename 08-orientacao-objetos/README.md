# Exemplo de Hierarquia de Classes: Transportes

```csharp
// Classe base
public class Transporte
{
    public string Marca { get; set; }
    public int Ano { get; set; }

    public virtual void Mover()
    {
        Console.WriteLine("O transporte está se movendo.");
    }
}

// Subclasse Carro
public class Carro : Transporte
{
    public int NumeroDePortas { get; set; }

    public override void Mover()
    {
        Console.WriteLine("O carro está andando na estrada.");
    }
}

// Subclasse Bicicleta
public class Bicicleta : Transporte
{
    public bool TemMarcha { get; set; }

    public override void Mover()
    {
        Console.WriteLine("A bicicleta está pedalando na ciclovia.");
    }
}

// Exemplo de uso
class Programa
{
    static void Main()
    {
        Carro carro = new Carro { Marca = "Toyota", Ano = 2020, NumeroDePortas = 4 };
        Bicicleta bike = new Bicicleta { Marca = "Caloi", Ano = 2022, TemMarcha = true };

        carro.Mover(); // Saída: O carro está andando na estrada.
        bike.Mover();  // Saída: A bicicleta está pedalando na ciclovia.
    }
}
```

---

- `Transporte` é a classe base.
- `Carro` e `Bicicleta` herdam de `Transporte` e sobrescrevem o método `Mover`.
- Cada subclasse pode ter propriedades