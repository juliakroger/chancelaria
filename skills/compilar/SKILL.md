---
name: compilar
description: Compila o formulário da casa — lê o acervo de protocolos, pareceres prontos e emendas do superior e destila regras curtas e verificáveis de estrutura, estilo, ortografia, vocabulário e citação em formulario/, para que as demais skills não precisem reler os exemplos. Use quando o usuário digitar /compilar, adicionar documentos ao acervo ou aprovar candidatas a regra.
---

# /compilar [completo | incremental | candidatas]

Objetivo: transformar dezenas de documentos em **poucas regras densas**. As outras skills leem só `formulario/`; o acervo nunca é lido em produção.

## Entradas
```
acervo/
  protocolos/   consultas originais (como chegaram)
  pareceres/    pareceres finais aprovados (de preferência a versão selada)
  emendas/      versões com comentários/alterações controladas do superior
```
Mais `formulario/_candidatas.md` (vindas do `/emendar`).

Modo padrão: **incremental** — processa só o que não está em `formulario/_indice.json` (nome + hash de cada documento já compilado).

## 1. Leitura em leque (subagentes)
Despache um subagente por lote de 3–5 documentos (mesmo tipo). Cada um devolve **observações**, não regras:

```
DOC: <nome>
TIPO: parecer | protocolo | emenda
ESTRUTURA: seções na ordem em que aparecem, com títulos literais
FÓRMULAS: aberturas, transições, fechos literais (≤ 15 palavras cada)
GRAFIA: maiúsculas, abreviações, numerais, datas, siglas — como aparecem
CITAÇÃO: como lei/artigo/consulta/acórdão são citados (literal)
VOCABULÁRIO: termos técnicos e escolhas recorrentes
EMENDAS (só tipo emenda): trecho original → correção do superior → motivo aparente
CONSULTA (só protocolo): tipo, estrutura, armadilhas do consulente
```

## 2. Consolidação (você, no loop principal)
- Agrupe observações iguais. Uma regra nasce quando o padrão aparece em **≥ 3 pareceres** ou é **emenda do superior em ≥ 2 documentos** (emenda pesa mais que uso).
- Conflito entre documentos → regra com a variante majoritária + nota `Variante: ...`; se empatar, leve ao Chanceler.
- Escreva cada regra assim:

```
### ORT-07 — Artigos de lei por extenso no corpo do texto
- Regra: escreva "artigo 12" no corpo; "art. 12" só dentro de parênteses e citações.
- Certo: conforme o artigo 12 da Lei nº ...
- Errado: conforme o art. 12 da Lei nº ...
- Força: emenda do superior (4 docs) · uso (11/14 pareceres)
```
Prefixos: `EST` estrutura · `EIL` estilo · `ORT` ortografia · `VOC` vocabulário · `CIT` citações · `CON` consulta.

- **Exemplos:** para cada seção da estrutura, escolha 2–3 trechos curtos (≤ 120 palavras) e **anonimize** (nome, CNPJ/CPF, IE, nº de protocolo, endereço, valores → `[CONSULENTE]`, `[CNPJ]`, `[PROTOCOLO]`, `[VALOR]`). Salve em `formulario/exemplos/<seção>.md`.

## 3. Aprovação ✋
Apresente ao Chanceler **só o diff**: regras novas, alteradas, removidas, com a força de cada uma. Grave em `formulario/*.md` apenas o aprovado. Atualize `_indice.json` e limpe de `_candidatas.md` o que foi resolvido.

## Metas de tamanho
Cada arquivo do formulário ≤ ~2 páginas. Se crescer, funda regras redundantes — densidade é o objetivo.

## Sigilo
- Rode `/compilar` só no computador onde está o acervo.
- Nada identificável sai do acervo: regras e exemplos são anonimizados antes de gravar.
