# TCC_II_IFG_2025 — Mapeamento do Projeto

> **Título:** Migração de Sistemas Legados de Análise Química: DE JAVA Desktop Para PYTHON WEB
>
> **Autor:** Wagner Oliveira de Araujo

> **Instituição:** Instituto Federal de Educação, Ciência e Tecnologia de Goiás — Campus Anápolis

> **Curso:** Bacharelado em Ciência da Computação

> **Trabalho:** TCC II (2026)

> **Orientador:** Prof. Alexandre Bellezi Jose, Me.

> **Coorientador:** Prof. Eder Silva de Brito, Dr.

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

---

## Estrutura de Diretórios

```
B_Projeto_Integrador_III_Final/
│
├── TCC_II_IFG_2025.tex          ← Arquivo raiz do documento
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
│   ├── 2secao.tex               ← Seção 2: Revisão da Literatura (RLM, Bootstrap)
│   ├── 3secao.tex               ← Seção 3: Materiais e Métodos (Amostras de Aço-Ligas)
│   ├── 4secao.tex               ← Seção 4: Resultados e Discussões
│   ├── 6secao.tex               ← Seção 5: Requisitos Funcionais
│   ├── 7secao.tex               ← Seção 6: Engenharia de Software e Modernização
│   ├── 8secao.tex               ← Seção 7: Ecossistema de Desenvolvimento (Python e Streamlit)
│   ├── 9secao.tex               ← Seção 8: Interface e Experiência do Usuário (UI/UX) Científica
│   ├── 10secao.tex              ← Seção 9: Desenvolvimento Iterativo por Sprints e Validação por Testes
│   ├── 5secao.tex               ← Seção 10: Conclusão
│   ├── algoritmos.tex           ← Algoritmos utilizados no trabalho
│   ├── graficos.tex             ← Código TikZ/pgfplots para os gráficos
│   ├── apoio_4secao.tex         ← Material de apoio para o Seção 4
│   ├── apoio_subagging.tex      ← Material de apoio sobre subagging
│   ├── discussao.tex            ← Texto auxiliar de discussão
│   ├── pesquisa.tex             ← Texto de pesquisa/levantamento bibliográfico
│   ├── dados/                   ← Dados tabulares para as seções
│   │   ├── bagging_fe.txt       ← Resultados de bagging para o elemento Fe
│   │   ├── bagging_mn.txt       ← Resultados de bagging para o elemento Mn
│   │   ├── bootstrap_fe.txt     ← Resultados de bootstrap para Fe
│   │   ├── bootstrap_mn.txt     ← Resultados de bootstrap para Mn
│   │   ├── rlm_fe.txt           ← Resultados de RLM para Fe
│   │   ├── rlm_mn.txt           ← Resultados de RLM para Mn
│   │   ├── subagging_fe.txt     ← Resultados de subagging para Fe
│   │   └── subagging_mn.txt     ← Resultados de subagging para Mn
│   └── [outros .txt/.csv]       ← Dados auxiliares de predições e RMSEP
│
├── pos/                         ← Elementos pós-textuais
│   ├── references.bib           ← Arquivo principal de referências bibliográficas (BibTeX)
│   ├── references1.bib          ← Referências complementares (versão anterior)
│   ├── apendice_a.tex           ← Apêndice A (incluído mas desabilitado no raiz)
│   ├── anexo_a.tex              ← Anexo A (incluído mas desabilitado no raiz)
│   └── [outros .bib]            ← Arquivos de referências individuais por fonte
│
├── outros/                      ← Recursos auxiliares do projeto
│   ├── fig/                     ← Figuras e imagens utilizadas no documento
│   │   ├── bootstrap.png        ← Ilustração do método Bootstrap
│   │   ├── subagging.png        ← Ilustração do método Subagging
│   │   ├── resultado_final.png  ← Figura de resultado principal
│   │   ├── resultado_final.eps  ← Versão EPS do resultado final
│   │   ├── RLM_Bagging.pdf      ← Gráfico comparativo RLM × Bagging
│   │   ├── BootStrapRMSEPFe.pdf ← Gráfico RMSEP Bootstrap para Fe
│   │   ├── IFGAnapolisHor2.png  ← Logomarca IFG (horizontal)
│   │   ├── logoIFG.jpg          ← Logomarca IFG alternativa
│   │   └── [outras figuras]     ← Figuras históricas/legadas (.eps, .pdf, .jpg, .png)
│   └── prog/                    ← Scripts e dados de programas auxiliares
│       ├── dados_Fe.txt         ← Dados do elemento Ferro
│       ├── dados_Mn.txt         ← Dados do elemento Manganês
│       ├── dados_Cr.txt         ← Dados do elemento Cromo
│       ├── dados_Ni.txt         ← Dados do elemento Níquel
│       ├── dados_Mo.txt         ← Dados do elemento Molibdênio
│       ├── bagging.txt          ← Script/saída de bagging
│       ├── subbagging.txt       ← Script/saída de subagging
│       └── insertionsort.c      ← Código C auxiliar (insertion sort)
│
├── pdf_old/                     ← PDFs de versões anteriores do trabalho
│   ├── introducao.pdf
│   └── 
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
    ├── TCC_II_IFG_2025.aux
    ├── TCC_II_IFG_2025.bbl      ← Bibliografia compilada
    ├── TCC_II_IFG_2025.blg
    ├── TCC_II_IFG_2025.toc      ← Sumário
    ├── TCC_II_IFG_2025.lof      ← Lista de figuras
    ├── TCC_II_IFG_2025.lot      ← Lista de tabelas
    ├── TCC_II_IFG_2025.idx
    ├── TCC_II_IFG_2025.ind
    ├── TCC_II_IFG_2025.ilg
    └── TCC_II_IFG_2025.log
```

---

## Detalhamento das Seções Textuais

### `1secao.tex` (Introdução)

Arquivo textual responsável pela introdução do trabalho. Responsável por:

- Apresentar o tema da calibração multivariada e a relevância da regressão linear múltipla
- Contextualizar o uso de métodos de conjunto (*ensemble*) no escopo da pesquisa
- Formular o problema de pesquisa, as hipóteses e as justificativas do estudo
- Definir formalmente os objetivos gerais e específicos do trabalho

---

### `2secao.tex` (Revisão da Literatura)

Arquivo textual dedicado à fundamentação teórica. Responsável por:

- Revisar a literatura sobre quimiometria, calibração analítica e modelagem matemática
- Detalhar os conceitos estatísticos da regressão linear múltipla e métricas de erro como o RMSEP
- Explicar os fundamentos teóricos dos métodos de conjunto (*bagging*, *boosting* ou correlatos)
- Referenciar trabalhos correlatos utilizando as normas de citação da ABNT

---

### `3secao.tex` (Materiais e Métodos)

Arquivo textual focado nos procedimentos práticos da pesquisa. Responsável por:

- Descrever a natureza dos dados e o processo de coleta ou simulação das amostras de aço-ligas
- Apresentar a arquitetura computacional e o fluxo de implementação dos algoritmos
- Detalhar a configuração dos experimentos, divisão dos conjuntos de treino/teste e validação
- Especificar as ferramentas, bibliotecas e ambientes de desenvolvimento utilizados

---

### `4secao.tex` (Resultados e Discussões)

Arquivo textual para apresentação dos achados experimentais. Responsável por:

- Exibir as tabelas comparativas geradas a partir dos arquivos `.csv` mapeados no arquivo raiz
- Analisar o desempenho dos métodos de conjunto frente aos modelos tradicionais através do RMSEP
- Discutir as implicações estatísticas e computacionais dos resultados obtidos
- Validar ou refutar as hipóteses propostas com base nas evidências empíricas

---

### `5secao.tex` (Conclusão)

Arquivo textual de encerramento do trabalho acadêmico. Responsável por:

- Sintetizar as principais conclusões alcançadas com a modelagem realizada
- Retomar e responder diretamente se os objetivos específicos foram atendidos
- Elencar as limitações encontradas ao longo do mapeamento e experimentos do projeto
- Propor direcionamentos e sugestões para trabalhos futuros na área

---

### `6secao.tex` (Requisitos Funcionais)

Arquivo textual voltado à especificação técnica da aplicação de software. Responsável por:

- Levantar e descrever detalhadamente os requisitos funcionais do sistema computacional desenvolvido
- Mapear as interações esperadas entre os usuários (pesquisadores/químicos) e o motor de calibração
- Definir as regras de negócio associadas à carga de dados, execução de modelos e exportação de resultados
- Apresentar diagramas de casos de uso ou documentação técnica que apoiem os requisitos de software

---

### `7secao.tex` (Engenharia de Software e Modernização)

Arquivo textual que aborda a arquitetura de engenharia de software aplicada. Responsável por:

- Justificar os padrões arquiteturais escolhidos para garantir a manutenibilidade do código do projeto
- Discutir os processos de modernização de software aplicados para transicionar scripts legados para aplicações integradas
- Detalhar as boas práticas de desenvolvimento de software adotadas no ciclo de vida do TCC
- Descrever a modularização do código para os métodos estatísticos e computacionais implementados

---

### `8secao.tex` (Ecossistema de Desenvolvimento)

Arquivo textual sobre o ecossistema tecnológico adotado. Responsável por:

- Apresentar a linguagem de programação Python e as bibliotecas científicas utilizadas no ambiente
- Justificar a escolha do ecossistema Streamlit para a criação rápida do MVP da aplicação web
- Detalhar o fluxo de processamento de dados tabulares utilizando as ferramentas nativas do ecossistema
- Descrever o gerenciamento de dependências e ambiente virtual do ambiente de produção/desenvolvimento

---

### `9secao.tex` (Interface e Experiência do Usuário Científica)

Arquivo textual dedicado ao design de interface (*UI*) e experiência (*UX*). Responsável por:

- Conceituar os princípios de UI/UX focados em aplicações e ferramentas de cunho científico
- Apresentar as decisões de design adotadas nas telas de exibição de erros preditivos e gráficos (como RMSEP)
- Descrever os fluxos de usabilidade pensados para simplificar tarefas complexas de calibração multivariada
- Documentar os feedbacks visuais e elementos interativos criados para o monitoramento de execuções estatísticas

---

### `10secao.tex` (Desenvolvimento Iterativo e Validação)

Arquivo textual com foco em metodologias ágeis de entrega e qualidade de software. Responsável por:

- Explicar a divisão do desenvolvimento do projeto em Sprints iterativas e incrementais
- Detalhar a estratégia de validação do código por meio de testes automatizados (unitários ou de integração)
- Apresentar as métricas de qualidade obtidas que atestam a robustez do software de calibração construído
- Relacionar o processo de feedback e refinamento contínuo dos modelos estatísticos durante o cronograma do TCC

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
├── \include{tex/1secao}                ← Seção. 1: Introdução
├── \include{tex/2secao}                ← Seção. 2: Revisão da Literatura
├── \include{tex/3secao}                ← Seção. 3: Materiais e Métodos
├── \include{tex/4secao}                ← Seção. 4: Resultados e Discussões
├── \include{tex/6secao}                ← Seção 5: Requisitos Funcionais
├── \include{tex/7secao}                ← Seção 6: Engenharia de Software e Modernização
├── \include{tex/8secao}                ← Seção 7: Ecossistema de Desenvolvimento (Python/Streamlit)
├── \include{tex/9secao}                ← Seção 8: Interface e Experiência do Usuário (UI/UX)
├── \include{tex/10secao}               ← Seção 9: Desenvolvimento Iterativo e Validação
├── \include{tex/5secao}                ← Seção. 10: Conclusão
│
└── ibliography{pos/references}       ← Referências bibliográficas
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
