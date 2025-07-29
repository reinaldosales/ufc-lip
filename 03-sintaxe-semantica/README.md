# Definição da Gramática

```
programa     → declaracao*
declaracao   → transacao | consulta
transacao    → 'pix' VALOR 'para' CHAVE_PIX
consulta     → 'consultar' 'saldo' | 'consultar' 'extrato'
VALOR        → DIGITO+ ('.' DIGITO{2})?
CHAVE_PIX    → EMAIL | TELEFONE | CPF
EMAIL        → LETRA (LETRA | DIGITO | '_')* '@' DOMINIO
TELEFONE     → '+' DIGITO{2} DIGITO{2} DIGITO{8,9}
CPF          → DIGITO{11}
DIGITO       → [0-9]
LETRA        → [a-zA-Z]
DOMINIO      → (LETRA | DIGITO)+ ('.' (LETRA | DIGITO)+)*
```

## Exemplo de Código MiniPIX

```minipix
pix 100.00 para joao@email.com
consultar saldo
pix 50.50 para +5585999998888
consultar extrato
pix 1000.00 para 12345678900
```

## Análise Léxica

Exemplo de tokens gerados para a primeira linha:
```text
<TOKEN_PIX, "pix">
<TOKEN_VALOR, "100.00">
<TOKEN_PARA, "para">
<TOKEN_EMAIL, "joao@email.com">
```

## Tabela de Tokens

| Token          | Padrão Regex          | Exemplo        |
|----------------|----------------------|----------------|
| TOKEN_PIX      | "pix"               | pix            |
| TOKEN_PARA     | "para"              | para           |
| TOKEN_VALOR    | [0-9]+(\.[0-9]{2})? | 100.00        |
| TOKEN_EMAIL    | [a-zA-Z][\w]*@...   | joao@email.com|
| TOKEN_TELEFONE | \+[0-9]{13}         | +5585999998888|
| TOKEN_CPF      | [0-9]{11}           | 12345678900   |
| TOKEN_CONSULTAR| "consultar"         | consultar      |
| TOKEN_SALDO    | "saldo"             | saldo         |
| TOKEN_EXTRATO  | "extrato"           | extrato       |

## Exemplo de Análise Léxica Completa

```python
Entrada: "pix 50.50 para +5585999998888"

Saída (tokens):
1. <TOKEN_PIX, "pix">
2. <TOKEN_VALOR, "50.50">
3. <TOKEN_PARA, "para">
4. <TOKEN_TELEFONE, "+5585999998888">
```

## Tratamento de Erros Léxicos

```text
Entrada inválida: "pix abc.xy para joao@email.com"
Erro: "abc.xy" não é um valor monetário válido (TOKEN_VALOR esperado)
```