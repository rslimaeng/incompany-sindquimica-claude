# Cinco plugins oficiais, um por área

Feitos pela Anthropic, com o código aberto: dá para ler cada receita antes de instalar.

- **A vitrine:** https://claude.com/plugins
- **As receitas, abertas:** https://github.com/anthropics/knowledge-work-plugins

**Como usar:** no Claude, **Plugins**, procure o nome, leia quem fez e o quadro **Segurança e acesso**, e clique em **Adicionar**. Aparece **Concluir configuração**: pode ignorar, é para ligar conector. Conversa nova e cole o pedido. Plugins são dos planos pagos. As receitas vêm em inglês; a resposta sai em português. Os dados dos exemplos são inventados.

## Operations · produção, qualidade, compras

Traz, entre outras: comparar fornecedor (`vendor-review`), escrever o POP (`process-doc`), enxugar um processo (`process-optimization`), levantar riscos (`risk-assessment`) e pedir uma mudança (`change-request`). **Atenção:** a `compliance-tracking` é de segurança da informação e privacidade (SOC 2, ISO 27001), e não de NR, Anvisa ou licença ambiental.

```
Use uma skill do plugin Operations para comparar dois fornecedores, em português simples e curto. No começo, me diga qual skill você usou. Responda aqui na conversa, sem criar documento e sem usar conector.

Compramos 12 toneladas de LESS por mês. O fornecedor A cobra R$ 6,00 o quilo e atrasou 4 das últimas 10 entregas. Por causa disso, a Linha 3 parou 2 vezes no semestre, e cada parada custou R$ 18.000. O fornecedor B cobra 8 % a mais e entrega em 5 dias.

Faça a conta dos dois em um ano, com o custo das paradas, mostre o risco de cada um e o que falta saber antes de decidir. Não invente número.
```

**O que esperar:** quase empate. A sai por R$ 936.000, com as paradas; B, por R$ 933.120, se nunca atrasar. A decisão depende do que ainda não se sabe, e ele diz o quê.

## Data · quem vive em planilha

Traz o raio-X de uma planilha (`explore-data`) e a conferência de uma análise antes de mostrar (`validate-data`). Anexe `laudos-recebimento-3tri-2026.xlsx`.

```
Use uma skill do plugin Data para fazer o raio-X desta planilha, em português simples, em meia página, sem termo de programação. No começo, me diga qual skill você usou. Responda aqui na conversa, sem criar documento e sem usar conector.

Quero saber o que cada linha representa, quantos lotes e fornecedores tem de verdade, e o que não fecha: repetido, vazio, unidade diferente, nome escrito de dois jeitos. Não corrija nada: liste e me pergunte.
```

**O que esperar:** 363 linhas, 120 lotes e 3 fornecedores com 5 nomes; o lote repetido, o resultado vazio, os 3 laudos sem data e as 2 unidades estranhas. No fim, as perguntas.

## Finance · financeiro e gestores

Traz a explicação de uma diferença (`variance-analysis`) e o fechamento do mês.

```
Use uma skill do plugin Finance para me explicar uma diferença, em português simples, sem termo de contabilidade, em meia página.

A conta de energia da fábrica em outubro veio R$ 84.000, e o planejado era R$ 70.000. A tarifa subiu 10 %. A produção ficou 5 % acima do plano.

De onde veio a diferença, quanto é de cada motivo e o que ficou sem explicação? No começo, me diga qual skill você usou.
```

**O que esperar:** os R$ 14.000 separados: R$ 3.500 da produção, R$ 7.350 da tarifa e R$ 3.150 sem explicação.

## Human Resources · quem lidera gente

Traz o roteiro de entrevista (`interview-prep`) e a avaliação de desempenho (`performance-review`). Não suba nome, salário nem dado de pessoa.

```
Use uma skill do plugin Human Resources para montar o roteiro de entrevista de um analista de qualidade, em português simples e curto. No começo, me diga qual skill você usou. Responda aqui na conversa, sem criar documento e sem usar conector.

A vaga: confere laudos de matéria-prima, fala com fornecedor e segura lote quando precisa. Quero 4 competências, uma pergunta sobre uma situação real para cada uma e a nota de 1 a 4, com o que é cada nota.

Nada de pergunta sobre idade, família, religião, saúde ou política.
```

**O que esperar:** as quatro competências, uma pergunta de situação real para cada uma, e a régua de 1 a 4.

## Customer Support · comercial e assistência técnica

Traz a resposta ao cliente (`draft-response`) e a triagem do que é urgente (`ticket-triage`).

```
Use uma skill do plugin Customer Support para escrever a resposta a uma reclamação técnica, em português simples, com até 120 palavras. No começo, me diga qual skill você usou. Responda aqui na conversa, sem criar documento e sem usar conector.

O caso: um distribuidor diz que 3 caixas do detergente chegaram separadas em duas fases e pede a troca. O laudo da contraprova sai em 3 dias úteis.

As regras: não admitir culpa nem prometer troca antes do laudo; pedir o número do lote e uma foto; dizer o próximo passo e o prazo.
```

**O que esperar:** cerca de 90 palavras, sem admitir culpa e sem prometer a troca, pedindo o lote e a foto, com o próximo passo e o prazo.

## Antes de instalar qualquer um

Leia quem fez e para onde ele pode mandar dados. Prefira os verificados. O selo **Comunidade** é de plugin feito por outra pessoa ou empresa: leia a receita antes. Na empresa, pergunte primeiro.
