# Exercício 1

## Processamento de Arquivos

### Parte A — Processamento assíncrono

Foi realizada a leitura e o processamento dos arquivos de forma assíncrona.

### Resultado

**Tempo total:** `0.1969 segundos`

| Arquivo        | Linhas | Palavras |
| -------------- | -----: | -------: |
| arquivo_01.txt |  50000 |   491682 |
| arquivo_02.txt |  50000 |   491661 |
| arquivo_03.txt |  50000 |   491828 |
| arquivo_04.txt |  50000 |   491565 |
| arquivo_05.txt |  50000 |   491223 |
| arquivo_06.txt |  50000 |   491616 |
| arquivo_07.txt |  50000 |   492012 |
| arquivo_08.txt |  50000 |   491616 |
| arquivo_09.txt |  50000 |   491744 |
| arquivo_10.txt |  50000 |   491288 |
| arquivo_11.txt |  50000 |   491573 |
| arquivo_12.txt |  50000 |   491934 |

Todos os arquivos possuem `50000` linhas.

---

## Parte B — Processamento paralelo

Foi implementada uma segunda solução em C utilizando **OpenMP**, distribuindo o processamento dos arquivos entre diferentes threads.

Foram realizadas execuções utilizando 1, 2, 4 e 8 threads.

### Resultados

| Threads | Tempo (segundos) | Speedup |
| ------: | ---------------: | ------: |
|       1 |         0.098537 |    1.00 |
|       2 |         0.066809 |    1.48 |
|       4 |         0.066362 |    1.48 |
|       8 |         0.069416 |    1.42 |

### Comandos utilizados

```bash
OMP_NUM_THREADS=1 ./programa
OMP_NUM_THREADS=2 ./programa
OMP_NUM_THREADS=4 ./programa
OMP_NUM_THREADS=8 ./programa
```

### Cálculo do Speedup

A fórmula utilizada foi:

```text
Speedup = tempo com 1 thread / tempo com N threads
```

#### 1 thread

```text
0.098537 / 0.098537 = 1.00
```

#### 2 threads

```text
0.098537 / 0.066809 ≈ 1.48
```

#### 4 threads

```text
0.098537 / 0.066362 ≈ 1.48
```

#### 8 threads

```text
0.098537 / 0.069416 ≈ 1.42
```
## Respostas

### 1. Qual é a diferença entre assincronismo e paralelismo?

**Assincronismo** permite que uma tarefa seja interrompida enquanto aguarda alguma operação, como a leitura de um arquivo, permitindo que outra tarefa seja executada nesse intervalo.

**Paralelismo** ocorre quando diferentes tarefas são executadas simultaneamente, geralmente utilizando múltiplos núcleos ou threads do processador.

### 2. O uso de asyncio significa necessariamente que duas instruções estão sendo executadas simultaneamente?

Não. O `asyncio` utiliza principalmente um modelo de execução assíncrona baseado em um event loop. Enquanto uma tarefa está aguardando uma operação, outra pode ser executada, mas isso não significa necessariamente que as duas instruções estejam sendo executadas ao mesmo tempo em diferentes núcleos.

### 3. O uso de mais threads sempre torna o programa mais rápido?

Não. O aumento do número de threads pode melhorar o desempenho até determinado ponto, mas também pode aumentar o custo de gerenciamento das threads e gerar disputa por recursos, como o acesso ao disco.

No experimento realizado, 2 e 4 threads apresentaram tempos muito próximos, enquanto 8 threads apresentou um tempo um pouco maior.

### 4. Em qual configuração você encontrou o melhor desempenho?

Na **Parte B**, o menor tempo obtido foi com **4 threads**, com aproximadamente **0,066362 segundos**.

Os resultados foram:

| Threads |    Tempo (s) |
| ------: | -----------: |
|       1 |     0,098537 |
|       2 |     0,066809 |
|       4 | **0,066362** |
|       8 |     0,069416 |

Portanto, considerando as execuções realizadas, a configuração com **4 threads apresentou o menor tempo de execução**.
