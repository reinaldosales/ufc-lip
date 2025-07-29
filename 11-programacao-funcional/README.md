# Exemplo Funcional em C#: Soma Recursiva de Transações PIX Acima de R$100

Vamos supor que tem uma lista de valores de transações PIX e quero somar apenas os valores acima de R$100, usando funções de alta ordem e recursão.

```csharp
using System;
using System.Linq;

class Program
{
    // Função recursiva para somar elementos de um array
    static double SomaRecursiva(double[] lista, int indice = 0)
    {
        if (indice >= lista.Length)
            return 0;
        return lista[indice] + SomaRecursiva(lista, indice + 1);
    }

    static void Main()
    {
        double[] transacoes = { 50, 200, 120, 80, 300, 90 };

        // Função de alta ordem: Where filtra os valores acima de 100
        var filtradas = transacoes.Where(valor => valor > 100).ToArray();

        double resultado = SomaRecursiva(filtradas);

        Console.WriteLine($"Soma dos valores PIX acima de R$100: {resultado}");
    }
}
```

---

- `Where(valor => valor > 100)` é uma função de alta ordem que filtra os valores.
- `SomaRecursiva` soma os elementos do array de forma recursiva.
- Não usamos laços tradicionais, apenas composição de funções e recursão, seguindo o estilo funcional.