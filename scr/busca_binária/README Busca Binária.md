## 🔎 Busca Binária em C

A busca binária é um algoritmo eficiente para encontrar elementos em um conjunto de dados **ordenado**. Diferente da busca sequencial, que percorre todos os elementos, a busca binária reduz o espaço de busca pela metade a cada iteração.

---

## ⚙️ Funcionamento

O algoritmo segue os seguintes passos:

1. Define dois limites:

   * `inicio` (primeira posição do vetor)
   * `fim` (última posição)

2. Calcula o elemento do meio:

   ```c
   int meio = (inicio + fim) / 2;
   ```

3. Compara a chave com o elemento do meio:

   * Se forem iguais → elemento encontrado
   * Se a chave for menor → busca na metade esquerda
   * Se for maior → busca na metade direita

4. Repete o processo até encontrar o elemento ou até o intervalo ser inválido.

---

## 📂 Estrutura do Código

### 📌 Estrutura de dados

```c
typedef struct {
    char nome[TAM_NOME];
} Filme;
```

Armazena os nomes dos filmes lidos do arquivo.

---

### 📌 Alocação dinâmica (Heap)

```c
filmes = malloc(MAX * sizeof(Filme));
```

A alocação é feita na **heap** para evitar estouro de memória (stack overflow), já que o dataset possui mais de 100 mil registros.

---

### 📌 Leitura do arquivo

```c
while (fgets(filmes[total].nome, TAM_NOME, arq) && total < MAX)
```

* Lê cada linha do arquivo
* Remove o `\n`
* Armazena no vetor
* Controla o limite com `MAX`

---

### 📌 Ordenação

```c
qsort(filmes, total, sizeof(Filme), comparar);
```

A busca binária **exige que os dados estejam ordenados**.
Caso o arquivo já esteja ordenado, essa etapa pode ser removida para melhorar o desempenho.

---

### 📌 Função de busca binária

```c
int buscaBinaria(char *chave, long long *comparacoes)
```

* Recebe a chave de busca
* Recebe um ponteiro para contar comparações
* Retorna o índice do elemento ou `-1` se não encontrado

---

### 📌 Contador de comparações

```c
(*comparacoes)++;
```

O código contabiliza:

* Comparação de igualdade (`strcmp`)
* Decisão de direção (esquerda/direita)

---

### 📌 Cálculo da média

```c
for (int i = 0; i < REPETICOES; i++)
```

A busca é executada várias vezes para obter uma média mais estável:

```c
double media = (double) totalComparacoes / REPETICOES;
```

---

## 📊 Métrica de Desempenho

O desempenho é medido com base na:

> **Quantidade de comparações realizadas durante a busca**

Essa abordagem é mais confiável do que tempo de execução, pois:

* Não depende do hardware
* Não sofre interferência do sistema operacional
* Permite comparação justa entre algoritmos

---

## ⚠️ Observações Importantes

* A busca binária **só funciona corretamente com dados ordenados**
* O uso de `malloc` evita falhas de segmentação para grandes volumes de dados
* O limite `MAX` deve ser maior que o número de registros do dataset

---

## 🚀 Complexidade

| Caso        | Complexidade |
| ----------- | ------------ |
| Melhor caso | O(1)         |
| Caso médio  | O(log n)     |
| Pior caso   | O(log n)     |

---

## 📌 Conclusão

A busca binária é extremamente eficiente para grandes volumes de dados, desde que o custo de ordenação seja considerado. Em cenários onde múltiplas buscas são realizadas, seu desempenho supera significativamente a busca sequencial.
