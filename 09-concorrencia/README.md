# Diferença entre Threads e Processos

- **Processo:**  
  Um processo é um programa em execução, com seu próprio espaço de memória, recursos e contexto de execução. Cada processo é isolado dos outros, o que garante segurança, mas dificulta a comunicação e consome mais recursos do sistema.

- **Thread:**  
  Uma thread é uma linha de execução dentro de um processo. Todas as threads de um mesmo processo compartilham o mesmo espaço de memória e recursos, tornando a comunicação entre elas mais fácil e eficiente. Threads são mais leves que processos, mas exigem cuidado com sincronização para evitar conflitos de acesso à memória.

---

# Exemplo de Concorrência em C# (Threads)

Simular dois caixas de supermercado atendendo clientes ao mesmo tempo:

```csharp
using System;
using System.Threading;

class Program
{
    static void AtenderClientes(string caixa)
    {
        for (int i = 1; i <= 5; i++)
        {
            Console.WriteLine($"{caixa} está atendendo o cliente {i}");
            Thread.Sleep(500); // Simula tempo de atendimento
        }
    }

    static void Main()
    {
        Thread t1 = new Thread(() => AtenderClientes("Caixa 1"));
        Thread t2 = new Thread(() => AtenderClientes("Caixa 2"));

        t1.Start();
        t2.Start();

        t1.Join();
        t2.Join();

        Console.WriteLine("Todos os clientes foram atendidos!");
    }
}
```

---

- Criada duas threads, cada uma simulando um caixa atendendo clientes.
- Ambas executam ao mesmo tempo, mostrando a concorrência.
- O método `Join()` faz o programa principal esperar as duas threads terminarem antes de exibir a mensagem final.