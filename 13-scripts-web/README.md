# Exemplo de Script para Automação: Relatório de Transações PIX em Python

## Contexto
Supondo que eu receba um arquivo CSV com transações PIX e precisa gerar um relatório com o total de transações e o valor total movimentado.

## Script em Python

```python
import csv

total_transacoes = 0
valor_total = 0.0

with open('transacoes.csv', newline='', encoding='utf-8') as csvfile:
    leitor = csv.DictReader(csvfile)
    for linha in leitor:
        total_transacoes += 1
        valor_total += float(linha['valor'])

print(f"Total de transações: {total_transacoes}")
print(f"Valor total movimentado: R$ {valor_total:.2f}")
```

---

O script irá ler o arquivo, contar as transações e somar os valores, mostrando um resumo no final.