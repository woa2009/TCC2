# TCC_II_IFG_2025 — Mapeamento do Projeto

* **Título:** Migração de Sistemas Legados de Análise Química: DE JAVA Desktop Para PYTHON WEB
* **Autor:** Wagner Oliveira de Araujo
* **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia de Goiás — Campus Anápolis
* **Curso:** Bacharelado em Ciência da Computação
* **Trabalho:** TCC II (2026)
* **Orientador:** Prof. Alexandre Bellezi Jose, Me.
* **Coorientador:** Prof. Eder Silva de Brito, Dr.

O repositório reúne duas frentes: (1) o **documento LaTeX** do TCC e (2) o **código-fonte** do sistema (legado Java e versão final Python/Streamlit), com testes, dados simulados e resultados de referência.

---

## Arquivo Raiz

### `TCC_II_IFG_2025.tex`

Ponto de entrada principal do documento LaTeX. Responsável por:

- Configurar a classe `abntex2` com as opções da instituição (IFG)
- Carregar todos os pacotes utilizados no documento (tipografia, gráficos, algoritmos, tabelas, referências ABNT etc.)
- Declarar metadados do trabalho (autor, título, orientadores, ano, local)
- Definir a lista de siglas (`\siglalista`) e a lista de símbolos matemáticos (`\simbololista`)
- Carregar dados de tabelas a partir de arquivos `.csv` (`r_bagging.csv`, `r_bagging2.csv`, `rmsep5080.csv`, `rmsepsuperior.csv`)
- Incluir os elementos pré-textuais, textuais e pós-textuais via `\input` e `\include`

### `Estrutura.tex`

Guia (texto de apoio, não compilado no documento) com a estrutura padrão de um TCC em Ciência da Computação: elementos pré-textuais, introdução, referencial teórico e metodologia/proposta da solução. Serve de checklist para a organização das seções.

---

## Estrutura de Diretórios

```
B_Projeto_Integrador_III_Final/
│
├── TCC_II_IFG_2025.tex          ← Arquivo raiz do documento
├── Estrutura.tex                ← Guia da estrutura padrão do TCC (apoio)
├── README.md                    ← Este arquivo
│
├── setup/                       ← Configurações e estilos LaTeX
│   ├── ufscthesisA4-alf.sty     ← Estilo principal do template (adaptado do UFSC para IFG)
│   ├── stylodefinicao.tex       ← Definições de formatação personalizadas
│   ├── algorithm2e.sty          ← Pacote para exibição de algoritmos
│   └── defs.ldf                 ← Definições de idioma
│
├── pre/                         ← Elementos pré-textuais
│   ├── pre.tex                  ← Orquestra todos os elementos pré-textuais
│   ├── fichaCatalografica.tex   ← Ficha catalográfica
│   ├── folhaAprovacao.tex       ← Folha de aprovação
│   ├── ata.tex                  ← Ata de defesa
│   └── termo.tex                ← Termo de compromisso/autorização
│
├── tex/                         ← Seções e conteúdo textual
│   ├── 1secao.tex               ← Seção 1: Introdução
│   ├── 2secao.tex               ← Seção 2: Revisão da Literatura
│   ├── 3secao.tex               ← Seção 3: Materiais e Métodos
│   ├── 4secao.tex               ← Seção 4: Resultados e Discussões
│   ├── 5secao.tex               ← Seção 5: Requisitos Funcionais
│   ├── 6secao.tex               ← Seção 6: Engenharia de Software e Modernização
│   ├── 7secao.tex               ← Seção 7: Ecossistema de Desenvolvimento (Python e Streamlit)
│   ├── 8secao.tex               ← Seção 8: Interface e Experiência do Usuário (UI/UX) Científica
│   ├── 9secao.tex               ← Seção 9: Desenvolvimento Iterativo por Sprints e Testes Automatizados
│   ├── 10secao.tex              ← Seção 10: Conclusão
│   ├── algoritmos.tex           ← Algoritmos utilizados no trabalho
│   ├── graficos.tex             ← Código TikZ/pgfplots para os gráficos
│   ├── apoio_4secao.tex         ← Material de apoio para a Seção 4
│   ├── apoio_subagging.tex      ← Material de apoio sobre subagging
│   ├── discussao.tex            ← Texto auxiliar de discussão
│   ├── pesquisa.tex             ← Texto de pesquisa/levantamento bibliográfico
│   ├── dados/                   ← Dados tabulares para as seções
│   │   ├── bagging_fe.txt / bagging_mn.txt       ← Resultados de bagging (Fe, Mn)
│   │   ├── bootstrap_fe.txt / bootstrap_mn.txt   ← Resultados de bootstrap (Fe, Mn)
│   │   ├── rlm_fe.txt / rlm_mn.txt               ← Resultados de RLM (Fe, Mn)
│   │   └── subagging_fe.txt / subagging_mn.txt   ← Resultados de subagging (Fe, Mn)
│   └── [outros .txt/.csv]       ← Dados auxiliares de predições e RMSEP
│
├── pos/                         ← Elementos pós-textuais
│   ├── references.bib           ← Arquivo principal de referências bibliográficas (BibTeX)
│   ├── references1.bib          ← Referências complementares (versão anterior)
│   ├── apendice_a.tex           ← Apêndice A (incluído mas desabilitado no raiz)
│   ├── apendice_c.tex           ← Apêndice: tabelas de paridade Java × Python + resultado dos testes
│   ├── apendice_d.tex           ← Apêndice: testes de gráficos (arquitetura, UML e PlantUML)
│   ├── result_test_consolidados.txt ← Saída bruta do pytest (\VerbatimInput no apêndice)
│   ├── anexo_a.tex              ← Anexo A (incluído mas desabilitado no raiz)
│   └── [outros .bib]            ← Arquivos de referências individuais por fonte
│
├── outros/                      ← Recursos auxiliares do projeto
│   ├── fig/                     ← Figuras e imagens utilizadas no documento
│   │   ├── bootstrap.png / subagging.png         ← Ilustrações dos métodos
│   │   ├── resultado_final.png / .eps            ← Figura de resultado principal
│   │   ├── RLM_Bagging.pdf, BootStrapRMSEPFe.pdf ← Gráficos comparativos
│   │   ├── IFGAnapolisHor2.png, logoIFG.jpg      ← Logomarcas IFG
│   │   ├── E_Diagramas/          ← Diagramas do Apêndice D
│   │   │   ├── out/              ← Sistema Java (classe, atividade, sequência)
│   │   │   └── streamlit/        ← Sistema Streamlit (atividades, classes, sequência)
│   │   └── [outras figuras]      ← Figuras históricas/legadas (.eps, .pdf, .jpg, .png)
│   └── prog/                     ← Scripts e dados de programas auxiliares
│       ├── dados_Fe.txt, dados_Mn.txt, dados_Cr.txt, dados_Ni.txt, dados_Mo.txt ← Espectros médios
│       ├── bagging.txt, subbagging.txt  ← Script/saída de bagging e subagging
│       └── insertionsort.c              ← Código C auxiliar (insertion sort)
│
├── streamlit-app/               ← Sistema final Python/Streamlit (TCC II)
│   ├── app.py                   ← Orquestrador da interface (Streamlit)
│   ├── models.py                ← Motor matemático (NumPy/Pandas)
│   ├── components.py            ← Fábrica de componentes visuais (Plotly + HTML/CSS)
│   ├── test_suite_5.py          ← Suíte de 92 testes automatizados (pytest)
│   ├── gerar_dados_simulados.py ← Gerador de dados espectrais simulados
│   └── resultados_java/         ← Saídas do sistema Java (referência dos testes de caixa-preta)
│       ├── Resultados_Otimizados_Mn.txt
│       ├── Resultados_Otimizados_Mo.txt
│       ├── Resultados_Otimizados_Cr.txt
│       ├── Resultados_Otimizados_Ni.txt
│       └── Resultados_Otimizados_Fe.txt
│
├── java/                        ← Sistema legado (Java Desktop)
│   └── BaggingOptimized.java    ← Aplicação Swing: RLM, Bagging e Subagging (EJML + JFreeChart)
│
├── pdf_old/                     ← PDFs de versões anteriores do trabalho
│
├── references.bib               ← Cópia de referências na raiz
├── r_bagging.csv                ← Dados CSV lidos diretamente pelo TCC_II_IFG_2025.tex
├── r_bagging2.csv               ← Dados CSV complementares (bagging)
├── rmsep5080.csv                ← Dados RMSEP (50%-80% divisão treino/teste)
├── rmsepsuperior.csv            ← Dados RMSEP superior
├── subfigure.sty                ← Pacote de subfiguras (legado)
│
└── [arquivos gerados pela compilação LaTeX]
    ├── TCC_II_IFG_2025.pdf      ← PDF final gerado
    ├── TCC_II_IFG_2025.aux / .bbl / .blg / .toc / .lof / .lot
    ├── TCC_II_IFG_2025.idx / .ind / .ilg
    └── TCC_II_IFG_2025.log
```

> **Nota:** as pastas `streamlit-app/`, `java/` e `resultados_java/` são a organização sugerida para os arquivos de código; ajuste conforme a estrutura real do repositório. O `test_suite_5.py` espera encontrar, no diretório de execução, `Resultados_Otimizados_<Analito>.txt`, `Xcal.txt`, `Ycal<Analito>.txt`, `Xteste<Analito>.txt` e `Yteste<Analito>.txt`; sem eles, os testes de caixa-preta são ignorados (`skip`).

---

## Código-Fonte do Sistema

### Sistema final — Python/Streamlit (`streamlit-app/`)

Arquitetura em três camadas com acoplamento zero entre elas (`models.py` não importa Streamlit nem Plotly; `components.py` não importa Streamlit nem NumPy).

| Arquivo | Camada | Responsabilidade |
|---------|--------|------------------|
| `app.py` | Apresentação | Layout Streamlit em três abas (Configuração, Resultados, Gráficos); `st.file_uploader` para `Xcal`, `Ycal`, `Xteste`, `Yteste` (`.txt`, `.csv`, `.xlsx`); validação de `m` e `k` (`parse_int_list`, `parse_float_list`); barra de progresso; persistência em `st.session_state["result"]`; exportação de métricas (`.csv`) e log (`.txt`); seletor de idioma PT/EN na barra lateral (`st.session_state["lang"]`), com dicionário `_TRADUCOES` para rótulos, mensagens e textos de ajuda. Sem lógica matemática. |
| `models.py` | Núcleo algorítmico | `parse_matrix()` / `parse_vector()` (decimal BR, separador automático); `perform_rlm()` (`np.linalg.lstsq`); `perform_bagging()` (Bagging com reposição e Subagging sem reposição); `calc_metrics()` (RMSE, MAE, R²); `run_cross_validation()` (5-fold); `find_optimal_parameters()` (grid search de `m` e `k`); `run_full_analysis()` (retorna `log`, `optimal`, `metrics`, `preds`); log de execução traduzível PT/EN via `_TRADUCOES_LOG` (parâmetro `lang`). |
| `components.py` | Visualização | Cores por modelo (`COR_RLM`, `COR_BAGGING`, `COR_SUBAGGING`, `COR_REAL`); `build_chart()` (real × predito); `build_scatter_chart()` (dispersão com linha ideal y=x); `metric_card_html()`; `APP_CSS`; traduções PT/EN (`_TRADUCOES_COMPONENTES`) e `get_header_html(lang)`. |

Execução:

```bash
pip install streamlit numpy pandas plotly openpyxl scipy pytest
streamlit run app.py
```

Aplicação em produção: <https://app-app-rmn8qdzis5uqkfbmy5pjwr.streamlit.app/>

### Testes — `test_suite_5.py`

Suíte `pytest` com **92 testes** em três classes:

| Classe | Seção | Qtde | Escopo |
|--------|-------|------|--------|
| `TestUnitario` | 4.1 | 21 | Parsing (TXT/CSV), `perform_rlm`, `perform_bagging`, `calc_metrics`, `run_cross_validation` |
| `TestCaixaPreta` | 4.2 | 60 | 12 testes × 5 analitos (Mn, Mo, Cr, Ni, Fe): fidelidade Python × Java. RLM com tolerância 5e-4; Bagging/Subagging com 0,15 (RMSE/MAE) e 5e-3 (R²) |
| `TestStress` | 4.3 | 11 | Tempo e RAM em matrizes 5000×723 e 15000×723; escalabilidade em `m` = 5, 10, 25, 50 |

Execução:

```bash
python -m pytest test_suite_5.py -v
python -m pytest test_suite_5.py -v -k "unitario"   # só 4.1
python -m pytest test_suite_5.py -v -k "caixa"      # só 4.2
python -m pytest test_suite_5.py -v -k "stress"     # só 4.3
```

### Dados simulados — `gerar_dados_simulados.py`

Gera quatro arquivos compatíveis com `parse_matrix()` / `parse_vector()`, para testes de carga com grandes volumes:

- `Xcal_simulado.txt` (30 165 × 723) e `Ycal_simulado.txt` (30 165 × 1)
- `Xteste_simulado.txt` (60 330 × 723) e `Yteste_simulado.txt` (60 330 × 1)

Usa o perfil espectral (média/desvio por comprimento de onda) do `Xcal.txt` real (17 × 723), um modelo latente esparso e resíduos de dois componentes, de modo que a RLM sobre o conjunto de teste reproduza RMSEP = 0,1051, MAE = 0,0887 e R² = 0,9907 (valores do Mn). A escrita é feita em blocos de 5 000 linhas para limitar o uso de RAM. Requer `Xcal.txt` no diretório de execução.

### Sistema legado — `java/BaggingOptimized.java`

Aplicação Swing (pacote `itensvisuais`, Java SE 17) que originou a base algorítmica do TCC I: seleção dos quatro arquivos, campos de `m` e `k`, otimização por validação cruzada 5-fold, avaliação de RLM/Bagging/Subagging (pseudoinversa via EJML `SimpleMatrix`), gráficos JFreeChart e relatório `Resultados_Otimizados_<timestamp>.txt`.

### Resultados de referência Java — `Resultados_Otimizados_<Analito>.txt`

Saídas do sistema Java para Mn, Mo, Cr, Ni e Fe (dimensões, RMSE-CV por `m`/`k`, parâmetros ótimos e métricas finais). São lidas por `_parsear_metricas_java()` em `test_suite_5.py` e servem de referência nos testes de caixa-preta.

| Analito | Xcal | Xteste | Bagging (m*) | Subagging (k*, m*) |
|---------|------|--------|--------------|--------------------|
| Mn | 17 × 723 | 34 × 723 | 30 | 80%, 10 |
| Mo | 17 × 723 | 21 × 723 | 30 | 80%, 30 |
| Cr | 17 × 723 | 34 × 723 | 20 | 80%, 30 |
| Ni | 17 × 723 | 20 × 723 | 30 | 60%, 10 |
| Fe | 17 × 723 | 34 × 723 | 30 | 80%, 30 |

---

## Detalhamento das Seções Textuais

### `1secao.tex` (Introdução)

- Contextualiza a calibração multivariada em aço-ligas (Mn, Cr, Mo, Ni, Fe) e as técnicas *bootstrap*, *bagging* e *subagging* aplicadas à RLM
- Formula o problema de pesquisa, a justificativa em dois eixos (quimiométrico e de engenharia de software) e os objetivos geral e específicos (a)–(d)
- Descreve a trajetória de migração em três estágios (Desktop Java → Vaadin Flow → Python/Streamlit) e resume a suíte de testes (21 + 60 + 11)
- Apresenta a organização do trabalho

### `2secao.tex` (Revisão da Literatura)

- Regressão Linear Múltipla e estimação por pseudoinversa de Moore-Penrose
- Técnica *bootstrap*, reamostragem aleatória, teoria da probabilidade, distribuição empírica e princípio *plug-in*
- *Bagging*, *subagging* e comparação entre ambos (algoritmos e quadro comparativo)
- Fundamentos de engenharia de migração e qualidade de software (Sommerville, reescrita *black-box*, testes de caixa-preta)

### `3secao.tex` (Materiais e Métodos)

- Ferramentas do TCC I (Java SE 17, Eclipse, EJML, JFreeChart, Swing/AWT) e uso declarado de IA como assistente
- Trechos-fonte de `performRLM` e `performBagging` (Java)
- Amostras de aço-ligas: espectrômetro ICP, 723 variáveis, dimensões dos conjuntos de calibração e teste
- Protocolo de validação cruzada 5-fold e grid search de `m` e `k`; definição de RMSEP, MAE e R²

### `4secao.tex` (Resultados e Discussões)

- RMSEP da RLM, *bagging* e *subagging* por analito; sensibilidade ao número de replicações
- Comparação de proporções de calibração (50% e 80%) e tempos de execução
- Comparação *bagging* × *subagging* com parâmetros otimizados por CV (RMSEP, MAE, R², tempo, `k*`, `m*`)
- Análise do custo computacional (figura de tempos com parâmetros otimizados)

### `5secao.tex` (Requisitos Funcionais)

- Inventário de funções, entradas e saídas do sistema
- Priorização MoSCoW (essenciais, desejáveis, extras)
- Fluxo principal (fluxograma TikZ), fluxos alternativos e pontos críticos de usabilidade
- Requisitos não funcionais: performance, usabilidade, segurança e escalabilidade

### `6secao.tex` (Engenharia de Software e Modernização)

- Engenharia de requisitos com Sommerville (elicitação, análise, especificação, validação)
- Requisitos funcionais (RF01–RF12) e não funcionais (RNF01–RNF08) implementados
- Estratégia de migração por reescrita *black-box* e papel do estágio intermediário (Vaadin)
- Mudança de paradigma: MVC (Java/Vaadin) → camadas com Streamlit e `st.session_state`

### `7secao.tex` (Ecossistema de Desenvolvimento)

- Python na computação científica (NumPy, Pandas, SciPy)
- Ciclo de vida do Streamlit: execução top-down, `st.session_state`, *callback* de progresso
- Gerenciamento de memória e oportunidades de `@st.cache_data`
- IDE (VS Code), extensões, qualidade de código e depuração

### `8secao.tex` (Interface e Experiência do Usuário Científica)

- Design centrado em dados: abas (`st.tabs`) × barra lateral (`st.sidebar`), colunas e feedback progressivo
- Visualização interativa com Plotly e padrões de publicação
- Contratos de interface, separação de camadas, *type hints* e princípio aberto/fechado

### `9secao.tex` (Desenvolvimento Iterativo e Validação)

- Quatro *sprints*: motor de dados, algoritmos científicos, interface reativa e otimização com *cache*
- Suíte de 92 testes com `pytest` (unitários, caixa-preta, carga/*stress*) e resultados consolidados
- Exemplo de paridade amostra-a-amostra (Bagging – Cr)

### `10secao.tex` (Conclusão)

- Síntese comparativa por analito (RMSEP, MAE, R², tempo) e recomendação por técnica
- Conclusões de engenharia de software (RNF01, RNF03) e da migração orientada por testes
- Limitações (amostra reduzida, 723 variáveis para 17 amostras, `k*` no limite da grade, tolerâncias amplas) e trabalhos futuros

### `pos/apendice_c.tex` (Paridade Amostra-a-Amostra e Resultado dos Testes)

- Tabelas de paridade Java × Python (Y real, Y predito Java, Y predito Python, Δ) para RLM, *Bagging* e *Subagging* nos cinco analitos
- Saída consolidada do `pytest` (`result_test_consolidados.txt`)

### `pos/apendice_d.tex` (Testes de Gráficos)

- Diagramas de arquitetura em camadas (Java e Python/Streamlit)
- Diagramas de classes, atividades e sequência dos sistemas Java e Streamlit (UML/PlantUML)

---

## Fluxo de Inclusão do Arquivo Raiz

```
TCC_II_IFG_2025.tex
│
├── \input{setup/stylodefinicao}        ← Definições de formatação
│
├── \input{pre/pre}                     ← Elementos pré-textuais
│   ├── capa, folha de rosto
│   ├── pre/fichaCatalografica.tex
│   ├── pre/folhaAprovacao.tex
│   ├── pre/ata.tex
│   └── pre/termo.tex
│
├── \include{tex/1secao}                ← Seção 1: Introdução
├── \include{tex/2secao}                ← Seção 2: Revisão da Literatura
├── \include{tex/3secao}                ← Seção 3: Materiais e Métodos
├── \include{tex/4secao}                ← Seção 4: Resultados e Discussões
├── \include{tex/5secao}                ← Seção 5: Requisitos Funcionais
├── \include{tex/6secao}                ← Seção 6: Engenharia de Software e Modernização
├── \include{tex/7secao}                ← Seção 7: Ecossistema de Desenvolvimento
├── \include{tex/8secao}                ← Seção 8: Interface e Experiência do Usuário
├── \include{tex/9secao}                ← Seção 9: Desenvolvimento Iterativo e Validação
├── \include{tex/10secao}               ← Seção 10: Conclusão
│
├── \bibliography{pos/references}       ← Referências bibliográficas
│
└── pos/apendice_c, pos/apendice_d      ← Apêndices C e D
```

---

## Como Compilar

O documento utiliza a classe `abntex2` com citações numéricas (`abntex2-num`). Para gerar o PDF, recomenda-se a seguinte sequência de compilação a partir da raiz do projeto:

```bash
pdflatex TCC_II_IFG_2025.tex
bibtex TCC_II_IFG_2025
pdflatex TCC_II_IFG_2025.tex
pdflatex TCC_II_IFG_2025.tex
```

Ou, usando `latexmk`:

```bash
latexmk -pdf TCC_II_IFG_2025.tex
```

> **Nota:** Os arquivos `.csv` (`r_bagging.csv`, `r_bagging2.csv`, `rmsep5080.csv`, `rmsepsuperior.csv`) devem estar presentes no diretório raiz, pois são lidos diretamente pelo compilador LaTeX para a geração das tabelas automatizadas.
