# O caso da etapa 3 · pagar só o que chegou certo

**Claude na Indústria Química** · etapa 3 · comigo, passo a passo

> **Fonte única dos prompts do caso.** O deck (`e3.py`) e a página leem os blocos de código abaixo **na ordem**. Os prompts gerais dos 10 passos, para a sua dor, ficam em `passo-a-passo.md`.

A Química Serra Azul, **fictícia**, compra 10 matérias-primas de 5 fornecedores. Todo mês, a coordenação de suprimentos cruza a **nota fiscal**, o **pedido de compra** e o **laudo do lote** antes de liberar o pagamento. Cada fornecedor manda a nota num formato. O que não fecha vira dinheiro: preço acima do combinado, quantidade a mais, nota repetida, nota sem pedido e lote reprovado que veio faturado.

**A pasta `sistema-fornecedores/`:**

| Pasta | O que tem |
|---|---|
| `novos-arquivos/` | as notas e os laudos de janeiro a outubro de 2026 dos 5 fornecedores, e as vendas e as despesas do mesmo período |
| `cadastros/` | os pedidos de compra (com o que o almoxarifado recebeu) e a especificação das matérias-primas |
| `fornecedores/` | o cadastro, o logo e a foto de cada fornecedor |
| `documentos-padrao/` | a carta-modelo para o fornecedor |
| `identidade-visual/` | o design system e o logo da empresa, e `referencia/`: um exemplo real de tela, sem marca |
| `planejamento/` | o planejamento estratégico de 2026: os OKRs, as metas de receita, os clientes de 2025 e o orçamento de despesas |
| `produtos/` | a foto de cada produto da Serra Azul |

Novembro, até o dia 25 (`novembro-fornecedores.zip`), só entra no passo 10.

---

## Passo 1 · A dor

```
Todo mês, eu confiro à mão as notas fiscais dos 5 fornecedores contra o pedido de compra e o laudo do lote antes de liberar o pagamento, e quem usa o resultado é o financeiro.
```

## Passo 4 · Ler

Na aba **Code**, abra a pasta `sistema-fornecedores`. Conversa nova:

```
Esta pasta tem tudo o que eu uso para liberar o pagamento dos fornecedores: as notas fiscais e os laudos que chegaram (novos-arquivos), os pedidos de compra e a especificação das matérias-primas (cadastros), os dados, o logo e a foto de cada fornecedor (fornecedores), uma carta-modelo (documentos-padrao), o padrão visual da empresa (identidade-visual), o planejamento estratégico de 2026 (planejamento) e as fotos dos produtos (produtos). Em novos-arquivos também estão as vendas e as despesas. Antes de qualquer pedido, leia tudo e me diga, em poucas linhas por pasta, o que tem, como cada arquivo está organizado e o que não fecha entre eles: formato diferente, unidade diferente, nota que não bate com o pedido, número escrito como texto. Não crie nada ainda.
```

## Passos 5, 6 e 7 · A entrevista, a referência e a pesquisa, num pedido só

Na sua dor, cada passo é uma conversa: a entrevista (`passo-a-passo.md`, passo 5) coleta a dor, as regras e como conferir; a referência (passo 6) mostra como o resultado deve ficar, o visual e o jeito de organizar; a pesquisa (passo 7) mostra como o mercado já resolve. Aqui, num caso de demonstração, as três já foram feitas, e o resultado delas vem num pedido só, em três partes:

```
Agora quero um sistema que resolva essa dor, só neste computador. Mas ainda não é hora de construir: primeiro, você precisa entender o que eu quero. No meu trabalho de verdade, eu faria isso em três conversas: a entrevista, a referência e a pesquisa. Para ganhar tempo, aqui vai o que as três me dariam.

O QUE EU QUERO (a entrevista)
- A dor: todo mês eu cruzo nota fiscal, pedido de compra e laudo, lote a lote, antes de liberar o pagamento. Os arquivos chegam por e-mail. Quem libera sou eu, da coordenação de suprimentos; quem paga é o financeiro.
- Preço: até 2 % acima do preço do pedido, pago a nota. Acima disso, pago o preço do pedido, e a diferença vira cobrança ao fornecedor.
- Quantidade: pago o que o almoxarifado recebeu. O que veio faturado a mais vira cobrança.
- Qualidade: lote fora da especificação, sem especificação cadastrada ou sem laudo tem o pagamento retido até a qualidade decidir. O limite da especificação conta como dentro, e "<0,05" é conforme.
- Nota repetida: paga uma vez só, e a repetição não entra no faturado. Nota sem pedido: bloqueada até suprimentos confirmar.
- Como eu confiro: o total das notas na tela bate com o total dos arquivos, e cada nota aparece uma vez só.
- A frase que atualiza tudo, quando chegarem os arquivos do mês seguinte: "leia os novos arquivos".

COMO DEVE FICAR (a referência)
- O padrão visual da empresa está em identidade-visual/design-system-serra-azul.md: siga esse arquivo.
- Um exemplo real de como as telas devem ficar está em identidade-visual/referencia/: um sistema pronto, sem marca e com dados ilustrativos (abra o index.html e as imagens). Siga o esqueleto e os componentes; os dados vêm dos arquivos da pasta.
- Um sistema com cara de sistema de verdade: menu lateral, os números grandes do período (faturado, liberado para pagar, retido, bloqueado e cobrado a mais), gráficos, a lista do que fazer com cada nota, uma página por fornecedor, com o logo e a foto da pasta fornecedores, e uma análise que compara os fornecedores. O período vai de janeiro a dezembro de 2026, e eu escolho o mês, o trimestre ou o ano.

O QUE O MERCADO JÁ FAZ (a pesquisa)
- Os sistemas de contas a pagar conferem em três vias: o pedido, a nota e o recebimento. Os bons também avisam a nota repetida e seguram o pagamento do lote reprovado. Nesta primeira versão, ficam as regras acima. Fica para depois: a agenda de vencimentos, a leitura direto do e-mail e a aprovação em duas etapas.

Se faltar alguma decisão importante, me faça no máximo uma rodada de perguntas de opção. No fim, grave no CLAUDE.md desta pasta a dor, as regras, o que o resultado mostra, onde mora o padrão visual e o que fica para depois, e me mostre um resumo do que gravou. Não crie programa nem tela agora: o plano vem no próximo pedido.
```

## Passo 8 · O plano

Ligue o modo **Plan** (Shift+Tab, ou o seletor ao lado do botão de enviar):

```
Planeje a primeira versão só com o que está no CLAUDE.md: um programa que lê o que chegar em novos-arquivos, cruza nota, pedido e laudo, guarda o histórico e move o arquivo lido para arquivos-lidos; o painel.html no padrão visual, que abre no navegador sem internet; e a conferência que mostra que o total bate com os arquivos. Inclua também, como skills desta pasta, as tarefas que vão se repetir: atualizar o painel quando chegarem arquivos novos, escrever a carta ao fornecedor a partir de documentos-padrao e fazer o resumo do mês para a diretoria. Se faltar biblioteca, me peça antes de instalar. Me mostre o plano e espere o meu OK.
```

## Passo 9 · Construir e conferir

Aprove o plano. Quando ele terminar de construir:

```
Rode com os arquivos de janeiro a outubro e me mostre a conferência: o total da tela e o total dos arquivos, lado a lado, por fornecedor. Depois, atualize o CLAUDE.md com o que cada pasta faz, o que eu posso mexer e a frase que atualiza o painel. Crie o 00-aqui-paramos.md com onde paramos e escreva no CLAUDE.md que toda atualização termina atualizando esse arquivo.
```

Uma skill trabalhando:

```
Escreva a carta à Brisamar sobre a nota que chegou sem pedido.
```

## O sistema cresce · a visão da diretoria

Mesma conversa, ou conversa nova: o CLAUDE.md lembra tudo.

```
Agora, a visão da diretoria. Na pasta planejamento está o planejamento estratégico de 2026: os OKRs, as metas de receita de cada mês, os clientes de 2025 e o orçamento de despesas. Em novos-arquivos também estão as vendas e as despesas do ano, e em produtos, a foto de cada produto. Acrescente ao sistema, no mesmo padrão visual e com o mesmo seletor de período: uma página Estratégia, com cada OKR, quanto já andou e se está no ritmo (o ritmo é a meta proporcional até a última data dos dados); uma página Vendas e metas, com a receita contra a meta mês a mês, por produto (com a foto), por canal e por cliente; e uma página Resultado, com a receita, a matéria-prima (as notas dos fornecedores), as despesas contra o orçamento e a margem. Me mostre o plano antes de construir. No fim, a conferência: a receita da tela bate com o arquivo de vendas, e as despesas, com o de despesas. Atualize o CLAUDE.md, o 00-aqui-paramos.md e a skill que atualiza o painel, para as vendas e as despesas do mês seguinte entrarem pela mesma frase.
```

## Passo 10 · Validar: chegou novembro

Baixe `novembro-fornecedores.zip` e solte os 12 arquivos em `novos-arquivos/`. **Conversa nova**, e só a frase:

```
leia os novos arquivos
```
