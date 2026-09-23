# TCC_II_IFG_2025 — Mapeamento do Projeto

> **Título:** Modelagem de calibração multivariada: regressão linear múltipla com métodos de conjunto e avaliação pelo erro padrão de predição da raiz quadrada média
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
├── tex/                         ← Capítulos e conteúdo textual
│   ├── 1secao.tex               ← Capítulo 1: Introdução
│   ├── 2secao.tex               ← Capítulo 2: Revisão da Literatura (RLM, Bootstrap)
│   ├── 3secao.tex               ← Capítulo 3: Materiais e Métodos (Amostras de Aço-Ligas)
│   ├── 4secao.tex               ← Capítulo 4: Resultados e Discussões
6secao.tex -Seção 5 - Requisitos Funcionais

7secao.tex-Seção 6 - Engenharia de Software e Modernização

8secao.tex -Seção 7 - Ecossistema de Desenvolvimento (Python e Streamlit)

9secao.tex -Seção 8 - Interface e Experiência do Usuário (UI/UX) Científica

10secao.tex -Seção 9 - Desenvolvimento Iterativo por Sprints e Validação por Testes Automatizados
│   ├── 5secao.tex               ← Capítulo 5: Conclusão
│   ├── algoritmos.tex           ← Algoritmos utilizados no trabalho
│   ├── graficos.tex             ← Código TikZ/pgfplots para os gráficos
│   ├── apoio_4secao.tex         ← Material de apoio para o Capítulo 4
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
│   └── CAP4_TCC_II_IFG_2025.pdf
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
├── \include{tex/4secao}                ← Cap. 4: Resultados e Discussões
├── \include{tex/5secao}                ← Cap. 5: Conclusão
│
└── \bibliography{pos/references}       ← Referências bibliográficas
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

> **Nota:** Os arquivos `.csv` (`r_bagging.csv`, `r_bagging2.csv`, `rmsep5080.csv`, `rmsepsuperior.csv`) devem estar presentes no diretório raiz, pois são lidos diretamente pelo pacote `readarray` durante a compilação.
