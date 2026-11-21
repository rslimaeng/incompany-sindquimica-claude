# Do chat ao procedimento · prática 4a

Uma conversa inteira, do jeito que ela acontece de verdade: você anexa a planilha, o Claude analisa, você pede o relatório, corrige e aprova. Depois de aprovado, a conversa já fez o trabalho dela. Se o relatório volta todo mês, ela vira **um projeto** ou **uma skill**.

**A planilha:** `producao-lotes-2025-2026.xlsx`, da página. A Química Serra Azul é fictícia: 4 linhas de envase, 6 produtos, planejado × produzido × aprovado de janeiro de 2025 a setembro de 2026, 506 linhas.

**Como fazer:** uma conversa nova no chat, fora de qualquer projeto. Os cinco prompts vão na **mesma** conversa, um de cada vez. A planilha só vai no primeiro.

## Prompt 1 · O raio-X da base (anexe a planilha)

```
[P] Você é um analista de planejamento e controle de produção (PCP) sênior de uma indústria de saneantes, especialista em planejado × realizado.

[C] A Química Serra Azul tem 4 linhas de envase e 6 produtos. A planilha anexa tem, por linha, produto e mês, os lotes planejados, produzidos e reprovados no controle de qualidade, e os volumes em litros, de janeiro de 2025 a setembro de 2026. Antes de qualquer relatório, quero entender a base.

[T] Faça uma análise exploratória: o que cada coluna significa e o tipo de cada uma, o período e os totais. Aponte valores vazios, linhas repetidas, grafias diferentes para a mesma coisa e contas que não fecham (lotes produzidos × volume por lote = volume produzido). Sugira 3 perguntas de negócio que esta base responde.

[F] Quatro blocos: (a) Estrutura da base; (b) Qualidade dos dados, com cada problema e onde ele está; (c) Primeira fotografia: volume planejado × aprovado por ano; (d) 3 perguntas para investigar.

[L] Sem gráficos e sem relatório ainda. Não corrija nada sozinho: liste os problemas e me pergunte como tratar.

[Critério de sucesso] Um gerente industrial entende o que tem em mãos, e quanto pode confiar, sem abrir a planilha.
[Negativo] Sem jargão de programação e sem nome de ferramenta ou biblioteca.
```

**O que esperar:** a estrutura das 16 colunas e, na qualidade, os problemas plantados de propósito: motivo vazio em desvio grande, 2 linhas repetidas, "Marco" sem cedilha, "linha 3 " com minúscula e espaço, e 2 volumes produzidos com um zero a mais. No fim, ele pergunta como tratar.

## Prompt 2 · Onde está o desvio

```
Sobre os problemas: as linhas repetidas saem; grafias diferentes viram uma só (Linha 3, Março); onde lotes produzidos × volume por lote não fecha com o volume produzido, vale lotes × volume. Os motivos vazios ficam como "sem motivo registrado". Refaça os totais com isso.

Agora compare o volume planejado × aprovado de 2026 por linha e por produto. Encontre os 3 maiores desvios negativos e o maior positivo. Para cada um: quanto (em litros e em %), desde quando, e o motivo que a planilha registra.

Uma tabela por linha, uma por produto, e uma seção curta por desvio. Causa, só a que a planilha mostra; o que for hipótese, marque como hipótese.
```

**O que esperar:** a Linha 3 muito abaixo das outras em 2026 (cerca de 40 % abaixo do planejado), e o amaciante como o único produto acima do plano. Os números do raio-X mudam um pouco, porque agora os problemas foram tratados.

## Prompt 3 · O relatório

```
Agora o relatório para a diretoria industrial, em uma página. Comece pela conclusão em 3 linhas. Depois, a tabela de 2026 por linha, os 3 pontos de atenção e 3 recomendações, cada uma com um dono e um prazo. Volumes em mil litros.
```

**O que esperar:** um relatório que já serve, mas com alguma recomendação genérica e número sem origem. É de propósito: o prompt 4 é a sua revisão.

## Prompt 4 · A sua correção

```
Três ajustes antes de eu aprovar:
1. A recomendação para a Linha 3 está genérica. Diga o que fazer, com um número que dê para conferir no mês que vem.
2. Cada número do texto diz de onde saiu: linha, produto e período.
3. Tire da conclusão o que é hipótese. Leve para uma seção no fim chamada "A confirmar".
```

**O que esperar:** a mesma página, mais curta na conclusão e mais precisa nas recomendações. Se ainda faltar algo, corrija de novo: a conversa é sua até você aprovar.

## Prompt 5 · Aprovado. E agora?

O relatório ficou do seu jeito. **Esta conversa não serve mais para o mês que vem**: ela carrega os números deste mês e as idas e vindas. O que serve é o **procedimento** que nasceu dela. Escolha um dos dois caminhos.

### 5a · Vira as instruções de um projeto

```
Aprovado. Este relatório vai se repetir todo mês, com a planilha nova. Escreva as instruções de um projeto do Claude que faça este trabalho do jeito que ficou aqui: o papel; o que ele recebe; os passos, nesta ordem (o raio-X e as perguntas sobre os problemas, depois os números, depois o relatório); o formato final; e cada correção que eu fiz nesta conversa, escrita como regra. Não use os números deste mês. Me entregue em um bloco só, para eu colar nas instruções do projeto.
```

**Depois:** Projetos › Novo projeto › cole nas Instruções. No mês que vem, uma conversa nova dentro do projeto e só a planilha nova.

### 5b · Vira uma skill

```
Aprovado. Transforme este trabalho numa skill chamada relatorio-producao-mensal. A descrição diz quando usar: quando eu mandar a planilha de produção do mês. O passo a passo segue esta conversa (o raio-X e as perguntas sobre os problemas, depois os números, depois o relatório), e cada correção que eu fiz vira uma regra. Não use os números deste mês. Me entregue o arquivo para eu instalar no Claude.
```

**Depois:** instale o arquivo no Claude. No mês que vem, em qualquer conversa, mande a planilha nova e peça o relatório de produção.

## Qual dos dois?

| | Projeto | Skill |
|---|---|---|
| Onde vale | dentro do projeto | em qualquer conversa ou projeto |
| Bom quando | o trabalho tem material fixo junto (a especificação, o POP, um modelo) | o procedimento é o mesmo, onde quer que você esteja |
| Neste encontro | o projeto da qualidade, da prática 4, nasceu assim | a skill da prática 4c é um exemplo pronto |
