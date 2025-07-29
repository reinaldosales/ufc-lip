# Exemplos de Passagem de Parâmetros por Valor e por Referência

## C# (por valor e por referência)

```csharp
using System;

class ExemploParametros
{
    // Passagem por valor (não altera o valor original)
    static void IncrementarPorValor(int x)
    {
        x = x + 1;
    }

    // Passagem por referência (altera o valor original)
    static void IncrementarPorReferencia(ref int x)
    {
        x = x + 1;
    }

    static void Main()
    {
        int a = 10;
        int b = 10;

        IncrementarPorValor(a);
        Console.WriteLine($"Após IncrementarPorValor: {a}"); // 10

        IncrementarPorReferencia(ref b);
        Console.WriteLine($"Após IncrementarPorReferencia: {b}"); // 11
    }
}
```

---

## Python (imutáveis por valor, mutáveis por referência)

```python
def incrementar_valor(x):
    x = x + 1  # Não altera o valor original se for int (imutável)

def incrementar_lista(lst):
    lst.append(1)  # Altera a lista original (mutável)

a = 10
incrementar_valor(a)
print(f"Após incrementar_valor: {a}")  # 10

b = [10]
incrementar_lista(b)
print(f"Após incrementar_lista: {b}")   # [10, 1]
```

---

## C++ (por valor e por referência)

```cpp
#include <iostream>
using namespace std;

void incrementarPorValor(int x) {
    x = x + 1;
}

void incrementarPorReferencia(int &x) {
    x = x + 1;
}

int main() {
    int a = 10;
    int b = 10;

    incrementarPorValor(a);
    cout << "Após incrementarPorValor: " << a << endl; // 10

    incrementarPorReferencia(b);
    cout << "Após incrementarPorReferencia: " << b << endl; // 11

    return 0;
}
```

---

- **C#**: Usa `ref` para passagem por referência.
- **Python**: Objetos mutáveis (listas, dicionários) são alterados; imutáveis (int, str) não.
- **C++**: Usa `&` para referência, padrão é por valor.
