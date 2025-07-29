# Comparação de Tipagem: Python, JavaScript e C#

## Python (Tipagem Dinâmica e Forte)

```python
# Tipagem dinâmica: o tipo da variável pode mudar em tempo de execução
valor = 100        # int
valor = "cem"      # agora é str

# Tipagem forte: não converte tipos automaticamente
total = "100" + 50     # Erro! Não soma string com inteiro
total = int("100") + 50  # Correto: 150
```

- **Resumo:** O tipo é verificado em tempo de execução. Não permite operações entre tipos incompatíveis sem conversão explícita.

---

## JavaScript (Tipagem Dinâmica e Fraca)

```javascript
// Tipagem dinâmica: tipo pode mudar
let valor = 100;    // number
valor = "cem";      // agora é string

// Tipagem fraca: faz coerção automática de tipos
let total = "100" + 50;   // "10050" (concatena como string)
let soma = "100" - 50;    // 50 (converte string para number)
```

- **Resumo:** O tipo é verificado em tempo de execução. Faz conversões automáticas, o que pode causar bugs difíceis de encontrar.

---

## C# (Tipagem Estática e Forte)

```csharp
// Tipagem estática: tipo definido em tempo de compilação
int valor = 100;
// valor = "cem"; // Erro de compilação: não é possível atribuir string a int

// Tipagem forte: exige conversão explícita
string texto = "100";
int total = int.Parse(texto) + 50; // 150
```

- **Resumo:** O tipo é verificado em tempo de compilação. Não permite operações entre tipos incompatíveis sem conversão explícita.

---

## Tabela Comparativa

| Linguagem   | Tipagem   | Força da Tipagem | Verificação         | Conversão Implícita |
|-------------|-----------|------------------|---------------------|---------------------|
| Python      | Dinâmica  | Forte            | Execução (runtime)  | Não                 |
| JavaScript  | Dinâmica  | Fraca            | Execução (runtime)  | Sim                 |
| C#          | Estática  | Forte            | Compilação          | Não                 |

---

- **Python:** Flexível, mas exige atenção para evitar erros de tipo em tempo de execução.
- **JavaScript:** Muito permissivo, pode causar bugs por conversão automática de tipos.
- **C#:** Mais seguro, pois erros de tipo são detectados antes de rodar o programa.