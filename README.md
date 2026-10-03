# TCC_II_IFG_2025 — Mapeamento do Projeto

* **Título:** Migração de Sistemas Legados de Análise Química: DE JAVA Desktop Para PYTHON WEB
* **Autor:** Wagner Oliveira de Araujo
* **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia de Goiás — Campus Anápolis
* **Curso:** Bacharelado em Ciência da Computação
* **Trabalho:** TCC II (2026)
* **Orientador:** Prof. Alexandre Bellezi Jose, Me.
* **Coorientador:** Prof. Eder Silva de Brito, Dr.
* **Repositório do legado Java:** <https://github.com/woa2009/MigracaoJava>

---

## Visão Geral do Trabalho

O trabalho tem **dois eixos**:

1. **Quimiométrico:** comparação de RLM clássica, RLM-*bagging* e RLM-*subagging* na calibração multivariada de cinco analitos (Mn, Mo, Cr, Ni, Fe) em amostras de aço-ligas (723 variáveis espectrais; 17 amostras de calibração; 20–34 amostras de teste), com hiperparâmetros `m` e `k` otimizados por validação cruzada 5-fold (*grid search*).
2. **Engenharia de software:** reescrita *black-box* em três estágios (Java Desktop → Vaadin/Spring → Python/Streamlit), com arquitetura em três módulos (`models.py`, `components.py`, `app.py`) validada por **92 testes automatizados** (21 unitários, 60 de caixa-preta, 11 de carga/*stress*).

---

## Arquivo Raiz

### `TCC_II_IFG_2025.tex`

Ponto de entrada principal do documento LaTeX. Responsável por:

- Configurar a classe `abntex2` com as opções da instituição (IFG)
- Carregar todos os pacotes utilizados (tipografia, TikZ/pgfplots, `algorithm2e`, `siunitx`, `threeparttable`, `booktabs`, `multirow`, `tabularx`, `listings`, `fancyvrb`, `float`, `subcaption`, referências ABNT etc.)
- Declarar metadados do trabalho (autor, título, orientadores, ano, local) e o comando `\oautor`
- Definir a lista de siglas (`\siglalista`), de símbolos (`\simbololista`) e as entradas de glossário usadas via `\gls{...}` (EJML, IDE, RMSEP, MAE, MoSCoW, WCAG, MVP, Xcal, Ycal, Xteste, yteste etc.)
- Carregar dados de tabelas a partir de arquivos `.csv` (`r_bagging.csv`, `r_bagging2.csv`, `rmsep5080.csv`, `rmsepsuperior.csv`), expostos como `\dados`, `\rmsepdados` e `\rmsepmaior`
- Declarar os ambientes `codigo` (usado no Apêndice B) e `quadro` (definido em `ufscthesisA4-alf.sty`)
- Incluir os elementos pré-textuais, textuais e pós-textuais via `\input` e `\include`

---

## Estrutura de Diretórios

```
B_Projeto_Integrador_III_Final/
│
├── TCC_II_IFG_2025.tex          ← Arquivo raiz do documento
│
├── setup/                       ← Configurações e estilos LaTeX
│   ├── ufscthesisA4-alf.sty     ← Estilo principal (origem UFSC, customizado para o IFG)
│   ├── stylodefinicao.tex       ← Definições de formatação personalizadas
│   ├── algorithm2e.sty          ← Pacote para exibição de algoritmos
│   └── defs.ldf                 ← Definições de idioma
│
├── pre/                         ← Elementos pré-textuais
│   ├── pre.tex                  ← Orquestra todos os elementos pré-textuais
│   ├── fichaCatalografica.tex   ← Ficha catalográfica
│   ├── folhaAprovacao.tex       ← Folha de aprovação (ambiente `folhaaprovacao`)
│   ├── ata.tex                  ← Ata de defesa (ambiente `atareuniao`)
│   └── termo.tex                ← Termo de compromisso/autorização
│
├── tex/                         ← Seções e conteúdo textual
│   ├── 1secao.tex               ← Cap. 1: Introdução
│   ├── 2secao.tex               ← Cap. 2: Revisão da Literatura
│   ├── 3secao.tex               ← Cap. 3: Materiais e Métodos
│   ├── 4secao.tex               ← Cap. 4: Análise Experimental dos Algoritmos Quimiométricos
│   ├── 5secao.tex               ← Cap. 5: Requisitos Funcionais
│   ├── 6secao.tex               ← Cap. 6: Engenharia de Software e Modernização
│   ├── 7secao.tex               ← Cap. 7: Resultados e Discussões
│   ├── 8secao.tex               ← Cap. 8: Interface e Experiência do Usuário (UI/UX) Científica
│   ├── 9secao.tex               ← Cap. 9: Desenvolvimento Iterativo por Sprints e Validação por Testes
│   ├── 10secao.tex              ← Cap. 10: Conclusão
│   ├── algoritmos.tex           ← Algoritmos utilizados no trabalho
│   ├── graficos.tex             ← Código TikZ/pgfplots para os gráficos
│   ├── apoio_4secao.tex         ← Material de apoio para o Cap. 4
│   ├── apoio_subagging.tex      ← Material de apoio sobre subagging
│   ├── discussao.tex            ← Texto auxiliar de discussão
│   ├── pesquisa.tex             ← Texto de pesquisa/levantamento bibliográfico
│   ├── YtesteMn.txt, YtesteFe.txt                      ← Concentração de referência (Fig. RMSEP com RLM)
│   ├── CpredMn.txt, CpredFe.txt                        ← Predições da RLM
│   ├── baggingCpredMn.txt, BaggingCpredFe.txt          ← Predições do RLM-bagging
│   ├── SubaggingCpredMn.txt, SubaggingCpredFe.txt      ← Predições do RLM-subagging
│   ├── bagging_mn.txt, bagging_fe.txt                  ← RMSEP × nº de replicações (bagging)
│   ├── bootstrap_mn.txt, bootstrap_fe.txt              ← RMSEP × nº de replicações (subagging)
│   └── dados/                   ← Séries para a comparação das três técnicas (Fig. 4.x)
│       ├── bagging_fe.txt / bagging_mn.txt
│       ├── bootstrap_fe.txt / bootstrap_mn.txt
│       ├── rlm_fe.txt / rlm_mn.txt
│       └── subagging_fe.txt / subagging_mn.txt
│
├── pos/                         ← Elementos pós-textuais
│   ├── references.bib           ← Arquivo principal de referências (BibTeX)
│   ├── references1.bib          ← Referências complementares (versão anterior)
│   ├── apendice_a.tex           ← Apêndice A (incluído mas desabilitado no raiz)
│   ├── apendice_c.tex           ← Apêndice: Paridade amostra-a-amostra Java × Python + Resultado dos Testes
│   ├── apendice_d.tex           ← Apêndice: Testes de Gráficos (diagramas de arquitetura, UML e PlantUML)
│   ├── result_test_consolidados.txt ← Saída bruta do pytest (lida via \VerbatimInput no apêndice_c)
│   ├── anexo_a.tex              ← Anexo A (incluído mas desabilitado no raiz)
│   └── [outros .bib]            ← Arquivos de referências individuais por fonte
│
├── outros/                      ← Recursos auxiliares do projeto
│   ├── fig/                     ← Figuras e imagens utilizadas no documento
│   │   ├── bootstrap.png / subagging.png / resultado_final.(png|eps)
│   │   ├── RLM_Bagging.pdf / BootStrapRMSEPFe.pdf
│   │   ├── IFGAnápolisH.jpg     ← Logomarca da capa (usada em \imprimircapa)
│   │   ├── IFGAnapolisHor2.png  ← Logomarca horizontal (usada na ata)
│   │   ├── logoIFG.jpg          ← Logomarca IFG alternativa
│   │   ├── E_Diagramas/out/     ← Diagramas gerados (Apêndice D)
│   │   │   ├── diag_classe/BaggingOptimized_Classe.png
│   │   │   ├── diag_sequencia/BaggingOptimized_Atividade.png
│   │   │   ├── diagrama/BaggingOptimized_FluxoCompleto.png
│   │   │   ├── diagrama02/Etapa2_GridSearch_CV.png
│   │   │   └── ../streamlit/ diagrama_atividades_ | diagrama_classes_ | diagrama_sequencia_streamlit.png
│   │   └── [outras figuras]     ← Figuras históricas/legadas (.eps, .pdf, .jpg, .png)
│   └── prog/                    ← Scripts e dados de programas auxiliares
│       ├── dados_Fe.txt / dados_Mn.txt / dados_Cr.txt / dados_Ni.txt / dados_Mo.txt
│       │                        ← Espectros médios plotados na Fig. "Espectros médios dos analitos"
│       ├── bagging.txt / subbagging.txt
│       └── insertionsort.c      ← Código C auxiliar (insertion sort)
│
├── pdf_old/                     ← PDFs de versões anteriores do trabalho
│
├── references.bib               ← Cópia de referências na raiz
├── r_bagging.csv                ← Dados CSV lidos diretamente pelo .tex raiz
├── r_bagging2.csv
├── rmsep5080.csv                ← RMSEP para proporções de calibração de 50% e 80%
├── rmsepsuperior.csv            ← Menor RMSEP por analito (Tabela de técnica vencedora)
├── subfigure.sty                ← Pacote de subfiguras (legado)
│
└── [arquivos gerados pela compilação LaTeX]
    ├── TCC_II_IFG_2025.pdf / .aux / .bbl / .blg / .toc / .lof / .lot
    └── .idx / .ind / .ilg / .log
```

---

## Detalhamento das Seções Textuais

### `1secao.tex` — Introdução (`cha:introducao`)

- Contextualiza a calibração multivariada na análise de aço-ligas (Mn, Cr, Mo, Ni, Fe) e a aplicação exploratória de *bootstrap*, *bagging* e *subagging* à RLM
- Formula o problema de pesquisa (calibração mais precisa + arquitetura modular verificável por testes)
- Declara a contribuição em dois eixos (quimiométrico e engenharia de software) e a ressalva sobre o conjunto amostral reduzido
- Define o objetivo geral e os objetivos específicos (a–e): aplicar as técnicas, comparar RLM/bagging/subagging, reaproveitar o sistema Java (JavaSE-17, EJML, Swing/AWT) como referência, desenvolver o protótipo Python 3.12/Streamlit e garantir equivalência com 92 testes `pytest`
- Apresenta a organização do trabalho (⚠ o parágrafo final cita apenas as Seções 2 e 2.x; ver "Pontos de Atenção")

---

### `2secao.tex` — Revisão da Literatura (`cha:tecboot`)

- Regressão Linear Múltipla: modelo, forma matricial, estimação por MQO/pseudo-inversa de Moore-Penrose, premissas e métodos robustos (o bloco antigo está dentro de `\begin{comment}`)
- Técnica de *bootstrap*: estimativa, replicações, número de replicações `m` (coeficiente de variação, regras de Efron), Algoritmo `alg:bootstrap`
- Reamostragem aleatória, teoria da probabilidade, função de distribuição empírica e princípio *plug-in*
- Técnicas clássicas de reamostragem: *bagging* (Algoritmo `alg:bagging`), *subagging* (Algoritmo `alg:subagging`) e Quadro comparativo `tab:bag-vs-subag`
- **Fundamentos de Engenharia de Migração e Qualidade de Software** (`sec:fundengsw`): engenharia de requisitos (Sommerville), reescrita *black-box* e testes de caixa-preta (Pressman)

---

### `3secao.tex` — Materiais e Métodos (`cha:metresult`)

- Ferramentas do sistema legado (Java, Eclipse, EJML 0.43.1, JFreeChart 1.5.4, Swing/AWT) e declaração de uso de IA generativa como ferramenta de apoio
- Fragmentos do código-fonte Java: `performRLM` (Fig. `lst:performrlm`) e `performBagging` (Fig. `lst:performbagging`)
- Amostras de aço-ligas: espectrômetro ICP, 723 variáveis, espectros médios (Fig. `fig:espectros`, lidos de `outros/prog/dados_*.txt`) e Quadro de dimensões dos conjuntos (17 × 723 de calibração; teste de 34, 21, 34, 20 e 34 amostras para Mn, Mo, Cr, Ni e Fe, conforme o Quadro)
- **Protocolo de validação e seleção de hiperparâmetros** (`sec:protocolo`): CV 5-fold apenas na calibração, `seed = 42`, grade `m ∈ {10,20,30,40,50}` e `k ∈ {0,50; 0,60; 0,70; 0,80}`, Equação do RMSEP-CV
- Métricas de avaliação: RMSEP, MAE e R² (Equações `eq:rmsep`, `eq:mae`, `eq:r2`)

---

### `4secao.tex` — Análise Experimental dos Algoritmos Quimiométricos (`sec:result`)

- RMSEP da RLM por analito (Tabela `tab:rmseprlm`) e predições de Mn e Fe
- *Bagging*: sensibilidade ao número de replicações (Figs. `fig:Figura42`, `fig:Figura43`) e comparação RLM × RLM-*bagging* sem otimização formal (Tabela `tab:bagging`)
- *Subagging*: sensibilidade (Fig. `fig:Figura45`), Tabela `tab:subagging` e Figura `fig:Figura46`
- Proporções de calibração 50% × 80% (Tabela `tab:comparacao_50_80`), técnica vencedora por elemento (Tabela `tab:melhor_rmseep`) e impacto de `m`
- Tempos de execução com 50% e 80% das amostras (Fig. `fig:tempo_comparacao`)
- **Bagging × Subagging com parâmetros otimizados por CV 5-fold** (Tabela `tab:baggingsubba` e Fig. `fig:tempo`): Mn e Ni → subagging; Fe → bagging; Mo e Cr → RLM clássica; custo computacional médio 3,0× menor no subagging (exceto Cr)

---

### `5secao.tex` — Requisitos Funcionais (`sec:reqfunc`)

- Inventário de funcionalidades, entradas e saídas (Quadros `tab:funcoes`, `tab:entradas`, `tab:saidas`)
- Classificação MoSCoW: essenciais (E01–E05), desejáveis (D01–D05) e extras (X01–X05)
- Fluxo principal em TikZ (Fig. `fig:figura00`), fluxos alternativos/exceções e pontos críticos de usabilidade
- Requisitos não funcionais: performance, usabilidade (WCAG 2.1 AA), segurança, escalabilidade
- Considerações finais do levantamento (prioridades para o MVP)

---

### `6secao.tex` — Engenharia de Software e Modernização (`sec:engenhariasoftware`)

- Engenharia de requisitos segundo Sommerville aplicada à migração: elicitação, análise, especificação e validação
- Mapeamento do `RegressionService.java` para os módulos Python e contratos com *type hints*
- Arquitetura modular em três camadas: `models.py` (núcleo matemático, `np.linalg.lstsq`), `components.py` (fábrica de gráficos Plotly) e `app.py` (orquestrador Streamlit/`session_state`)

---

### `7secao.tex` — Resultados e Discussões (`sec:resultados`)

- Síntese da avaliação preditiva dos cinco analitos: RLM clássica melhor para Mo e Cr; *bagging* melhor para Fe; *subagging* melhor ou equivalente para Mn e Ni
- Eficiência computacional: *subagging* mais rápido que *bagging* em quatro dos cinco analitos, atribuído às subamostras menores (`k < 1`)
- Indica como trabalho futuro a decomposição viés–variância e a análise físico-química

---

### `8secao.tex` — Interface e Experiência do Usuário (UI/UX) Científica (`sec:uiux`)

- Design da interface Streamlit e fluxo de trabalho em três abas: Configuração e Carga de Dados, Resultados Numéricos e Logs, Visualização Gráfica
- Acesso simultâneo via navegador, sem instalação local de dependências, sujeito aos limites da plataforma de hospedagem

---

### `9secao.tex` — Desenvolvimento Iterativo por Sprints e Validação por Testes Automatizados

- Metodologia ágil em quatro *sprints*: (1) leitura e tratamento de dados, (2) algoritmos científicos, (3) interface reativa, (4) otimização com *cache* (`@st.cache_data`, ganho não medido)
- **Suíte `pytest` com 92 testes** (`sec:testescaixapreta`): 21 unitários, 60 de caixa-preta (12 testes × 5 analitos; tolerância 5×10⁻⁴ para a RLM; 0,15 / 5×10⁻³ para *ensembles*) e 11 de carga/*stress* (`tracemalloc`, `perf_counter`)
- Resultados consolidados e define a macro `\testes` (tempo de execução da suíte), **reutilizada no Apêndice B**
- Tabela de paridade *Bagging* — Cr (`tab:paridade_bagging_cr`); as demais estão no Apêndice A

---

### `10secao.tex` — Conclusão (`sec:conclusao`)

- Síntese dos dois eixos (quimiométrico e engenharia de software)
- Limitações (`sec:limitacoes`): ausência de testes formais de hipótese/decomposição viés–variância, latência do *cache* não medida e calibração limitada às amostras reais disponíveis
- Trabalhos futuros: agente de IA para interpretação dos gráficos, ampliação do conjunto amostral e testes de carga em nuvem sob acessos concorrentes

---

## Apêndices (arquivos enviados)

### `apendice_c.tex` — Paridade Amostra-a-Amostra (`cha:paridadeamostra`) e Resultado dos Testes (`cha:resultadotestes`)

- 15 tabelas de paridade Java × Python (5 analitos × RLM, *Bagging*, *Subagging*), com Y real, Y predito (Java), Y predito (Python) e Δ (todos zero), formatadas com colunas `S` do `siunitx`
- Capítulo "Resultado dos Testes": saída bruta do `pytest` 9.1.0 (Python 3.12.10, Windows) incluída com `\VerbatimInput{pos/result_test_consolidados.txt}` (Código `code:codi5`)

### `apendice_d.tex` — Testes de Gráficos (`cha:testesgraficos`)

- Diagramas de arquitetura em camadas (Java monolítico × Python/Streamlit, TikZ)
- Diagramas UML/PlantUML: classes, atividades e sequência do sistema Java; atividades, classes (módulos) e sequência do sistema Streamlit

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
├── \include{tex/1secao}                ← Cap. 1: Introdução
├── \include{tex/2secao}                ← Cap. 2: Revisão da Literatura
├── \include{tex/3secao}                ← Cap. 3: Materiais e Métodos
├── \include{tex/4secao}                ← Cap. 4: Análise Experimental dos Algoritmos Quimiométricos
├── \include{tex/5secao}                ← Cap. 5: Requisitos Funcionais
├── \include{tex/6secao}                ← Cap. 6: Engenharia de Software e Modernização
├── \include{tex/7secao}                ← Cap. 7: Resultados e Discussões
├── \include{tex/8secao}                ← Cap. 8: Interface e Experiência do Usuário (UI/UX)
├── \include{tex/9secao}                ← Cap. 9: Sprints e Validação por Testes   (define \testes)
├── \include{tex/10secao}               ← Cap. 10: Conclusão
│
├── \bibliography{pos/references}       ← Referências bibliográficas
│
└── Apêndices
    ├── pos/apendice_c                  ← Paridade Java × Python + Resultado dos Testes (usa \testes)
    └── pos/apendice_d                  ← Testes de Gráficos (diagramas)
```

> A ordem acima é a ordem numérica natural dos arquivos; confirme no `TCC_II_IFG_2025.tex`, que não foi enviado junto.
> Atenção: no README anterior `5secao.tex` era a Conclusão e `6secao.tex` os Requisitos — a numeração dos arquivos agora segue a numeração dos capítulos.

---

## Estilo `ufscthesisA4-alf.sty`

Customização do abnTeX2 (origem UFSC, adaptada ao IFG Anápolis). Principais recursos:

- Fonte Latin Modern; cabeçalho com `fancyhdr`; "Capítulo" renomeado para "Seção" nos cabeçalhos
- Pacote `glossaries` com siglas (`\siglalista`), símbolos (`\simbololista`), glossário e comandos `\imprimirlistadesiglas`, `\imprimirlistadesimbolos`, `\imprimirglossario`
- Equação numerada continuamente (`\counterwithout{equation}{chapter}`)
- Novo float **`quadro`** com lista de quadros (`\listofquadros`), numeração contínua e regras ABNT
- Capa (`\imprimircapa`, usa `outros/fig/IFGAnápolisH.jpg`) e folha de rosto reformatadas
- Ambientes `folhaaprovacao` e `atareuniao` (ata nº 20/ano, usa `outros/fig/IFGAnapolisHor2.png`; requer `\ministerio`, `\secretaria`, `\instituto`, `\reitoria`)
- Comandos de metadados adicionais: `\subtitulo`, `\programa`, `\formacao`, `\nivel`, `\area`, `\centro`, `\coordenador` etc.

---

## Código e Dados de Apoio ao Documento

| Arquivo | Função |
|---|---|
| `BaggingOptimized.java` | Sistema legado (Java/Swing/EJML), v3.0 — referência de validação; gera `Resultados_Otimizados_*.txt` |
| `Resultados_Otimizados_{Mn,Mo,Cr,Ni,Fe}.txt` | Saídas do sistema Java (CV 5-fold + métricas de teste) — fonte da Tabela `tab:baggingsubba` e do teste de caixa-preta |
| `models.py` / `components.py` / `app.py` | Sistema Python/Streamlit (núcleo matemático, gráficos Plotly, interface) |
| `test_suite_5.py` | Suíte `pytest` de 92 testes (4.1 unitários, 4.2 caixa-preta, 4.3 *stress*) |
| `gerar_dados_simulados.py` | Gerador de dados espectrais sintéticos (30.165 × 723 de calibração e 60.330 × 723 de teste) para os testes de carga |

---

## Como Compilar

O documento utiliza a classe `abntex2` com citações numéricas (`abntex2-num`). Para gerar o PDF, recomenda-se a seguinte sequência a partir da raiz do projeto:

```bash
pdflatex TCC_II_IFG_2025.tex
bibtex TCC_II_IFG_2025
makeglossaries TCC_II_IFG_2025   # se as listas de siglas/símbolos usarem glossaries (modo noidx: ver logs)
pdflatex TCC_II_IFG_2025.tex
pdflatex TCC_II_IFG_2025.tex
```

Ou, usando `latexmk`:

```bash
latexmk -pdf TCC_II_IFG_2025.tex
```

> **Notas:**
> - Os arquivos `.csv` (`r_bagging.csv`, `r_bagging2.csv`, `rmsep5080.csv`, `rmsepsuperior.csv`) devem estar na raiz, pois são lidos diretamente pelo LaTeX.
> - Os `.txt` plotados com `pgfplots` precisam estar nos caminhos relativos indicados (`tex/`, `tex/dados/`, `outros/prog/`).
> - `pos/result_test_consolidados.txt` precisa existir, senão o Apêndice B falha.
> - Para executar o sistema Python: `streamlit run app.py`; para os testes: `python -m pytest test_suite_5.py -v`.

---

## Pontos de Atenção Identificados nos `.tex`

1. **Rótulo duplicado:** `sec:bagxsuagg` é definido tanto em `2secao.tex` (subseção "Comparação entre *Bagging* e *Subagging*") quanto em `4secao.tex` — gera aviso *multiply defined* e referências ambíguas.
2. **Erro de digitação em `4secao.tex`:** na Figura `fig:Figura46b`, `mark=nome` deve ser `mark=none`.
3. **Pendências marcadas:** `% TODO: citar fonte` (autoabsorção do Fe e sobreposição espectral do Cr) em `4secao.tex`.
4. **Resumo de organização desatualizado:** o último parágrafo de `1secao.tex` descreve só as Seções 2.x; vale listar os 10 capítulos atuais.
5. **Inconsistências entre texto e código:**
   - `5secao.tex` cita quatro abas ("Arquivos", "Configuração", "Resultados", "Gráficos"); `8secao.tex` e `app.py` têm três;
   - `5secao.tex` lista apenas `.txt` nas entradas, enquanto `.csv` e `.xlsx` já estão implementados (X03 consta como *Could Have*);
   - `6secao.tex` mostra `parse_matrix(content: bytes)`, mas o código recebe `file_obj`;
   - `8secao.tex` menciona "superfícies de erro" na aba de gráficos, que não existem em `components.py`.
6. **Grafia:** "Mangânes" (deveria ser "Manganês") nas notas das tabelas de Mn em `apendice_c.tex`.
7. **Dependência entre arquivos:** `\testes` é definido em `9secao.tex` e usado em `apendice_c.tex`; a ordem de inclusão deve ser preservada.
