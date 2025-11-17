# Ordenação de Dígitos e  Algoritmos de Ordenação

## Descrição do Projeto
Este projeto implementa três algoritmos de ordenação em C para ordenar os dígitos do RGM do aluno em ordem crescente. Além disso, os algoritmos são aplicados a vetores aleatórios de diferentes tamanhos para análise de desempenho. 

O objetivo é comparar os métodos em termos de:
- **Número de passos** (comparações e trocas)
- **Tempo de execução** (milissegundos)
- **Escalabilidade e sensibilidade a diferentes casos de entrada**

## Algoritmos Implementados
Escolhi três algoritmos clássicos:

1. **Bubble Sort** – simples, fácil de implementar.  
2. **Insertion Sort** – eficiente para vetores quase ordenados.  
3. **Selection Sort** – fácil de entender, comportamento previsível mesmo com entradas repetidas.

> A escolha foi feita para demonstrar diferenças práticas entre métodos quadráticos em vetores pequenos (RGM) e médios/grandes (vetores aleatórios).

## Como Compilar e Rodar

> No terminal, dentro da pasta `src`:
> ```bash
> gcc -O1 -std=c11 main.c -o ordena
> ```
>  Para rodar o arquivo
> ```bash
> ./ordena
> ```
> O programa solicitará que você digite seu RGM e, em seguida, imprimirá os resultados em formato CSV, incluindo número de passos e tempo de execução.
> O programa imprime os resultados em formato CSV, incluindo número de passos e tempo de execução.

## Política de Contagem de Passos
Comparações: cada if que verifica a ordem entre elementos conta 1 passo.

Trocas/movimentações: cada troca de elementos conta 1 passo.

> Exemplo: se um if leva a uma troca, contam-se 2 passos (1 comparação + 1 troca).

## Métricas de Tempo

Usado clock() da biblioteca <time.h> para medir o tempo de CPU.

Resultado convertido para milissegundos:

> tempo_ms = 1000.0 * (t1 - t0) / CLOCKS_PER_SEC;

## Resultados Médios de 6 Execuções 
| Método    | N      | Caso      | Passos    | Tempo (ms) |
|-----------|--------|-----------|-----------|------------|
| Bubble    | 8      | rgm       | 39        | 0.003      |
| Insertion | 8      | rgm       | 33        | 0.002      |
| Selection | 8      | rgm       | 36        | 0.002      |
| Bubble    | 8      | rgm       | 40        | 0.006      |
| Insertion | 8      | rgm       | 36        | 0.005      |
| Selection | 8      | rgm       | 37        | 0.005      |

>Os números são de 2 RGM diferentes e representam médias de 3 execuções ( métodos ), por RGM.
>
>Passos contam comparações e trocas; tempo em milissegundos.

# Discussão Crítica

Computabilidade: Todos os algoritmos ordenam corretamente os dígitos do RGM e vetores aleatórios.

Escalabilidade: Para N pequeno, a diferença de tempo é desprezível. Para N grande, Bubble e Selection crescem rapidamente (O(n²)), enquanto Insertion se sai um pouco melhor com vetores quase ordenados.

Estabilidade e memória: Insertion é estável, todos são in-place, usando memória mínima.

Conclusão: Para vetores pequenos e médios, Insertion Sort apresenta melhor desempenho prático e estabilidade. Bubble e Selection são úteis para estudo didático de complexidade.
