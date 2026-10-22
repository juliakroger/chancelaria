# Esquema dos autos (dossiê por protocolo)

Todo agente lê e escreve **apenas** dentro da pasta dos autos do protocolo em curso.
A pasta raiz é configurada pelo Chanceler (ex.: `~/Protocolos/autos/`). Nunca dentro do repositório do plugin.

```
autos/<nº-protocolo>/
  00_metadados.json      ← Senescal / Mensageiro
  01_documentos/         ← Mensageiro (originais, nunca editados)
  02_analise.md          ← Inquisidor
  03_pesquisa/
    P1.md, P2.md, ...    ← Arquivista (uma nota por pergunta)
    pendencias.md        ← Arquivista (o que exigiu sessão que caiu, etc.)
  03b_verificacao.md     ← Guardião do Selo
  04_relatorio.md        ← Senescal (checkpoint 1)
  05_parecer_vN.docx     ← Escriba (uma versão por rodada)
  06_emendas.md          ← Copista (log de cada rodada de emendas)
  diario.md              ← Senescal (linha do tempo: o que rodou, quando, decisões do Chanceler)
```

## 00_metadados.json

```json
{
  "protocolo": "",
  "origem": "siare | documentos_enviados",
  "consulente_tipo": "contribuinte | orgao_estadual | outro",
  "assunto": "",
  "tributo": "",
  "data_fato_gerador": "",
  "data_abertura": "",
  "status": "aberto | relatorio | aprovado | lavrado | em_emendas | selado",
  "versao_parecer": 0
}
```

## Convenções

- Datas em `AAAA-MM-DD` nos arquivos de máquina; por extenso só no parecer.
- Perguntas numeradas `P1`, `P2`… do jeito que o Inquisidor as fixou; todos os arquivos seguintes usam a mesma numeração.
- Fatos: `F1`, `F2`… com marcação **[comprovado: doc X, fl. Y]** ou **[alegado]**.
- Fontes: `N1`, `N2`… (normas) e `J1`… (consultas/jurisprudência), referenciadas pelo ID em todo o resto.
