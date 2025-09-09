# Métodos Numéricos para Equações Diferenciais Ordinárias

Este projeto implementa diversos métodos numéricos para resolver Equações Diferenciais Ordinárias (EDOs), abrangendo tanto Problemas de Valor Inicial (PVI) quanto Problemas de Valor de Contorno (PVC). O código foi desenvolvido em Python utilizando as bibliotecas `numpy`, `pandas` e `matplotlib` para os cálculos e visualização dos resultados.

## Métodos Implementados

O notebook contém implementações para resolver diferentes tipos de EDOs.

### 1. Problemas de Valor Inicial (PVI)

Para os PVIs, onde as condições são dadas em um ponto inicial, os seguintes métodos de passo único e passo múltiplo foram implementados:

* **Método de Euler Explícito:** Um método de primeira ordem, simples e direto, para encontrar a solução numérica de EDOs. O código suporta tanto uma única equação quanto sistemas de duas equações.

* **Método de Runge-Kutta de 4ª Ordem (RK4):** Um dos métodos mais populares e precisos para resolver PVIs. Oferece um bom equilíbrio entre precisão e custo computacional. A implementação também lida com equações únicas e sistemas.

* **Método Preditor-Corretor de Adams-Bashforth-Moulton:** Um método de passo múltiplo que combina o método de Adams-Bashforth (preditor) com o de Adams-Moulton (corretor) para obter uma solução mais precisa. O código utiliza o RK4 para gerar os pontos iniciais necessários para o método de passo múltiplo.

* **Métodos Auxiliares (Euler Modificado e Melhorado):** O código também inclui implementações dos métodos de Euler Modificado (Ponto Médio) e Melhorado (Heun), que foram desenvolvidos para fins de estudo e comparação, oferecendo precisão superior ao método de Euler Explícito.

### 2. Problemas de Valor de Contorno (PVC)

Para os PVCs, onde as condições são especificadas nas fronteiras do intervalo, foi utilizado o **Método das Diferenças Finitas (MDF)**.

* **Método das Diferenças Finitas (MDF):** Este método transforma a EDO em um sistema de equações lineares através da discretização do domínio e da aproximação das derivadas por diferenças finitas.

* **Algoritmo de Thomas:** Para resolver o sistema de equações lineares tridiagonal gerado pelo MDF de forma eficiente, o código utiliza o Algoritmo de Thomas, que é uma versão simplificada da eliminação de Gauss.

O MDF foi implementado para resolver EDOs de segunda ordem com três tipos de condições de contorno:
1.  **Condições de Dirichlet:** O valor da função é especificado em ambos os contornos (`y(a)` e `y(b)`).
2.  **Condições de Neumann:** O valor da derivada da função é especificado em ambos os contornos (`y'(a)` e `y'(b)`).
3.  **Condições de Robin (Mistas):** Uma combinação das condições acima, onde o valor da função é dado em um contorno e o valor da derivada é dado no outro.

## Estrutura do Código

O código está organizado nas seguintes seções:

1.  **`Definição das funções`**: Célula onde as EDOs ( `funcion1` e `funcion2` ) a serem resolvidas são definidas.
2.  **`Implementação dos Métodos para PVI`**: Funções `sistema_euler`, `euler_modificado`, `euler_melhorado`, `RungeKutta4` e `Adams_Bashforth_Moulton`.
3.  **`Implementação dos Métodos para PVC (MDF)`**: Funções `thomas_matriz_completa`, `mdf_dirichlet`, `mdf_Robin`, e `mdf_newman`.
4.  **`Menu Interativo`**: Uma célula final que permite ao usuário escolher o método, o tipo de problema, o número de equações e inserir os parâmetros necessários (`x` inicial, `x` final, passo `h` e condições iniciais/de contorno).

## Como Utilizar

1.  **Defina sua EDO**: Modifique as funções `funcion1(x, y1, y2)` e `funcion2(x, y1, y2)` na primeira célula de código para representar a equação ou o sistema que você deseja resolver. Para PVCs, modifique as funções `p(x)`, `q(x)` e `r(x)`.
2.  **Execute as Células**: Execute todas as células do notebook para carregar as funções dos métodos.
3.  **Interaja com o Menu**: Na última célula ("Menu Geral"), o programa solicitará que você escolha:
    * O tipo de método (PVI ou Adams-Bashforth-Moulton).
    * O número de equações (1 ou 2).
    * O intervalo de integração (`x` inicial e `x` final).
    * O tamanho do passo (`h`).
    * Os valores iniciais de `y1` e `y2`.
4.  **Visualize os Resultados**: Após a execução, o programa exibirá o passo a passo dos cálculos, uma tabela (DataFrame do Pandas) com os resultados e um gráfico da solução gerado pelo Matplotlib.

## Dependências

Para executar este código, você precisará das seguintes bibliotecas Python:
- `matplotlib`
- `numpy`
- `pandas`
