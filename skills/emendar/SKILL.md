---
name: emendar
description: Aplica ao parecer as emendas devolvidas pelo superior (docx com comentários/alterações controladas ou anotações coladas), gera nova versão e registra cada mudança. Use quando o usuário digitar /emendar ou trouxer o parecer revisado pelo superior.
---

# /emendar <arquivo do superior | anotações coladas>

1. Identifique o protocolo (pelo nome do arquivo, pelo texto do parecer ou perguntando).
2. Salve o arquivo do superior em `autos/<nº>/01_documentos/` como `NN_emendas_rodada<k>.<ext>` (original intacto).
3. Despache `copista`.
4. Emendas `PRECISA_CHANCELER`:
   - se pedem pesquisa → ofereça `/inquirir`;
   - se pedem decisão → apresente as opções.
5. Despache `guardiao-do-selo` (Modo 2) sobre a nova versão.
6. Apresente ao Chanceler: nova versão, tabela da rodada (de `06_emendas.md`) e as **candidatas a regra**.
7. Candidatas aprovadas pelo Chanceler → anote em `${CLAUDE_PLUGIN_ROOT}/formulario/_candidatas.md` para o próximo `/compilar`. Não edite o formulário direto daqui.

Atualize `status = em_emendas` e `versao_parecer`. Ao aprovar a versão final, `status = selado`.
