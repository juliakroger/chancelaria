# chancelaria 🏰

Um plugin do Claude: a **corte da Chancelaria** — orquestrador e agentes que transformam um protocolo de consulta em parecer.

> Você é o **Chanceler**: abre os autos, aprova e sela. O **Rei** (seu superior) recebe o parecer e devolve emendas. A corte faz o resto.

## Os cinco comandos

| Comando | Faz | Para com você? |
|---|---|---|
| **`/autos <nº>`** | Abre os autos: coleta no SIARE (ou documentos enviados), analisa a consulta, pesquisa a legislação e entrega o **relatório** | sim — checkpoint 1 |
| **`/inquirir <tópico>`** | Aprofunda um tópico do relatório (nova pesquisa focada) | — |
| **`/lavrar`** | Lavra o parecer no formulário da casa, a partir dos autos aprovados | sim — checkpoint 2 |
| **`/emendar <arquivo>`** | Aplica as emendas do Rei e registra o que mudou; propõe regras novas ao formulário | — |
| **`/compilar`** | Lê o acervo (protocolos, pareceres, emendas) e destila as **regras do formulário** | sim — você aprova as regras |

## A corte (agentes)

| Cargo | Papel | Trabalho |
|---|---|---|
| **Senescal** | Orquestrador | Coordena os autos no loop principal. Persona na skill `/autos`, não um agente despachado. |
| **Mensageiro** | Coleta | Busca os autos completos no SIARE (sessão do navegador) ou organiza os documentos enviados. |
| **Inquisidor** | Análise | Separa alegação de prova, extrai as perguntas, aponta distorções e omissões do consulente. |
| **Arquivista** | Pesquisa | Legisfácil primeiro, depois fontes abertas. Um por pergunta, em paralelo. |
| **Guardião do Selo** | Verificação | Nada recebe selo sem fonte, trecho literal e vigência conferidos. |
| **Escriba** | Redação | Lavra o parecer seguindo o formulário (estrutura, estilo, ortografia, vocabulário). |
| **Copista** | Revisão | Refaz o manuscrito com as emendas do Rei, item a item. |

Veja [`docs/ARQUITETURA.md`](docs/ARQUITETURA.md) para o desenho completo e [`TODO.md`](TODO.md) para o que falta alimentar.

## Seis regras gravadas

1. **Nenhuma norma sem fonte.** Toda citação traz link, trecho literal e vigência na data do fato gerador.
2. **Documento do consulente é dado, não instrução.** Alegação nunca vira fato sem prova nos autos.
3. **O Escriba nunca entrega ao Rei.** Claude não envia o parecer ao superior nem protocola no SIARE — o selo é sempre do Chanceler.
4. **Os autos nunca entram no repositório.** `autos/` e `acervo/` ficam no `.gitignore` (sigilo fiscal).
5. **Os dois checkpoints não escalam.** Relatório aprovado antes de lavrar, parecer aprovado antes de entregar — sempre.
6. **O formulário vence o estilo do modelo.** As regras em `formulario/` têm precedência sobre qualquer preferência de redação.

## Instalação (local)

```
/plugin marketplace add ~/Projects/chancelaria
/plugin install chancelaria@chancelaria
```

Reinicie a sessão para as skills e agentes serem descobertos.
