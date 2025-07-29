# Exemplo de Problema Lógico: Relações de Família (Genealogia) em Prolog

Pequeno problema de genealogia, onde é possivel saber quem é avô de quem.

```prolog
% Fatos: relações de pai/mãe
pai(joao, maria).
pai(joao, pedro).
mae(ana, maria).
mae(ana, pedro).
pai(pedro, carla).
mae(julia, carla).

% Regra: X é avô de Z se X é pai de Y e Y é pai ou mãe de Z
avo(X, Z) :- pai(X, Y), pai(Y, Z).
avo(X, Z) :- pai(X, Y), mae(Y, Z).

% Consultas possíveis:
% Quem é avô de carla?
% ?- avo(X, carla).
%
% Resposta esperada:
% X = joao.
```

---

- Os fatos `pai` e `mae` definem as relações básicas.
- A regra `avo` usa variáveis e unificação para deduzir quem é avô de alguém.
- Consultas podem ser feitas para descobrir relações familiares.