# Arquitetura da Chancelaria

## Visão geral

```
            /autos <nº>
                 │
            ┌────▼─────┐
            │ Senescal │  (loop principal — persona da skill /autos)
            └────┬─────┘
                 │
   ┌─────────────┼──────────────────────────────┐
   ▼             ▼                              ▼
Mensageiro → Inquisidor → Arquivista ×N (uma por pergunta, em paralelo)
 (coleta)     (análise)        │
                               ▼
                        Guardião do Selo
                               │
                               ▼
                     04_relatorio.md  ──►  ✋ CHECKPOINT 1 (Chanceler)
                                              │  /inquirir <tópico> (volta ao Arquivista)
                                              │  aprovado
                                              ▼
                                   /lavrar → Escriba → Guardião do Selo
                                              │
                                              ▼
                                   05_parecer_v1.docx ──► ✋ CHECKPOINT 2
                                              │
                                   Chanceler entrega ao Rei (fora do Claude)
                                              │
                                   /emendar → Copista → v2, v3…
                                              │
                                   regras recorrentes ──► formulario/ (com aprovação)
```

## Três camadas

| Camada | Onde vive | Versionada? |
|---|---|---|
| **Cérebro** — agentes, skills, `formulario/`, `conhecimento/` | este repositório (privado) | sim, git |
| **Autos** — um dossiê por protocolo | pasta local do computador do trabalho | **não** (sigilo) |
| **Acervo** — exemplos reais para `/compilar` | `acervo/` local, ignorado pelo git | **não** |

O computador pessoal edita o cérebro e testa com casos anonimizados. O do trabalho roda protocolos reais.

## O formulário (regras pré-compiladas)

Problema: cada skill reler dezenas de pareceres a cada execução é caro e inconsistente.
Solução: `/compilar` lê o acervo **uma vez** e destila regras curtas e verificáveis em `formulario/`.
As skills leem só o formulário — nunca o acervo.

```
formulario/
  estrutura.md     ordem e conteúdo de cada seção do parecer
  estilo.md        tom, pessoa verbal, tempos, fórmulas de abertura/fecho
  ortografia.md    grafias da casa, maiúsculas, abreviações, numerais, datas
  vocabulario.md   termos preferidos × proibidos, expressões consagradas
  citacoes.md      como citar lei, artigo, inciso, consulta, jurisprudência
  consulta.md      padrões de consultas (tipos, armadilhas recorrentes do consulente)
  exemplos/        3–5 trechos curtos e anonimizados por seção (não pareceres inteiros)
  modelo/          template.docx com estilos de parágrafo da casa
```

Cada regra tem um ID (`EST-03`, `ORT-12`…), uma frase imperativa, um exemplo certo/errado e a origem (quantos documentos do acervo a sustentam). O Copista e o Guardião citam os IDs ao apontar desvios.

## Modelos sugeridos por agente

| Agente | Modelo | Motivo |
|---|---|---|
| Mensageiro | sonnet | navegação mecânica |
| Inquisidor | opus | julgamento sobre fatos e intenção |
| Arquivista | sonnet | volume de busca, roda em paralelo |
| Guardião do Selo | opus | precisão crítica |
| Escriba | opus | qualidade de redação |
| Copista | sonnet | aplicação dirigida |

## Sessão de 50 minutos

Só o Mensageiro (e o Arquivista no Legisfácil) dependem de login. Coleta em lote logo após o login; o restante roda sem sessão. O que falhar por sessão vencida vai para `03_pesquisa/pendencias.md` e é retomado no próximo login.
