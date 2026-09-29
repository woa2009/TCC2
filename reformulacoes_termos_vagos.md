# Reformulações de termos vagos — TCC II

Convenções: **Antes** é o trecho atual; **Depois** é a proposta em LaTeX. `[TODO]` marca dado, citação ou medição que só você pode fornecer. Nenhum número novo foi inventado: todos os valores saem das tabelas do próprio trabalho (recalculados quando indicado).

---

## 0. Bloco `\include` corrigido (`TCC_II_IFG_2026.tex`)

```latex
% ---
% Seções textuais, na ordem da numeração dos arquivos
% ---
\include{tex/1secao}    % Seção 1  - Introdução
\include{tex/2secao}    % Seção 2  - Revisão da literatura
\include{tex/3secao}    % Seção 3  - Materiais e Métodos
\include{tex/4secao}    % Seção 4  - Resultados e Discussões
\include{tex/5secao}    % Seção 5  - Requisitos Funcionais
\include{tex/6secao}    % Seção 6  - Engenharia de Software e Modernização
\include{tex/7secao}    % Seção 7  - Ecossistema de Desenvolvimento (Python e Streamlit)
\include{tex/8secao}    % Seção 8  - Interface e Experiência do Usuário (UI/UX) Científica
\include{tex/9secao}    % Seção 9  - Desenvolvimento Iterativo por Sprints e Testes
\include{tex/10secao}   % Seção 10 - Conclusão
```

Atualmente a ordem é `4, 6, 7, 8, 9, 10, 5`, o que põe Requisitos Funcionais depois da Conclusão e deixa os comentários desatualizados. Depois de reordenar, compile duas vezes, porque as referências cruzadas (`\ref`) dependem do `.aux`.

---

## 1. `4secao.tex` — Resultados e Discussões

### 1.1 Parágrafo de abertura da subseção da RLM (linha ~99)

**Antes**
> Pode ser visto na Tabela~\ref{tab:rmseprlm} que o Mn apresenta o menor RMSEP entre os três métodos, com destaque para o RLM-subagging (0,0974). Por outro lado, o Fe apresenta o maior RMSEP, com o valor mais elevado obtido pela RLM (2,7513). De forma geral, o RLM-subagging apresentou desempenho superior ao RLM-bagging na maioria dos elementos analisados […]

**Problemas:** a Tabela `tab:rmseprlm` mostra só a RLM, então "entre os três métodos" não se sustenta nela. O valor 0,0974 diverge do 0,0966 da Tabela `tab:baggingsubba`. "Na maioria" não tem contagem.

**Depois**
```latex
A Tabela~\ref{tab:rmseprlm} mostra que, para a RLM, o Mn apresenta o menor RMSEP
(\num{\dados[2,2]}) e o Fe o maior (\num{\dados[2,6]}). Na comparação com parâmetros
otimizados (Tabela~\ref{tab:baggingsubba}), o RLM-\textit{subagging} obteve RMSEP menor
que o RLM-\textit{bagging} em quatro dos cinco analitos (Mn, Mo, Cr e Ni), e a RLM
clássica obteve o menor RMSEP entre as três técnicas em dois analitos (Mo e Cr). Isso
indica que a técnica mais adequada depende do analito.
```
`[TODO]` Reconciliar 0,0974 (subagging com *m* fixo) com 0,0966 (com CV) e dizer de qual experimento vem cada um.

### 1.2 Justificativa de Mn e Fe como analitos ilustrativos

**Antes**
> Acredita-se que o comportamento destas duas amostras são suficientes para ilustrar o comportamento geral esperado para as outras amostras.

**Problemas:** "acredita-se" e "suficientes" são inverificáveis, há erro de concordância e "amostras" está no lugar de "analitos".

**Depois**
```latex
Mn e Fe foram escolhidos como analitos ilustrativos nas figuras desta seção; os
resultados dos cinco analitos são apresentados na Tabela~\ref{tab:baggingsubba}.
```

### 1.3 Sensibilidade do *bagging* ao número de replicações (linha ~167)

**Antes** (trechos)
> …comportamento mais estável após (15–20) replicações… menor variabilidade absoluta… **considerável** variabilidade para ambos… desempenho variando de 34% a 41%, indicando **sensibilidade elevada**… O Manganês apresenta tendência de estabilização após aproximadamente 20 replicações… Isso sugere que […] a predição do Fe é **inerentemente** mais difícil que a do Mn. Os valores apresentados na **Figura 6**… **Tabelas 5 e 9**.

**Problemas:** adjetivos sem critério; "34% a 41%" não diz de quê; "inerentemente" é uma causa não testada; a estabilização aparece duas vezes; a numeração da figura e das tabelas está escrita à mão.

**Depois**
```latex
Para o Mn, o RMSEP tende a se estabilizar entre \num{0,026} e \num{0,030} a partir de
15--20 replicações. Para o Fe, o RMSEP oscila entre \num{1,3} e \num{2,2} em todo o
intervalo de 1 a 50 replicações, sem estabilização observável. [TODO: definir a grandeza
a que se refere o intervalo de 34\% a 41\% (ex.: variação relativa do RMSEP entre quais
condições) ou remover a frase.] Duas hipóteses são compatíveis com esse comportamento:
o Fe pode exigir mais de 50 replicações, ou sua predição pode ser mais difícil que a do
Mn; o experimento não permite distingui-las. Os valores da Figura~\ref{fig:Figura42}
foram obtidos com o conjunto de calibração completo, em análise de sensibilidade
interna, e podem diferir dos valores do conjunto de teste independente reportados nas
Tabelas~\ref{tab:bagging} e~\ref{tab:baggingsubba}.
```

### 1.4 Efeito da proporção de calibração (80%)

**Antes:** "…resultou em desempenho superior… para a **grande maioria** dos casos analisados."

**Depois**
```latex
…resultou em menor RMSEP em 14 das 15 combinações analito~$\times$~técnica; a única
exceção foi a RLM clássica para o Cr.
```
(Contagem conferida no próprio texto: 5 + 5 casos de *ensemble* mais 4 de 5 da RLM.)

### 1.5 Tempos de execução, cenários 50% e 80% (linhas ~644–662)

**Antes → Depois**

| Antes | Depois |
|---|---|
| "revela diferenças **significativas** entre os três algoritmos" | "apresenta os tempos de execução dos três algoritmos com 50% e 80% das amostras" (sem teste estatístico, evite "significativas") |
| "variação **considerável** entre elementos (1,1× para Ni até 3,1× para Fe)" | "variando de 1,1× (Ni) a 3,1× (Fe)" |
| "comportamento igualmente **heterogêneo** entre os analitos" | "variando de `[TODO: mín]`× a `[TODO: máx]`× entre os analitos" |
| "Este crescimento **expressivo**… número **substancialmente maior** de iterações" | "Esse aumento, de 8,5× (Mn) a 21,7× (Cr), é compatível com o maior número de iterações exigido pelos parâmetros ótimos *m*\* e *k*\* com 80% das amostras (`[TODO: citar os valores de m*·k* nos dois cenários]`)" |

### 1.6 Comparação de tempo com parâmetros otimizados (antes da Figura `fig:tempo`)

**Antes**
> Em média, o RLM-subagging é aproximadamente 3,0 vezes mais rápido, representando uma redução de **66,7%** no tempo de execução.

**Problema:** 66,7% é 1 − 1/3, derivado da razão média, e não do tempo total. Pela Tabela `tab:baggingsubba`, a soma dos tempos é 344,0 ms (*bagging*) contra 162,5 ms (*subagging*), uma redução de **52,8%**. A Conclusão já usa "cerca de 53%", então o texto se contradiz.

**Depois**
```latex
Em quatro dos cinco analitos (Mn, Mo, Ni e Fe), o RLM-\textit{subagging} foi mais
rápido que o RLM-\textit{bagging}. A razão média entre os tempos (\textit{bagging}/\textit{subagging})
foi \num{3,0}, variando de \num{0,95} (Cr) a \num{6,3} (Ni); a soma dos tempos dos
cinco analitos é 52,8\% menor no \textit{subagging} (\SI{162,5}{ms} contra \SI{344,0}{ms}).
```
(Os valores da figura, ex.: 0,0683 s, diferem em ±0,1 ms dos da tabela, ex.: 68,2 ms; use a tabela como fonte única.)

### 1.7 Causa da eficiência do *subagging* e caso do Cr

**Antes**
> Essa eficiência **decorre** da amostragem sem reposição… operações matriciais **mais ágeis** e **menor redundância**…
> Esse comportamento **é explicado** pelos parâmetros ótimos… custo computacional **equivalente**…

**Depois**
```latex
A menor duração do \textit{subagging} é compatível com o uso de subconjuntos menores
($k^* \leq 80\%$ das amostras), que reduzem a dimensão de cada problema de mínimos
quadrados; este trabalho não isolou esse efeito experimentalmente.

O Cromo (Cr) é o único analito em que o RLM-\textit{subagging} foi mais lento que o
RLM-\textit{bagging} (\SI{46,8}{ms} contra \SI{44,5}{ms}; diferença de \SI{2,3}{ms}, ou
5,2\%). Esse resultado é consistente com os parâmetros selecionados por validação
cruzada: $m^*=20$ para o \textit{bagging} e $m^*=30$ com $k^*=80\%$ para o
\textit{subagging}.
```

### 1.8 Interpretação espectral (Fe, Cr, Mn, Mo)

**Antes**
> …características que **introduzem** não-linearidades e instabilidade no modelo base… Para Mn e Mo, cujas linhas analíticas apresentam **menor interferência matricial**, a relação espectral-concentração é **suficientemente bem** capturada pela RLM clássica.

**Problemas:** as causas são afirmadas sem teste nem citação, e a última frase contradiz a tabela: para o Mn o melhor método foi o *subagging* (0,0966 contra 0,1051 da RLM), não a RLM.

**Depois**
```latex
Para o Fe, o RLM-\textit{bagging} obteve o menor RMSEP (\num{2,6406}). Uma hipótese
para esse resultado é que o Fe, por ser o elemento matriz, apresente espectro de alta
densidade e possível autoabsorção~\cite{[TODO]}, o que tornaria o modelo base mais
instável e favoreceria a agregação; este trabalho não testou essa hipótese. Para o Cr,
apesar da sobreposição espectral com linhas do Fe e do Ni~\cite{[TODO]}, nenhuma
técnica de \textit{ensemble} superou a RLM clássica (RMSEP = \num{1,0798}). Uma
interpretação possível é que, com 17 amostras de calibração, a redução de variância do
\textit{ensemble} não compensou o viés introduzido pela reamostragem; essa
interpretação também carece de verificação direta (ex.: decomposição viés--variância).
Para o Mo, a RLM clássica obteve o menor RMSEP (\num{0,2633}); para o Mn, o
RLM-\textit{subagging} obteve o menor RMSEP (\num{0,0966}), 8,1\% abaixo da RLM.
```

### 1.9 Fecho da seção

**Antes**
> …custo computacional **significativamente** superior, com o RLM-bagging sendo em média **21,9** vezes mais lento e o RLM-subagging até **19,4** vezes… o RLM-subagging configura-se como **alternativa equilibrada**…, sendo preferível ao RLM-bagging **na maioria** dos cenários avaliados.

**Problemas:** os valores divergem da própria Tabela e da Conclusão. Recalculando a partir da Tabela `tab:baggingsubba` (razões com o tempo da RLM), a média do *bagging* é **22,1×** e o máximo do *subagging* é **19,5×** (Mo). "Equilibrada" e "na maioria" não têm critério.

**Depois**
```latex
Em relação à RLM clássica, o custo computacional dos \textit{ensembles} é maior: o
RLM-\textit{bagging} foi, em média, 22,1 vezes mais lento e o RLM-\textit{subagging}
até 19,5 vezes mais lento (Mo). Comparado ao RLM-\textit{bagging}, o
RLM-\textit{subagging} obteve menor RMSEP em quatro analitos (Mn, Mo, Cr e Ni) e menor
tempo em quatro (Mn, Mo, Ni e Fe), superando-o simultaneamente nos dois critérios em
Mn, Mo e Ni.
```

### 1.10 Figuras 7, 9 e 11 (verificar)

- Cada subfigura (a) lê `tex/YtesteMn.txt` e `tex/CpredMn.txt` (e as (b) os de Fe). Os **mesmos arquivos** aparecem nas Figuras 7 (RLM), 9 (*bagging*) e 11 (*subagging*), ou seja, três figuras com dados idênticos. Se as predições de cada método estão em arquivos diferentes, os caminhos precisam ser corrigidos.
- O texto diz "azul = esperada, vermelho = predita", mas o código plota `Yteste` em **vermelho** e a legenda `{Conc. pred., Conc. ref.}` rotula a primeira série (vermelha, `Yteste`) como "pred.". Texto, cor e legenda precisam concordar.

---

## 2. `10secao.tex` — Conclusão

| Antes | Depois |
|---|---|
| "atende aos objetivos propostos, dentro das limitações discutidas" | "aborda os objetivos específicos (a)–(d) da Seção~\ref{cha:introducao}, dentro das limitações discutidas ao final desta seção" |
| "Todos os modelos apresentam coeficiente de determinação superior a 0,98…, o que evidencia **elevada capacidade preditiva**" | "Os valores de R$^2$ variaram de \num{0,9805} (RLM-*bagging*, Mo) a \num{0,9938} (RLM, Cr) no conjunto de teste." |
| "A análise da eficiência computacional mostra diferenças **expressivas** entre os métodos" | "Os tempos medidos foram de \SI{2,3}{}–\SI{13,5}{ms} (RLM), \SI{44,5}{}–\SI{97,2}{ms} (*bagging*) e \SI{10,6}{}–\SI{46,8}{ms} (*subagging*)." |
| "O RLM-*subagging* ocupa **posição intermediária**: […] em média, 3,0 vezes mais rápido, com variação entre 1,4 vez (Mo) e 6,3 vezes (Ni)" | "A razão média entre os tempos do *bagging* e do *subagging* foi 3,0, de 0,95 (Cr) a 6,3 (Ni)." (o Cr, com 0,95, é a exceção que o próprio texto cita depois) |
| "Para Mn e Ni, o RLM-*subagging* apresenta dominância de Pareto sobre o RLM-*bagging*" | "…sobre o RLM-*bagging* em Mn, Mo e Ni" (o Mo também cumpre: RMSEP 0,2879 < 0,3388, MAE 0,2201 < 0,2722, tempo 46,8 < 67,5 ms) |
| "o RLM-*subagging* é a alternativa **mais equilibrada** entre precisão e eficiência" | "o RLM-*subagging* obteve menor RMSEP que o *bagging* em quatro analitos e menor tempo em quatro; supera o *bagging* nos dois critérios em Mn, Mo e Ni" |
| "constitui **contribuição metodológica válida**" | "descreve um procedimento reprodutível de migração incremental, verificado por testes de caixa-preta" |
| "esse cenário **amplifica a sensibilidade** dos resultados" | "com 723 variáveis para 17 amostras (razão ≈ 42:1), o resultado é sensível à composição das amostras de calibração" |

---

## 3. Demais seções

### `1secao.tex`
| Antes | Depois |
|---|---|
| "extração de informações **valiosas** de dados complexos" | "estimação de concentrações a partir de dados instrumentais multivariados" |
| "técnicas estatísticas **avançadas** para obter resultados **confiáveis**" | "técnicas de calibração multivariada para obter estimativas com erro de predição quantificável (RMSEP, MAE, R$^2$)" |
| "Este estudo é **significativo** tanto pelo potencial de impacto prático… quanto pela contribuição metodológica" | "Este estudo contribui em dois eixos: (i) a aplicação de *bagging* e *subagging* à calibração de aço-ligas; (ii) a migração de um sistema legado verificada por testes automatizados." |
| "arquitetura de software **confiável** e testável" | "arquitetura de software modular e verificável por testes automatizados" |

### `2secao.tex`
| Antes | Depois |
|---|---|
| "constitui **significativa vantagem** sobre outras técnicas" | "dispensa a suposição prévia de uma distribuição paramétrica dos dados" |
| "estruturas **complexas**… a violação de pressupostos… é **frequente**" | "Em dados espectrais, a colinearidade entre variáveis e a presença de *outliers* violam com frequência esses pressupostos `[TODO \cite]`." |
| "Observa-se **frequentemente** que cv não será menor que 0,10; […] com m = 100 obtêm-se resultados **bem satisfatórios**" | "Para $cv(\widehat{se}_\infty)\geq 0{,}10$, com $m=100$ o $cv(\widehat{se}_m)$ excede o ideal em no máximo \num{0,02} (Tabela~\ref{tab:coefvaria})." |
| "**Muito raramente** serão necessárias mais que m = 200… Valores **muito maiores**…" | "Segundo Efron e Tibshirani~\cite{EFRON:1993}, raramente são necessárias mais de 200 replicações para o erro padrão; para intervalos de confiança, `[TODO: valor citado pelos autores, com página]`." |

### `3secao.tex`
| Antes | Depois |
|---|---|
| "espectros… são **bastante complexos** e constituem centenas ou até milhares de frequências" | "espectros… contêm centenas a milhares de frequências (723 variáveis por amostra neste trabalho)" |

### `5secao.tex` (vagueza e divergências com o código)
| Antes | Depois / observação |
|---|---|
| X04: "Reduz necessidade de conhecimento técnico **avançado**" | "Dispensa o usuário de informar *m* e *k* manualmente" |
| Inventário: "Exportação: *Não identificada*… não apresenta botões de download" | "Exportação \| Métricas (`.csv`) e log (`.txt`) \| `st.download_button` na aba Resultados" |
| D02: "Exportação de resultados (CSV, PDF, PNG)" | "Exportação em PDF e PNG (CSV e TXT já implementados)" |

Outras divergências entre a 5secao e o código de `app.py`/`components.py`, que afetam a verificabilidade:
- Entradas: só `.txt`, e X03 lista `.csv`/`.xlsx` como "extra". O `app.py` já aceita `.txt`, `.csv` e `.xlsx` (RF01, na 6secao).
- Parâmetro *k*: "Inteiro ≥ 1", mas `parse_float_list()` aceita decimais em (0, 1].
- Abas: o texto cita quatro ("Arquivos", "Configuração", "Resultados", "Gráficos"). O `app.py` tem três.
- Gráficos de "resíduos" e "barras comparativas": `components.py` só tem `build_chart` e `build_scatter_chart`.
- RF11/RNF08 (idioma PT/EN "conforme seleção do usuário"): o `app.py` enviado não tem seletor de idioma nem chama `get_header_html(lang)`. Verifique se há um `app.py` mais novo que o v7.

### `6secao.tex`
| Antes | Depois |
|---|---|
| "reduz o **atrito** de distribuição em laboratórios e viabiliza uso colaborativo **simultâneo**" | "dispensa a instalação local de JVM e viabiliza o acesso simultâneo de múltiplos usuários por navegador (capacidade estimada de 10–20 usuários no plano gratuito, Quadro~\ref{tab:escalabilidade})" |
| "funcionalidade **inexistente no sistema Vaadin original**" | "…inexistente no sistema *Desktop* original". Um sistema Vaadin Flow já é web e multiusuário, então confirme a afirmação antes de mantê-la. |
| "Essa correspondência unívoca **confirma**, em nível de especificação, a separação de camadas" | "…**ilustra**, em nível de especificação, a separação de camadas" |
| "detalhada no **capítulo** de Testes e Validação deste TCC II" | "detalhada na Seção~\ref{sec:testescaixapreta}" (referência inexistente e termo fora da NBR 14724) |
| RNF05: "fluxo sequencial e **irreversível**… impedindo execuções" | "fluxo sequencial sugerido pelas abas; o único bloqueio implementado é o botão desabilitado até que os quatro arquivos sejam carregados" (`st.tabs` permite navegar livremente entre abas) |

### `7secao.tex`
| Antes | Depois |
|---|---|
| "executando em **tempo próximo** a linguagens compiladas" | "delegando o cálculo a rotinas compiladas de álgebra linear (LAPACK, via NumPy)" |
| Título e corpo: "**Extensão Natural** para SciPy… **baixo risco**" | "Extensão Possível com SciPy… as rotinas operam sobre `np.ndarray` e podem ser incorporadas a `models.py` sem alterar `components.py` nem `app.py`; a incorporação não foi implementada neste trabalho" |
| "reduzindo a latência percebida pelo usuário **a milissegundos**" | "sem reexecutar `run_full_analysis()` ao navegar entre abas `[TODO: medir e informar o tempo]`" |
| "reduzindo a latência em **70–90%**" (`@st.cache_data`, não implementado) | "evitando recomputação em execuções com os mesmos arquivos; o ganho não foi medido neste trabalho" |
| "informações **impossíveis** de obter com `st.write()`" | "informações **inviáveis** de obter com `st.write()` sem alterar a interface" |
| "mitiga a **percepção de travamento**" | "informa o progresso durante as execuções do *grid search*" |

### `8secao.tex`
| Antes | Depois |
|---|---|
| "priorizando a **clareza e a produtividade** do cientista em detrimento de elementos decorativos" | "organizando o fluxo em três etapas sequenciais (Configuração, Resultados e Gráficos)" |
| "reduz a **sobrecarga cognitiva** ao esconder informações irrelevantes" | "exibe, em cada aba, apenas o conteúdo da etapa correspondente; o efeito sobre a carga cognitiva não foi avaliado empiricamente" |
| "replica *dashboards* técnicos e industriais **sem poluir** o `app.py`" | "concentra os estilos em `components.APP_CSS`, mantendo `app.py` sem definições de estilo" |
| "padrão **recomendado pelas diretrizes de usabilidade**" | "atende à heurística de visibilidade do estado do sistema `\cite{[TODO: Nielsen]}`" |
| "garantem legibilidade… alinhando-se às **normas** de visualização" | "usam grade e fontes pretas explícitas `[TODO: citar a norma ou diretriz do periódico-alvo]`" |
| "fluxo linear e **irreversível**" / "impõe explicitamente a sequência" | mesmo ajuste do RNF05 (ver 6secao) |

### `9secao.tex`
| Antes | Depois |
|---|---|
| Sprint 4: "…pode ser aplicado diretamente, **reduzindo a latência** em execuções repetidas" | "…pode ser aplicado diretamente, podendo reduzir a latência em execuções repetidas; o ganho não foi medido" |

---

## Ordem sugerida de aplicação

1. Corrigir o bloco `\include` (item 0).
2. Corrigir as divergências com o código (5secao, 6secao, 8secao, item 1.10 da 4secao).
3. Reformular a 4secao e a 10secao (itens 1 e 2), começando pelos números recalculados (1.6 e 1.9).
4. Aplicar as demais tabelas da seção 3.
5. Preencher os `[TODO]`.
