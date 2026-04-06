# 🔍 Busca Sequencial em C

Este diretório contém a implementação do algoritmo de **busca sequencial (linear)** em linguagem C, utilizando um dataset de nomes de filmes armazenados em arquivo `.txt`.

---

## 🧠 O que é Busca Sequencial?

A **busca sequencial** percorre os elementos de uma lista **um a um**, comparando cada item com o valor desejado até encontrar o alvo ou chegar ao final.

### 📌 Complexidade

* **Melhor caso:** O(1) → elemento na primeira posição
* **Caso médio:** O(n/2)
* **Pior caso:** O(n) → elemento no final ou inexistente

---

## 📂 Funcionamento do Código

### 1. 📥 Leitura do Dataset

O programa abre o arquivo:

```c
FILE *dataset = fopen("../../data/movies_name.txt", "r");
```

Depois:

* Lê linha por linha com `fgets`
* Remove o caractere `\n`
* Aloca memória dinamicamente com `malloc`
* Armazena cada nome em um vetor de strings

---

### 2. 🧱 Estrutura de Dados

```c
char *lista[MAX_FILMES];
```

* Cada posição do vetor aponta para uma string
* Cada string contém o nome de um filme
* O tamanho da memória é ajustado dinamicamente para cada nome

---

### 3. 🔎 Execução da Busca

O usuário informa o nome do filme:

```c
fgets(busca, 100, stdin);
```

A busca percorre o vetor sequencialmente:

```c
for (int j = 0; j < total_filmes; j++) {
    comparacoes++;

    if (strcmp(lista[j], busca) == 0) {
        encontrado = 1;
        posicao = j;
        break;
    }
}
```

* `strcmp` compara strings
* Quando retorna `0`, significa que encontrou
* O `break` interrompe a busca imediatamente

---

## 📊 Métrica Utilizada

### 🔢 Número de Comparações

A única métrica utilizada agora é:

```c
long long comparacoes;
```

Ela representa:

👉 quantas vezes o algoritmo precisou comparar strings até encontrar (ou não) o elemento

---

### 📈 Interpretação

| Situação       | Comparações esperadas |
| -------------- | --------------------- |
| Início         | poucas                |
| Meio           | médias                |
| Final          | muitas                |
| Não encontrado | máximas (n)           |

---

## 📊 Base Ordenada vs Desordenada

### 🔹 Diferença no código

A única alteração é o arquivo utilizado:

```c
// Base desordenada
FILE *dataset = fopen("../../data/movies_name.txt", "r");

// Base ordenada
FILE *dataset = fopen("../../data/movies_ordenado.txt", "r");
```

---

### ⚠️ Impacto na Busca Sequencial

👉 A ordenação **não melhora o algoritmo**

Isso porque a busca sequencial:

* sempre percorre elemento por elemento
* não utiliza nenhuma informação sobre ordenação

---

### 🧠 Efeito prático

A ordenação pode:

* ✔️ Melhorar o desempenho → se o elemento estiver mais no início
* ❌ Piorar o desempenho → se o elemento for deslocado para o final

---

## 🔬 Observações

* O número de comparações é uma métrica **determinística**
* Diferente do tempo, não sofre interferência do sistema
* Representa diretamente a complexidade do algoritmo

---

## 📌 Conclusão

A busca sequencial é:

* simples de implementar
* não depende de ordenação
* possui custo linear O(n)

👉 Seu desempenho depende exclusivamente da posição do elemento na lista