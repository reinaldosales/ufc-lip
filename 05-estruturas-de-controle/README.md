# Exemplo de Programa em C# com Estruturas de Seleção, Repetição e Controle de Fluxo

## Contexto: Simulador de Caixa Eletrônico Simplificado

O programa permite ao usuário consultar saldo, depositar, sacar e sair. Usa `if`, `switch`, `while` e `break`.

```csharp
using System;

class CaixaEletronico
{
    static void Main()
    {
        double saldo = 500.00;
        while (true)
        {
            Console.WriteLine("\n=== Caixa Eletrônico ===");
            Console.WriteLine("1 - Consultar saldo");
            Console.WriteLine("2 - Depositar");
            Console.WriteLine("3 - Sacar");
            Console.WriteLine("4 - Sair");
            Console.Write("Escolha uma opção: ");
            string opcao = Console.ReadLine();

            switch (opcao)
            {
                case "1":
                    Console.WriteLine($"Seu saldo é R$ {saldo:F2}");
                    break;
                case "2":
                    Console.Write("Valor para depositar: ");
                    double deposito = double.Parse(Console.ReadLine());
                    if (deposito > 0)
                    {
                        saldo += deposito;
                        Console.WriteLine("Depósito realizado!");
                    }
                    else
                    {
                        Console.WriteLine("Valor inválido.");
                    }
                    break;
                case "3":
                    Console.Write("Valor para sacar: ");
                    double saque = double.Parse(Console.ReadLine());
                    if (saque > 0 && saque <= saldo)
                    {
                        saldo -= saque;
                        Console.WriteLine("Saque realizado!");
                    }
                    else
                    {
                        Console.WriteLine("Saldo insuficiente ou valor inválido.");
                    }
                    break;
                case "4":
                    Console.WriteLine("Saindo...");
                    break;
                default:
                    Console.WriteLine("Opção inválida.");
                    break;
            }

            if (opcao == "4")
                break; // Controle de fluxo para sair do loop
        }
    }
}
```
---

- `while (true)`: repetição do menu até o usuário sair
- `switch`: seleção da operação
- `if`: validação de valores e controle de fluxo
- `break`: saída do loop principal e dos casos do switch