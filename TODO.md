# TODO — alimentar a Chancelaria

Ordem sugerida: **A → B → C → D**. Sem A e B, o `/compilar` não tem o que destilar e o `/lavrar` escreve sem o padrão da casa.

## A. Acervo para o `/compilar` (vai em `acervo/`, fora do git)

Quanto mais variado em **tipo de consulta e tributo**, melhores as regras. Casar os três por `<id>` quando possível.

- [ ] **10–20 pareceres finais aprovados** → `acervo/pareceres/`
  - mínimo útil: 8; ideal: 15+
  - variar: assuntos diferentes, respostas favoráveis e desfavoráveis, curtos e longos
  - se houver mais de um "padrão" (ex.: modelo antigo × atual), mande **só o atual** ou avise qual vale
- [ ] **Os protocolos de origem desses pareceres** → `acervo/protocolos/`
  - ensina o Inquisidor a ler consultas reais (armadilhas, premissas embutidas)
  - inclua 2–3 consultas "difíceis" (consulente distorcendo fatos, perguntas que embutem a resposta)
- [ ] **5–10 versões com emendas do superior** → `acervo/emendas/`
  - o .docx com comentários / alterações controladas, **antes** de você aceitar
  - é a fonte mais valiosa: emenda pesa mais que uso na compilação
- [ ] **(opcional) 3–5 relatórios/notas internas** que você já faz hoje antes do parecer
  - serve para calibrar o formato do relatório do checkpoint 1

## B. Formulário oficial (vai em `formulario/`)

- [ ] **`modelo/template.docx`** — parecer em branco com os estilos da casa (ver `formulario/modelo/README.md`)
- [ ] **Manual, norma ou instrução de redação** do órgão, se existir (padrão de documentos oficiais, manual de redação) → mande junto do acervo; vira regra com força máxima
- [ ] **Lista de "nunca escreva assim"** que você já conhece de cor — 5 minutos de ditado poupam várias rodadas de emenda

## C. Conhecimento (vai em `conhecimento/`)

- [ ] **`fontes.md`** — preencher URLs reais, ordem de busca, quais exigem login, hierarquia de autoridade e fontes proibidas como fundamento
- [ ] **Legisfácil** — como buscar: tela de pesquisa, filtros, operadores de palavra-chave, como aparece o resultado (prints ajudam)
- [ ] **SIARE** — caminho de telas até um protocolo e onde ficam os anexos/tramitação (prints ajudam) → preenche o TODO do `agents/mensageiro.md`
- [ ] **Pasta raiz dos autos** no computador do trabalho → preenche o TODO do `skills/autos/SKILL.md`

## D. Decisões de desenho (me responda quando refinarmos)

- [ ] O parecer sempre sai em **.docx**? Há numeração/ementa/assinatura padrão?
- [ ] O relatório do checkpoint 1: formato de conversa, Markdown nos autos, ou documento?
- [ ] Quem é o "consulente" mais comum (contribuinte × órgão) e há tratamentos diferentes?
- [ ] Há prazos ou tipos de consulta que devam ter prioridade/alerta?
- [ ] Repositório: novo repo **privado** `chancelaria`? (recomendado)

## Depois de A e B

1. Rodar `/compilar completo` no computador do trabalho → revisar o diff das regras com calma (é o passo que mais vale o seu tempo)
2. Rodar `/autos` com **documentos enviados** (sem SIARE) em 2–3 casos já resolvidos e comparar com o parecer real
3. Ajustar agentes e regras → commit
4. Só então ligar o Mensageiro no SIARE
