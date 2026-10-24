# TCC II IFG 2026 — Guia do Projeto

* **Título:** Migração de sistemas legados de análise química: de Java desktop para Python web
* **Autor:** Wagner Oliveira de Araujo
* **Instituição:** Instituto Federal de Goiás (IFG) — Campus Anápolis
* **Curso:** Bacharelado em Ciência da Computação
* **Trabalho:** TCC II, 2026
* **Orientador:** Prof. Alexandre Bellezi Jose, Me.
* **Coorientador:** Prof. Eder Silva de Brito, Dr.
* **Defesa prevista:** 20 de novembro de 2026, Anápolis

---

## Fonte da verdade: GitHub

Os arquivos do TCC **não são mantidos neste projeto**. A versão oficial e atualizada está no GitHub.

| Repositório | Conteúdo | Link |
|-------------|----------|------|
| `TCC2` | Documento LaTeX completo (texto, `.bib`, estilos, figuras, dados) | https://github.com/woa2009/TCC2 |
| `streamlit-app` | Sistema Python/Streamlit (`app.py`, `models.py`, `components.py`) | https://github.com/woa2009/streamlit-app |
| `MigracaoJava` | Sistema Java Desktop legado (`BaggingOptimized.java`) | https://github.com/woa2009/MigracaoJava |


---

## Estrutura do repositório `TCC2`

```
TCC2/
├── TCC_II_IFG_2026.tex      ← arquivo raiz (classe abntex2, bibliografia numérica)
├── setup/                   ← ufscthesisA4-alf.sty, stylodefinicao.tex, algorithm2e.sty
├── pre/                     ← pre.tex, ata.tex, termo.tex, folhaAprovacao.tex, fichaCatalografica.tex
├── tex/                     ← 1secao.tex ... 10secao.tex e dados das figuras (.txt)
├── pos/                     ← references.bib, apendice_c.tex, apendice_d.tex, saídas dos testes
├── outros/                  ← fig/ (figuras) e prog/ (dados espectrais)
├── quadro_*.tex, apoio.tex  ← quadros auxiliares (parte comentada no arquivo raiz)
└── *.csv                    ← r_bagging, r_bagging2, rmsep5080, rmsepsuperior (lidos pelo LaTeX)
```

## Ordem de inclusão no arquivo raiz

| Ordem | Arquivo | Seção |
|:-----:|---------|-------|
| — | `pre/pre` (`\input`) | Capa, resumos, listas, sumário |
| 1 | `tex/1secao` | Introdução |
| 2 | `tex/2secao` | Revisão da literatura |
| 3 | `tex/3secao` | Materiais e métodos |
| 4 | `tex/4secao` | Análise experimental dos algoritmos quimiométricos |
| 5 | `tex/5secao` | Requisitos funcionais |
| 6 | `tex/6secao` | Engenharia de software e modernização |
| 7 | `tex/7secao` | Resultados e discussões |
| 8 | `tex/8secao` | Interface e experiência do usuário (UI/UX) científica |
| 9 | `tex/9secao` | Desenvolvimento iterativo por sprints e validação por testes |
| 10 | `tex/10secao` | Conclusão, limitações e trabalhos futuros |
| — | `pos/apendice_a`, `pos/apendice_b` | Diagramas UML; paridade Java × Python e resultado dos testes |
| — | `pos/references` | Referências (`abntex2-num`) |

## Como compilar

```bash
pdflatex TCC_II_IFG_2026.tex
bibtex TCC_II_IFG_2026
pdflatex TCC_II_IFG_2026.tex
pdflatex TCC_II_IFG_2026.tex
```

Os arquivos `.csv` da raiz devem estar presentes, pois são lidos diretamente pelo LaTeX. O `README.md` do repositório `TCC2` traz o detalhamento completo.

---

## Referência neste projeto

* `Regras_trabalhos_academicos.md`: normas ABNT e regras de formatação do TCC (não está no GitHub).
