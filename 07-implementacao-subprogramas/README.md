# Pilha de Chamadas em Recursão (Exemplo em C#)

## Exemplo Recursivo: Fatorial

```csharp
using System;

class Program
{
    static int Fatorial(int n)
    {
        if (n == 0)
            return 1;
        else
            return n * Fatorial(n - 1);
    }

    static void Main()
    {
        int resultado = Fatorial(3);
        Console.WriteLine(resultado); // Saída: 6
    }
}
```

## Pilha de Chamadas (Stack)

Ao chamar `Fatorial(3)`, a pilha de chamadas fica assim:

| Topo da Pilha | Chamada Atual         | Estado da Pilha                |
|---------------|----------------------|--------------------------------|
| 1             | Fatorial(0) retorna 1| Fatorial(3) → Fatorial(2) → Fatorial(1) → **Fatorial(0)** |
| 2             | Fatorial(1) retorna 1*1| Fatorial(3) → Fatorial(2) → **Fatorial(1)** |
| 3             | Fatorial(2) retorna 2*1| Fatorial(3) → **Fatorial(2)** |
| 4             | Fatorial(3) retorna 3*2| **Fatorial(3)** |

## Explicação Passo a Passo

1. `Fatorial(3)` chama `Fatorial(2)`  
   Pilha: [Fatorial(3)]
2. `Fatorial(2)` chama `Fatorial(1)`  
   Pilha: [Fatorial(3), Fatorial(2)]
3. `Fatorial(1)` chama `Fatorial(0)`  
   Pilha: [Fatorial(3), Fatorial(2), Fatorial(1)]
4. `Fatorial(0)` retorna 1  
   Pilha: [Fatorial(3), Fatorial(2), Fatorial(1), Fatorial(0)]
5. Cada chamada retorna multiplicando o valor:
   - Fatorial(1): 1 * 1 = 1
   - Fatorial(2): 2 * 1 = 2
   - Fatorial(3): 3 * 2 = 6

## Visualização em Diagrama

```mermaid
graph TD
    A[Fatorial(3)] --> B[Fatorial(2)]
    B --> C[Fatorial(1)]
    C --> D[Fatorial(0)]
    D --> E[retorna 1]
    C --> F[retorna 1*1]
    B --> G[retorna 2*1]
    A --> H[retorna 3*2]
```

---

- Cada chamada recursiva empilha uma nova função na pilha de chamadas.
- Quando chega ao caso base (`n == 0`), as funções começam a ser desempilhadas, retornando os valores.
- A pilha de chamadas é fundamental para entender o funcionamento da recursão e evitar estouro de pilha (stack overflow) em casos de recursão