# Detecção de Fraturas em Imagens de Raios-X Usando Aumento de Dados para Melhoria do Modelo

#### Aluno: [Ashley Vanessa Williams](https://github.com/leynessa)
#### Orientadora: [Dr. Leonardo  Mendoza](https://github.com/link_do_github).
-->

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso.

- [Link para o código](https://colab.research.google.com/drive/14gTqqFqsg1JGBo38VZH2oucJkiQAwfdT?usp=sharing).


---

### Resumo

Este projeto visa desenvolver um modelo robusto de aprendizado de máquina para detectar fraturas em imagens de raios-X, utilizando técnicas de aumento de dados para melhorar o desempenho do modelo. A arquitetura EfficientNetB0 foi utilizada, e diversas estratégias de aumento foram aplicadas e avaliadas para entender seu impacto na precisão e generalização do modelo. O conjunto de dados foi dividido em subconjuntos de treinamento, validação e teste, e os resultados demonstraram a eficácia de aumentos específicos na melhoria da capacidade do modelo em detectar fraturas.

### 1. Introdução

A detecção de fraturas em imagens de raios-X é uma aplicação crucial da inteligência artificial em imagens médicas. No entanto, a disponibilidade limitada de conjuntos de dados anotados apresenta um grande desafio para treinar modelos de aprendizado profundo. O aumento de dados, uma técnica para aumentar artificialmente a diversidade do conjunto de dados, tem sido amplamente adotado para resolver esse problema. Este projeto explora o impacto de diferentes técnicas de aumento no desempenho de um modelo de detecção de fraturas, utilizando a arquitetura EfficientNetB0.

### 2. Arquitetura do Modelo

A arquitetura EfficientNetB0 foi escolhida por sua eficiência e alto desempenho em tarefas de classificação de imagens. O modelo foi modificado para classificação binária (fratura vs. não fratura).

### 3. Técnicas de Aumento de Dados

As técnicas de aumento de dados desempenham um papel fundamental em aumentar a diversidade dos conjuntos de dados para modelos de aprendizado de máquina. As técnicas básicas de aumento incluem transformações geométricas, como rotação, escala, translação, reflexão, cisalhamento e mudanças de perspectiva. Também pode envolver recorte, onde patches aleatórios são selecionados, ou oclusão, que simula imagens incompletas ao remover partes delas. Operações de intensidade, como ajuste de brilho, modificação de contraste e correção de gama, também são comumente usadas. Além disso, injeção de ruído, como ruído Gaussiano ou ruído sal e pimenta, e filtros como nitidez, desfoque ou suavização são aplicados para alterar a qualidade da imagem.

Técnicas avançadas de aumento, como campos de deslocamento aleatórios, deformações elásticas aplicadas com filtros gaussianos, interpolação de splines e modelagem de forma estatística, são utilizadas para gerar variações anatômicas aprendidas. Métodos baseados em aprendizado profundo, como Redes Gerativas Adversárias (GANs), autoencoders variacionais e adaptação de domínio, também foram explorados.

### 4. Metodologia

A metodologia deste projeto envolveu três fases principais: preparação de dados, experimentos de aumento e treinamento do modelo.

1. **Preparação dos Dados**  
As imagens do conjunto de dados foram redimensionadas para uma dimensão consistente de 224x224 pixels para atender à exigência de entrada do modelo EfficientNetB0. O conjunto de dados foi então dividido em três subconjuntos: treinamento, validação e teste.

2. **Experimentos de Aumento**  
Várias estratégias de aumento foram aplicadas utilizando o `ImageDataGenerator` do TensorFlow e a biblioteca Albumentations. Cada técnica de aumento foi testada individualmente, permitindo uma análise detalhada de como cada tipo de aumento influenciou o desempenho do modelo.

3. **Treinamento do Modelo**  
O modelo foi treinado usando o otimizador Adam com uma taxa de aprendizado de 1e-4. A entropia cruzada binária foi usada como função de perda, e a precisão foi o principal métrico de avaliação. O treinamento também incluiu callbacks como EarlyStopping e ModelCheckpoint.

### 5. Resultados

A tabela a seguir resume os resultados de precisão de validação, perda e AUC (Área sob a Curva) para o modelo base e diferentes estratégias de aumento.



| Aumento de Dados      | Precisão de Validação | Perda de Validação | AUC de Validação |
|-----------------------|-----------------------|--------------------|------------------|
| Baseline              | 0.896                 | 0.284              | 0.452            |
| Geométrico            | 1.000                 | 0.047              | 0.467            |
| Ruído                 | 0.941                 | 0.333              | 0.507            |
| Intensidade           | 0.235                 | 0.908              | 0.497            |
| Flip                  | 0.910                 | 0.272              | 0.521            |
| Rotação               | 1.000                 | 0.024              | 0.532            |
| Zoom                  | 0.941                 | 0.117              | 0.443            |
| Deslocamento (Shift)  | 0.941                 | 0.276              | 0.515            |
| Brilho                | 1.000                 | 0.047              | 0.532            |
| Flip + Rotação        | 0.890                 | 0.139              | 0.519            |
| Brilho + Zoom         | 0.941                 | 0.358              | 0.507            |
| Flip + Deslocamento   | 0.941                 | 0.053              | 0.503            |
| Geo + Ruído           | 0.882                 | 0.495              | 0.524            |
| Geo + Intensidade     | 0.783                 | 0.939              | 0.497            |
| Ruído + Intensidade   | 0.882                 | 0.438              | 0.507            |




### 6. Discussões

Os resultados indicam que técnicas de aumento de dados, como transformações geométricas (rotação, zoom) melhoraram consistentemente o desempenho do modelo. No entanto, as técnicas baseadas em intensidade apresentaram resultados mistos, com o brilho funcionando bem isoladamente, mas não melhorando significativamente quando combinadas com outras transformações.

### 7. Conclusões

Este estudo ressalta a importância de selecionar cuidadosamente as técnicas de aumento de dados para equilibrar a precisão e a generalização do modelo. Trabalho futuro pode explorar aumentos avançados, como transformações deformáveis ou abordagens baseadas em GANs, para melhorar ainda mais as capacidades do modelo em aplicações clínicas reais.

---

Matrícula: 222.100.121

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
