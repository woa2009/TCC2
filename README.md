# TCC II IFG 2026 — Guia do Projeto no Claude

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

### Instruções para o Claude

1. **Antes de qualquer revisão, edição ou consulta ao texto do TCC, clonar `woa2009/TCC2`** (`git clone --depth 1`) e ler os arquivos a partir da cópia clonada. Não usar cópias antigas anexadas ao projeto.
2. Para o código Python, clonar `woa2009/streamlit-app`; para o legado Java, `woa2009/MigracaoJava`.
3. O Claude **não envia alterações ao GitHub** (sem autenticação). Toda alteração é entregue como arquivo ou trecho para o Wagner aplicar localmente e fazer `git commit` e `git push`.
4. Se o repositório estiver privado ou inacessível (erro 404), avisar o Wagner e pedir o `.zip` do projeto.
5. Mudanças feitas só no computador do Wagner, sem `push`, não são visíveis ao Claude.

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
| — | `pos/apendice_d`, `pos/apendice_c` | Diagramas UML; paridade Java × Python e resultado dos testes |
| — | `pos/references` | Referências (`abntex2-num`) |

> A numeração dos arquivos não coincide com a ordem das seções (por exemplo, `5secao.tex` é Requisitos Funcionais e `10secao.tex` é a Conclusão). Consultar sempre o arquivo raiz.

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
