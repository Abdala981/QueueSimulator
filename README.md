# Simulador de Sistema de Filas (Discreto)

Este repositório contém a implementação de um simulador de eventos discretos voltado para a análise de sistemas de filas. O projeto foi desenvolvido como parte de uma atividade acadêmica para a disciplina de Modelagem e Simulação.

O objetivo principal é simular o comportamento de clientes e caixas ao longo do tempo, coletando métricas de desempenho e realizando análises estatísticas baseadas em intervalos de confiança.

## Descrição do Projeto

O código implementa a lógica de chegada e atendimento de clientes, utilizando geração de números pseudoaleatórios para determinar os tipos de clientes e os tempos de serviço. O simulador não utiliza a biblioteca `random` nativa do Python para a geração dos números, implementando manualmente um Gerador Congruencial Linear (LCG) para fins didáticos e de controle da semente (seed).

O script executa três cenários distintos em sequência:
1.  **Simulação com Servidor Único:** Um único caixa atendendo a demanda.
2.  **Simulação com Múltiplos Servidores (n caixas):** Expansão para 4 caixas com lógica de alocação para o servidor desocupado ou com menor tempo de término.
3.  **Versão Refatorada:** Uma implementação otimizada e limpa do cenário de múltiplos caixas.

## Funcionalidades e Métricas

O sistema calcula as seguintes métricas de desempenho para avaliar a eficiência da fila:

* **Tempo Médio na Fila:** Tempo que o cliente aguarda até ser atendido.
* **Tempo Médio de Serviço:** Duração do atendimento no caixa.
* **Tempo Médio no Sistema:** Soma do tempo de fila e tempo de serviço.
* **Taxa de Ociosidade:** Tempo médio em que os caixas ficam sem clientes.

Para garantir a validade estatística, a simulação é rodada múltiplas vezes (499 sementes diferentes) para calcular:
* Média das médias.
* Desvio padrão.
* Intervalos de confiança (95%).

## Detalhes Técnicos

* **Linguagem:** Python 3.
* **Bibliotecas:** `numpy` (para manipulação de arrays e cálculos matemáticos) e `math`.
* **Geração de Números Aleatórios:** Método Congruencial Linear (LCG) com parâmetros a = 16807, c = 0, M = 2^31 - 1.
* **Distribuição de Probabilidade:** Utiliza o método da Transformada Inversa para gerar tempos de chegada e serviço baseados em uma distribuição logarítmica.

## Pré-requisitos

Para executar este projeto, é necessário ter o Python instalado e a biblioteca `numpy`.

```bash
pip install numpy
```

Como Executar
O arquivo principal contém as três versões do simulador em sequência. Para rodar a simulação e visualizar os resultados no console:

```Bash
python simulador.py
```
Exemplo de Saída
Ao final da execução, o programa exibirá os dados estatísticos consolidados:

```
Média das médias do tempo gasto na fila = [Valor]
Média das médias do tempo de serviço = [Valor]
Média das médias do tempo despendido no sistema = [Valor]
Média das médias do tempo ocioso do sistema = [Valor]

Desvio padrão do tempo gasto na fila = [Valor]
...

Intervalo de confiança para o tempo gasto na fila = [Min, Max]
...
