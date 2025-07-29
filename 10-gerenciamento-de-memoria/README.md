# Gestão de Memória: Comparação entre C# e Python

| Característica            | C# (.NET)                                         | Python                                      |
|---------------------------|---------------------------------------------------|----------------------------------------------|
| **Alocação de Memória**   | Automática (heap e stack)                         | Automática (heap)                           |
| **Coleta de Lixo**        | Sim (Garbage Collector generacional)              | Sim (Garbage Collector + contagem de ref.)  |
| **Liberação Manual**      | Possível com `Dispose()` e `using` (IDisposable)  | Não (mas pode usar `del` para refs)         |
| **Gerenciamento de Objetos** | Objetos desalocados quando não referenciados   | Objetos desalocados quando ref. = 0         |
| **Gerenciamento de Recursos** | `using` para liberar recursos não gerenciados | Context manager (`with`) para recursos      |
| **Fragmentação de Memória** | Minimizada pelo GC generacional                 | Pode ocorrer, mas o GC tenta minimizar      |
| **Controle do Programador** | Parcial (pode forçar GC, mas não recomendado)   | Muito limitado, GC é automático             |
| **Desempenho**            | Alto, otimizado para aplicações empresariais      | Menor que C#, mas suficiente para scripts   |

---

## Resumo

- **C#**: Usa Garbage Collector generacional, permite algum controle manual de recursos (com `Dispose` e `using`), e é otimizado para aplicações de alta performance.
- **Python**: Usa coleta de lixo baseada em contagem de referências e um GC complementar para ciclos, com gerenciamento totalmente automático e pouca intervenção do programador.

**Exemplo prático em C#:**
```csharp
using (var arquivo = new StreamWriter("exemplo.txt"))
{
    arquivo.WriteLine("Olá, mundo!");
} // O arquivo é fechado automaticamente aqui
```

**Exemplo prático em Python:**
```python
with open("exemplo.txt", "w") as arquivo:
    arquivo.write("Olá, mundo!")
# O arquivo é fechado automaticamente aqui
```