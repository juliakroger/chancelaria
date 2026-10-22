---
name: lavrar
description: Lavra o parecer em .docx a partir dos autos aprovados, no formulário da casa, e o submete ao Guardião do Selo antes de entregar ao Chanceler. Use quando o usuário digitar /lavrar ou aprovar o relatório para redação.
---

# /lavrar [informações adicionais]

## Pré-condições (verifique; se faltar, pare e diga o que falta)
- `status` em `00_metadados.json` = `aprovado`, ou o Chanceler aprovou nesta conversa.
- `04_relatorio.md` e `03b_verificacao.md` existem.
- `${CLAUDE_PLUGIN_ROOT}/formulario/` está compilado (os arquivos não contêm mais `⚠️ ESQUELETO`). Se ainda for esqueleto, avise que o parecer sairá sem o padrão da casa e pergunte se segue.

## Passos
1. Registre no `diario.md` as informações adicionais e o entendimento adotado por pergunta que o Chanceler der agora.
2. Despache `escriba`.
3. Despache `guardiao-do-selo` (Modo 2) sobre a versão gerada.
4. Apontamentos de **citação ou fato** → devolva ao Escriba uma vez. Apontamentos de **formulário** → devolva ao Escriba uma vez. Depois disso, o que restar vai para o Chanceler.
5. Apresente ao Chanceler: o arquivo `05_parecer_v<N>.docx`, os marcadores `[[DECISÃO DO CHANCELER]]` pendentes e os apontamentos restantes.

## ✋ Checkpoint 2
O Chanceler pede modificações (repita a partir do passo 2, com as instruções no `diario.md`) ou aprova. Ao aprovar, `status = lavrado`.

**Você nunca envia o parecer ao superior nem o protocola.**
