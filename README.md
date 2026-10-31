# Pong AI – NEAT

Uma implementação do jogo Pong utilizando Inteligência Artificial, Python e **NEAT (NeuroEvolution of Augmenting Topologies)**. O projeto explora a aplicação de redes neurais evolutivas em um ambiente competitivo, permitindo que agentes autônomos aprendam a jogar Pong por meio de partidas simuladas.

## Sobre o Projeto

Este projeto foi desenvolvido como um experimento prático para aprofundar os estudos em Inteligência Artificial, Machine Learning e algoritmos evolutivos.

O jogo utiliza redes neurais para controlar automaticamente as raquetes dos jogadores. Durante o treinamento, dois agentes controlados por redes neurais competem entre si, e seus desempenhos são avaliados com base na quantidade de rebatidas realizadas.

A partir dessas avaliações, o algoritmo NEAT conduz o processo evolutivo, permitindo que as redes neurais sejam aprimoradas ao longo das gerações.

Além do treinamento, o projeto também possui um modo de teste no qual é possível jogar contra uma rede neural previamente treinada.

## Tecnologias Utilizadas

- **Python:** Linguagem principal utilizada no desenvolvimento.
- **Pygame:** Biblioteca responsável pela implementação do jogo, renderização e interação.
- **NEAT-Python:** Biblioteca utilizada para implementar o algoritmo de neuroevolução.
- **Pickle:** Utilizado para serializar e armazenar a melhor rede neural encontrada durante o treinamento.

## Como Funciona

O projeto utiliza o algoritmo NEAT para evoluir redes neurais capazes de controlar as raquetes de maneira autônoma.

### Entradas da Rede Neural

Cada rede neural recebe três valores como entrada:

| Entrada | Descrição |
|---|---|
| Posição Y da raquete | Posição vertical atual da raquete controlada pela rede. |
| Posição Y da bola | Posição vertical atual da bola no ambiente. |
| Distância horizontal até a bola | Distância horizontal absoluta entre a raquete e a bola. |

### Saídas da Rede Neural

A rede neural produz três possíveis decisões para controlar a raquete:

| Saída | Ação |
|---|---|
| 0 | Permanecer na posição atual. |
| 1 | Movimentar a raquete para cima. |
| 2 | Movimentar a raquete para baixo. |

A decisão é determinada pela saída de maior valor produzida pela rede neural.

### Treinamento e Fitness

O treinamento acontece por meio de partidas entre dois agentes controlados por redes neurais independentes.

A função de fitness utiliza a quantidade de rebatidas realizadas por cada jogador como critério de avaliação:

- Cada rebatida contribui para aumentar o fitness do respectivo indivíduo.
- As partidas são encerradas quando um jogador marca um ponto ou quando o limite de rebatidas estabelecido é atingido.
- O desempenho dos agentes é utilizado pelo NEAT para conduzir a evolução das redes neurais.

## Modos de Execução

O projeto possui dois modos principais:

### Treinamento da IA

Executa partidas entre dois agentes autônomos, cada um controlado por uma rede neural independente.

O processo utiliza o algoritmo NEAT para avaliar os indivíduos e evoluir suas redes neurais ao longo das gerações.

### Jogador contra IA

Permite testar uma rede neural previamente treinada em uma partida contra um jogador humano.

Nesse modo, o jogador controla a raquete esquerda utilizando as teclas:

- **W:** Movimentar para cima.
- **S:** Movimentar para baixo.

A raquete direita é controlada automaticamente pela rede neural carregada.

## Salvamento e Recuperação do Treinamento

O projeto utiliza arquivos de serialização para preservar os resultados do treinamento:

- **Checkpoints:** Permitem recuperar o estado de uma população durante o processo evolutivo.
- **best.pickle:** Armazena a melhor rede neural encontrada, permitindo utilizá-la posteriormente no modo de teste.

Esse mecanismo possibilita continuar um treinamento interrompido e testar os resultados sem precisar executar todo o processo novamente.

## Estrutura do Projeto

```text
.
├── pong.py
├── main.py
├── config.txt
├── best.pickle
└── neat-checkpoint-22
```

## Como Executar

### Pré-requisitos

- Python 3.x
- pip

### Instalação

1. Clone o repositório:

```bash
git clone <url-do-repositorio>
cd <nome-do-repositorio>
```

2. Instale as dependências:

```bash
pip install pygame neat-python
```

3. Execute o projeto:

```bash
python main.py
```

Por padrão, o código está configurado para executar o treinamento da IA utilizando um checkpoint existente.

Para alternar entre os modos de execução, utilize as funções disponíveis no final do arquivo `main.py`:

```python
# Treinamento da IA
run_neat(config)

# Jogador contra IA
test_ia(config)
```

**Observação:** Para utilizar o modo de teste, é necessário possuir um arquivo `best.pickle` gerado pelo treinamento. O treinamento também depende da disponibilidade do checkpoint configurado no código, ou de uma população inicial caso seja habilitada a criação de uma nova população.

## Objetivos de Aprendizado

O desenvolvimento deste projeto proporcionou contato prático com os seguintes conceitos:

- Fundamentos de Inteligência Artificial e Machine Learning.
- Redes neurais artificiais aplicadas ao controle de agentes.
- NeuroEvolution of Augmenting Topologies (NEAT).
- Algoritmos genéticos e computação evolutiva.
- Funções de fitness e avaliação de desempenho.
- Competição entre agentes autônomos.
- Persistência e recuperação de modelos treinados.

## Considerações Finais

Este projeto representa um experimento de aplicação de Inteligência Artificial em um ambiente competitivo, explorando a utilização de redes neurais evolutivas para desenvolver agentes capazes de controlar um jogo de maneira autônoma.

A implementação permitiu explorar conceitos de neuroevolução, avaliação de desempenho e tomada de decisão, utilizando partidas simuladas como ambiente de treinamento.