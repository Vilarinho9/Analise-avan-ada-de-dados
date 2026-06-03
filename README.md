# State of Data Brazil 2024–2025

## Análise dos Fatores que Influenciam o Salário no Mercado de Dados Brasileiro

Disciplina: Análise Avançada de Dados — UNIFSA
Professora: Ma. Heloísa Guimarães
Dataset: State of Data Brazil 2024–2025 — Kaggle
Fonte dos dados: Data Hackers + Bain & Company | 5.217 respondentes | 403 colunas

---

## Pergunta Central

"Quais fatores mais influenciam o salário de um profissional de dados no Brasil em 2024?"

---

## Resposta em 3 Parágrafos

O fator mais determinante do salário de um profissional de dados no Brasil é a senioridade. A mediana salarial dobra a cada transição de nível: Júnior (R$ 3.500) → Pleno (R$ 7.000) → Sênior (R$ 14.000), resultando em uma diferença de +300% entre os extremos. A correlação de Spearman entre senioridade e salário é ρ=0,73, a maior observada em toda a análise. Isso significa que conhecer o nível de senioridade de um profissional permite prever seu salário com boa precisão, independentemente de outros fatores.

Em segundo lugar, o tempo de experiência (ρ=0,66) e a especialização de cargo têm impacto relevante. Profissionais com mais de 10 anos de experiência ganham, em mediana, quatro vezes mais que iniciantes. Cargos técnicos avançados como ML/AI Engineer e Arquiteto de Dados apresentam mediana de R$ 14.000, o dobro de Analistas de Dados (R$ 7.000). A escolaridade stricto sensu (Mestrado e Doutorado) também diferencia: mediana de R$ 14.000, cerca de 40% acima de quem tem apenas graduação ou pós-graduação lato sensu.

Em menor magnitude, região e gênero também influenciam. O Sudeste e Sul têm mediana 43% maior que Norte e Nordeste, diferença que tende a diminuir com a expansão do trabalho remoto. A diferença salarial bruta por gênero na mediana geral é próxima de zero, mas isso não significa ausência de desigualdade. Mulheres são sub-representadas em cargos sênior e técnicos avançados, o que reduz seu salário mediano agregado. Essa desigualdade estrutural exige análise mais profunda do que a simples comparação de medianas.

---

## Estrutura do Repositório

```text
nome1-nome2-state-of-data/
├── README.md
├── notebook/
│   └── nome1-nome2-analise.ipynb
├── relatorio/
│   └── nome1-nome2-relatorio.pdf
└── dados/
    └── README.md
```

---

## Dashboard

Acessar Dashboard no Google Looker Studio: INSERIR LINK AQUI

O dashboard contém:

* Distribuição salarial (histograma interativo)
* Mediana por senioridade e cargo
* Mapa de calor salarial por região
* Comparativo salarial por gênero e escolaridade
* Filtros por senioridade, região e cargo

---

## Metodologia

| Etapa                 | Descrição                                                                                                                        |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| 1. Carregamento       | Leitura do CSV (403 colunas, 5.217 linhas), inspeção de shape, tipos de dados e valores ausentes, renomeação de 14 colunas-chave |
| 2. Limpeza            | Conversão de faixas salariais para ponto médio, tratamento de dados ausentes e padronização de cargos                            |
| 3. Análise Univariada | Frequência, média, mediana, moda, desvio padrão, variância, amplitude, assimetria e curtose                                      |
| 4. Análise Bivariada  | Correlação de Spearman, boxplots e análise comparativa por gênero, cargo e região                                                |
| 5. Síntese            | Ranking dos fatores por impacto na mediana salarial                                                                              |

---

## Principais Decisões de Limpeza

### Conversão salarial para ponto médio numérico

A coluna `2.h_faixa_salarial` contém valores textuais como:

`de R$ 8.001/mês a R$ 12.000/mês`

Ela foi convertida para o ponto médio aritmético da faixa.

| Faixa original                   | Ponto médio |
| -------------------------------- | ----------- |
| Menos de R$ 1.000/mês            | R$ 500      |
| de R$ 4.001/mês a R$ 6.000/mês   | R$ 5.000    |
| de R$ 8.001/mês a R$ 12.000/mês  | R$ 10.000   |
| de R$ 12.001/mês a R$ 16.000/mês | R$ 14.000   |
| Acima de R$ 40.001/mês           | R$ 50.000   |

Impacto: possibilita análises quantitativas, embora introduza uma aproximação ao assumir distribuição uniforme dentro das faixas. A mediana foi utilizada como principal medida para reduzir esse efeito.

### Tratamento de dados ausentes

* 354 registros sem informação salarial (6,8%) foram excluídos das análises salariais.
* 1.399 registros sem cargo ou nível (26,8%) foram excluídos das análises de cargo e senioridade.
* Respostas "Prefiro não informar" em gênero e raça não foram imputadas.
* Valores ausentes em ferramentas como Python e SQL foram tratados como 0 (não utiliza).

---

## Principais Insights

| Nº | Insight                                      | Resultado                                  |
| -- | -------------------------------------------- | ------------------------------------------ |
| 1  | Senioridade é o fator dominante              | Júnior R$ 3.500 → Sênior R$ 14.000 (+300%) |
| 2  | Experiência aumenta o salário                | ρ = 0,66                                   |
| 3  | ML/AI e Engenharia de Dados lideram salários | R$ 14.000 vs R$ 7.000                      |
| 4  | Mestrado e Doutorado agregam valor           | R$ 14.000 vs R$ 10.000                     |
| 5  | Existe diferença regional                    | Sudeste/Sul +43% vs Norte/Nordeste         |
| 6  | Mediana salarial geral                       | R$ 10.000/mês                              |

---

## Tecnologias Utilizadas

```text
Python 3.10
├── pandas
├── numpy
├── matplotlib
├── seaborn
├── scipy.stats
└── reportlab
```

---

## Aspectos Éticos

* A diferença salarial bruta entre gêneros não representa necessariamente igualdade de oportunidades.
* Profissionais pretos e pardos são menos representados na amostra e nos cargos de maior remuneração.
* A pesquisa possui viés de seleção por concentrar participantes engajados em comunidades técnicas.
* As relações identificadas são correlacionais e não permitem inferir causalidade.

---

## Referências

Data Hackers & Bain & Company. State of Data Brazil 2024–2025. Kaggle. Disponível em: [https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-20242025](https://www.kaggle.com/datasets/datahackers/state-of-data-brazil-20242025)

Documentação Pandas: [https://pandas.pydata.org/docs/](https://pandas.pydata.org/docs/)

Documentação SciPy Stats: [https://docs.scipy.org/doc/scipy/reference/stats.html](https://docs.scipy.org/doc/scipy/reference/stats.html)

Spearman, C. (1904). The proof and measurement of association between two things. The American Journal of Psychology, 15(1), 72–101.

---

Trabalho desenvolvido para a disciplina Análise Avançada de Dados, UNIFSA, junho de 2026.
