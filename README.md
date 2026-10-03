# TCC_II_IFG_2026 — Mapeamento do Projeto

* **Título:** Migração de sistemas legados de análise química: de Java desktop para Python web
* **Autor:** Wagner Oliveira de Araujo
* **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia de Goiás — Campus Anápolis
* **Curso:** Bacharelado em Ciência da Computação
* **Trabalho:** Trabalho de Conclusão de Curso II (TCC II), 2026
* **Orientador:** Prof. Alexandre Bellezi Jose, Me.
* **Coorientador:** Prof. Eder Silva de Brito, Dr.
* **Coordenador do curso:** Prof. Hugo Vinicius Leão e Silva, Dr.
* **Banca:** Luiz Fernando Loja, Dr. (avaliador interno, IFG) e Ermiliano Nelson, Dr. (avaliador externo, UFG)
* **Defesa prevista:** 20 de novembro de 2026, Anápolis

---

## Arquivo Raiz

### `TCC_II_IFG_2026.tex`

Ponto de entrada do documento LaTeX. Responsável por:

- Configurar a classe `abntex2` (12 pt, A4, `oneside`, idioma principal `brazil`) e carregar o estilo `setup/ufscthesisA4-alf`
- Carregar os pacotes de tabelas (`tabularx`, `threeparttable`, `booktabs`, `siunitx`, `multirow`), gráficos (`tikz`, `pgfplots`), algoritmos (`algorithm2e`), código (`listings`, `fancyvrb`) e dados (`readarray`)
- Usar citações numéricas ABNT (`abntex2cite` com opção `num`), `\bibliographystyle{abntex2-num}` e `\bibliography{pos/references}`; `backref` indica as páginas de citação
- Declarar metadados (título, autor, orientadores, coordenador, banca, ano, local) e metadados do PDF (`hyperref` + `hyperxmp`)
- Declarar a lista de siglas (`\siglalista`) e de símbolos (`\simbololista`), exibidas por `glossaries`
- Definir as macros `\oautor` (fonte das figuras e tabelas) e `\testes` (tempo da suíte de testes: 75,25 s)
- Ler os arquivos `.csv` da raiz como matrizes (`\readarray`)
- Incluir os elementos pré-textuais, as dez seções textuais e os apêndices

**Siglas declaradas:** LASSO, MAE, PLS, RLM, RMSEP, RMSEP-CV, AWT, EJML, JVM, MVC, MVP, WCAG, AJAX, IDE, MoSCoW.

**Dados `.csv` lidos pelo LaTeX**

| Arquivo | Matriz | Colunas | Uso (seção 4) |
|---------|--------|:------:|---------------|
| `r_bagging.csv` | `\dados` | 6 | RMSEP por analito: linha 2 = RLM, 3 = *bagging* (m = 17), 4 = *subagging* |
| `r_bagging2.csv` | `\rdados` | 6 | Dados complementares de *bagging* |
| `rmsep5080.csv` | `\rmsepdados` | 7 | RMSEP com 50% e 80% de calibração (RLM, *bagging*, *subagging*) |
| `rmsepsuperior.csv` | `\rmsepmaior` | 4 | Menor RMSEP por elemento e proporção correspondente |

---

## Estrutura de Diretórios

```
Projeto_TCC_II/
│
├── TCC_II_IFG_2026.tex          ← Arquivo raiz
├── r_bagging.csv · r_bagging2.csv · rmsep5080.csv · rmsepsuperior.csv
│
├── setup/
│   ├── ufscthesisA4-alf.sty     ← Estilo (abnTeX2 adaptado da UFSC para o IFG): capa, folha de rosto,
│   │                              folha de aprovação, ata, cabeçalhos (fancyhdr), glossaries, quadros
│   ├── stylodefinicao.tex       ← Definições de formatação
│   ├── algorithm2e.sty          ← Algoritmos
│   └── defs.ldf                 ← Definições de idioma
│
├── pre/                         ← Elementos pré-textuais
│   ├── pre.tex                  ← Orquestra os elementos abaixo
│   ├── fichaCatalografica.tex · folhaAprovacao.tex · ata.tex · termo.tex
│
├── tex/                         ← Seções textuais (1secao.tex … 10secao.tex) e dados dos gráficos
│   ├── dados/                   ← rlm_{mn,fe}.txt · bagging_{mn,fe}.txt · subagging_{mn,fe}.txt
│   ├── bagging_{mn,fe}.txt · bootstrap_{mn,fe}.txt        ← Sensibilidade ao número de replicações
│   ├── Yteste{Mn,Fe}.txt                                  ← Concentrações de referência
│   ├── Cpred{Mn,Fe}.txt                                   ← Predições RLM
│   ├── baggingCpredMn.txt · BaggingCpredFe.txt            ← Predições RLM-bagging
│   └── SubaggingCpred{Mn,Fe}.txt                          ← Predições RLM-subagging
│
├── pos/
│   ├── references.bib                ← Referências (BibTeX)
│   ├── apendice_d.tex                ← Apêndice A (Testes de Gráficos)
│   ├── apendice_c.tex                ← Apêndices B (Paridade) e C (Resultado dos Testes)
│   └── result_test_consolidados.txt  ← Saída bruta do pytest, lida por \VerbatimInput
│
└── outros/
    ├── fig/                          ← Logos IFG (capa e ata) e diagramas em E_Diagramas/out/ e E_Diagramas/streamlit/
    └── prog/                         ← Espectros médios por analito: dados_{Fe,Cr,Mn,Ni,Mo}.txt
```

> **Atenção:** os nomes dos arquivos de apêndice **não** coincidem com as letras no PDF (ver [Apêndices](#apêndices)).

### Código-fonte e artefatos de apoio

```
├── BaggingOptimized.java            ← Sistema legado (Java Desktop monolítico: Swing/AWT, EJML, JFreeChart), v3.0
├── Resultados_Otimizados_{Mn,Mo,Cr,Ni,Fe}.txt   ← Saídas do Java (referência dos testes de caixa-preta)
│
├── models.py                        ← Núcleo matemático (NumPy/Pandas), v8a
├── components.py                    ← Componentes visuais (Plotly + HTML/CSS), v8b
├── app.py                           ← Interface Streamlit (3 abas, i18n pt/en), v8a
├── test_suite_5.py                  ← Suíte pytest: 21 unitários, 60 caixa-preta, 11 stress
├── gerar_dados_simulados.py         ← Dados espectrais sintéticos de alta dimensão
│
├── Estrutura.tex                    ← Roteiro-padrão de estrutura de TCC em Ciência da Computação
└── Regras_trabalhos_academicos.md   ← Normas ABNT e regras de redação do TCC 2
```

| Módulo | Responsabilidade | Funções principais |
|--------|------------------|--------------------|
| `models.py` | Leitura de `.txt`/`.csv`/`.xlsx`, RLM, *bagging/subagging*, métricas, validação cruzada 5-*fold*, *grid search* | `parse_matrix`, `parse_vector`, `perform_rlm` (`np.linalg.lstsq`), `perform_bagging`, `calc_metrics`, `run_cross_validation`, `find_optimal_parameters`, `run_full_analysis` |
| `components.py` | Gráficos Plotly e *cards* de métricas | `build_chart`, `build_scatter_chart`, `metric_card_html`, `get_header_html` |
| `app.py` | Abas Configuração, Resultados e Gráficos; validação de parâmetros; exportação CSV/log | `parse_int_list`, `parse_float_list` |

---

## Detalhamento das Seções Textuais

A numeração segue a ordem do sumário (ordem de `\include` no arquivo raiz); **o número da seção nem sempre coincide com o do arquivo** (ver [Pontos de atenção](#pontos-de-atenção)).

### Seção 1 — Introdução (`1secao.tex`, `cha:introducao`)

- Contextualiza a calibração multivariada de aço-ligas (Mn, Cr, Mo, Ni, Fe) e formula o problema de pesquisa
- Declara a contribuição em dois eixos (quimiométrico e engenharia de *software*) e a limitação por conjunto amostral reduzido
- Objetivo geral e objetivos específicos **a)** a **e)**: aplicar *bootstrap/bagging/subagging* com RLM; comparar RLM, RLM-*bagging* e RLM-*subagging*; reaproveitar o sistema Java (JavaSE-17) como referência; desenvolver o protótipo Python 3.12/Streamlit com três módulos; garantir equivalência por 92 testes pytest
- Descreve a organização do trabalho em dez seções

### Seção 2 — Revisão da Literatura (`2secao.tex`, `cha:tecboot`)

- Regressão Linear Múltipla: estimação dos coeficientes (pseudo-inversa de Moore-Penrose) e premissas/métodos robustos
- Técnica de *bootstrap*: estimativa *bootstrap*, número de replicações *m* (Tabela do coeficiente de variação)
- Reamostragem aleatória, teoria da probabilidade, função de distribuição empírica, princípio *plug-in*
- Técnicas clássicas de reamostragem: *bagging*, *subagging* e comparação entre ambos (Quadro)
- Fundamentos de engenharia de migração (reescrita *black-box*) e qualidade de *software*
- **Figuras:** método *bootstrap*, amostragem aleatória, agregação de regressores. **Algoritmos:** estimativa *bootstrap*, *bagging*, *subagging*

### Seção 3 — Materiais e Métodos (`3secao.tex`, `cha:metresult`)

- Ferramentas do sistema legado (JavaSE-17, Eclipse, EJML 0.43.1, JFreeChart 1.5.4, Swing/AWT) e declaração do uso de IA como ferramenta de apoio
- Fragmentos do código Java: `performRLM` e `performBagging` (Figuras)
- Amostras de aço-ligas: espectrômetro de emissão atômica em plasma, 723 variáveis; espectros médios (Figura) e dimensões dos conjuntos por elemento (Quadro)
- Protocolo de validação: CV 5-*fold* só na calibração, *seed* = 42, *grid search* em *m* ∈ {10, 20, 30, 40, 50} e *k* ∈ {0,50; 0,60; 0,70; 0,80}
- Métricas RMSEP, MAE e R² (equações) e RMSEP-CV

### Seção 4 — Análise Experimental dos Algoritmos Quimiométricos (`4secao.tex`, `sec:result`)

- RMSEP da RLM por analito; ilustração com Mn e Fe
- *Bagging*: sensibilidade ao número de replicações (1 a 50) e comparação com a RLM
- *Subagging*: sensibilidade ao número de *bootstraps* e comparação com a RLM
- Proporções de calibração 50% × 80% e técnica vencedora por elemento
- Tempo de execução (50% e 80% das amostras)
- *Bagging* × *Subagging* com parâmetros otimizados por CV 5-*fold*: tabela comparativa (RMSEP, MAE, R², tempo, *k*\*, *m*\*) e gráfico de tempos
- **Tabelas:** `rmseprlm`, `bagging`, `subagging`, `comparacao_50_80`, `melhor_rmseep`, `baggingsubba`

### Seção 5 — Requisitos Funcionais (`5secao.tex`, `sec:reqfunc`)

- Inventário de funções, entradas e saídas
- Priorização MoSCoW: essenciais (E01–E05), desejáveis (D01–D05) e extras (X01–X05)
- Fluxo principal (fluxograma TikZ), fluxos alternativos e pontos críticos de usabilidade
- Requisitos não funcionais: performance, usabilidade (WCAG 2.1 AA), segurança e escalabilidade
- Considerações finais do levantamento
- **12 quadros** (`funcoes`, `entradas`, `saidas`, `essenciais`, `desejaveis`, `extras`, `fluxos-alternativos`, `pontos-criticos`, `performance`, `usabilidade`, `seguranca`, `escalabilidade`)

### Seção 6 — Engenharia de Software e Modernização (`6secao.tex`, `sec:engenhariasoftware`)

- Engenharia de requisitos segundo Sommerville: elicitação, análise, especificação (contratos com *type hints*) e validação
- Arquitetura modular em três camadas: `models.py`, `components.py`, `app.py`

### Seção 7 — Resultados e Discussões (`7secao.tex`, `sec:resultados`)

- Avaliação preditiva (RLM × *bagging* × *subagging*) por analito e eficiência computacional

### Seção 8 — Interface e Experiência do Usuário (UI/UX) Científica (`8secao.tex`, `sec:uiux`)

- Design da interface e fluxo de trabalho em três abas: Configuração e Carga de Dados, Resultados Numéricos e Logs, Visualização Gráfica

### Seção 9 — Desenvolvimento Iterativo por *Sprints* e Validação por Testes Automatizados (`9secao.tex`, `sec:sprints`)

- Quatro *sprints*: leitura de dados, algoritmos científicos, interface reativa, otimização com *cache* (`@st.cache_data`, ganho não medido)
- Suíte pytest (`sec:testescaixapreta`): 21 testes unitários, 60 de caixa-preta (12 testes × 5 analitos) e 11 de carga e *stress*
- Resultado consolidado: 92 testes aprovados, 75,25 s (Windows, Python 3.12.10, pytest 9.1.0)
- Tabela de paridade Java × Python para *Bagging* – Cr (as demais estão no Apêndice B)

### Seção 10 — Conclusão (`10secao.tex`, `sec:conclusao`)

- Síntese dos dois eixos, limitações e trabalhos futuros (agente de IA para interpretação de gráficos, ampliação amostral, testes de carga em nuvem)

---

## Apêndices

Em `TCC_II_IFG_2026.tex`, `apendice_d` é incluído antes de `apendice_c`, e cada `\chapter` vira um apêndice em ordem alfabética:

| Letra no PDF | Título | Arquivo | Conteúdo |
|:------------:|--------|---------|----------|
| **A** | Testes de Gráficos | `pos/apendice_d.tex` | Arquitetura em camadas (Java e Python) e diagramas UML/PlantUML: classes, atividades e sequência (Java e Streamlit) |
| **B** | Tabelas de Paridade Amostra-a-Amostra — Java × Python | `pos/apendice_c.tex` | 14 tabelas (RLM, *Bagging*, *Subagging* × Mn, Mo, Cr, Ni, Fe), exceto *Bagging* – Cr, que está na Seção 9 |
| **C** | Resultado dos Testes | `pos/apendice_c.tex` | Saída do pytest (`pos/result_test_consolidados.txt`, Código `code:codi5`) |

---

## Fluxo de Inclusão do Arquivo Raiz

```
TCC_II_IFG_2026.tex
│
├── \usepackage{setup/ufscthesisA4-alf}
├── \input{setup/stylodefinicao}
├── \input{pre/pre}                    ← Capa, folha de rosto, ficha, aprovação, ata, listas
│
├── \include{tex/1secao}               ← 1  Introdução
├── \include{tex/2secao}               ← 2  Revisão da Literatura
├── \include{tex/3secao}               ← 3  Materiais e Métodos
├── \include{tex/4secao}               ← 4  Análise Experimental dos Algoritmos Quimiométricos
├── \include{tex/5secao}               ← 5  Requisitos Funcionais
├── \include{tex/6secao}               ← 6  Engenharia de Software e Modernização
├── \include{tex/7secao}               ← 7  Resultados e Discussões
├── \include{tex/8secao}               ← 8  Interface e Experiência do Usuário
├── \include{tex/9secao}               ← 9  Sprints e Testes Automatizados
├── \include{tex/10secao}              ← 10 Conclusão
│
├── \bibliography{pos/references}
├── \input{pos/apendice_d}             ← Apêndice A
└── \input{pos/apendice_c}             ← Apêndices B e C
```

---

## Pontos de atenção

1. **Ordem das seções = ordem do sumário.** A numeração adotada neste README é a do sumário (ordem dos `\include` no raiz): 4 Análise Experimental, 5 Requisitos Funcionais, 6 Engenharia de Software, 7 Resultados e Discussões. O parágrafo "Este trabalho está organizado em dez seções" em `1secao.tex` está fora dessa ordem (cita `sec:resultados` logo após `sec:result`) e deve ser corrigido: `sec:result` (4), `sec:reqfunc` (5), `sec:engenhariasoftware` (6), `sec:resultados` (7), `sec:uiux` (8), `sec:sprints` (9), `sec:conclusao` (10).
2. **Comentários desatualizados no raiz.** O comentário de `\include{tex/7secao}` ainda cita "Ecossistema de Desenvolvimento (Python e Streamlit)", mas esse arquivo contém Resultados e Discussões. Não existe seção dedicada ao ecossistema Python/Streamlit no momento.
3. **Nomes dos apêndices.** Os arquivos `apendice_d.tex` e `apendice_c.tex` geram os Apêndices A, B e C no PDF (tabela acima).
4. **Seção 4 (`4secao.tex`).** Contém um comentário interno de substituição de trecho ("TRECHO ORIGINAL a ser REMOVIDO") que pode ser limpo.

---

## Como Compilar o Documento

```bash
pdflatex TCC_II_IFG_2026.tex
bibtex TCC_II_IFG_2026
pdflatex TCC_II_IFG_2026.tex
pdflatex TCC_II_IFG_2026.tex
```

Ou: `latexmk -pdf TCC_II_IFG_2026.tex`

> Os quatro `.csv` precisam estar na raiz (lidos pelo LaTeX), assim como `outros/fig/` (logos) e `pos/result_test_consolidados.txt`.

---

## Como Executar a Aplicação e os Testes

```bash
streamlit run app.py                          # aplicação web

python -m pytest test_suite_5.py -v           # suíte completa
python -m pytest test_suite_5.py -v -k "unitario"   # 4.1 unitários
python -m pytest test_suite_5.py -v -k "caixa"      # 4.2 caixa-preta (Python × Java)
python -m pytest test_suite_5.py -v -k "stress"     # 4.3 carga e stress
```

Os testes de caixa-preta exigem `Xcal.txt`, `Ycal*.txt`, `Xteste*.txt`, `Yteste*.txt` (um conjunto por analito) e `Resultados_Otimizados_*.txt` no diretório de execução; sem eles, são ignorados (`skip`). `gerar_dados_simulados.py` requer o `Xcal.txt` real para extrair o perfil espectral.
