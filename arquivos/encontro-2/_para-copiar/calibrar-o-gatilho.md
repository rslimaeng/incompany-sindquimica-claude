# Teste o gatilho · prática 4c

A skill `relatorio-producao-serra-azul` vem com a etiqueta (na tela, *description*) completa: diz **o quê**, **quando**, **com que falas** e **quando não**. Aqui você testa se ela acerta, frase por frase.

## Instalar

Baixe `relatorio-producao-serra-azul.skill` da página. No Claude, no menu da esquerda: **Plugins › Adicionar › Fazer upload de plugin** (a tela aceita o arquivo .skill). Na sua tela ainda aparece **Personalizar › Habilidades**? O caminho é esse, e o botão também é Adicionar. Se pedir, ligue a execução de código. Tem a skill do 5b instalada? Desligue durante o teste.

## As cinco frases do teste

Uma **conversa nova** para cada frase. Na frase 1, anexe `producao-lotes-2025-2026.xlsx`, a planilha da prática 4a. Repare se o Claude lê a skill antes de responder.

| # | Frase | Deve acionar? |
|---|---|---|
| 1 | Segue a planilha de produção de setembro. Monta o relatório do mês. | sim |
| 2 | Como fechou a produção das linhas esse mês? | sim |
| 3 | Preciso do fechamento mensal da fábrica para a diretoria industrial. | sim |
| 4 | Confere estes laudos de matéria-prima contra a especificação. | não |
| 5 | Escreve um comunicado para a equipe da Linha 3 sobre a parada de manutenção. | não |

## Leia a etiqueta

Abra a skill em **Plugins** (filtro **Skills**) e ache as quatro partes:

1. **O quê:** o que ela entrega, numa frase.
2. **Quando:** a situação, não o assunto.
3. **As falas:** as frases entre aspas, do jeito que a pessoa pede.
4. **Quando não:** os pedidos parecidos que não são dela.

## O pedido de ajuste

Use só se alguma frase errou.

```
A skill relatorio-producao-serra-azul [entrou / não entrou] quando eu escrevi: "[cole a frase]". Ela [não deveria / deveria] entrar. Ajuste só a description: acrescente a fala que faltou, ou o caso que faltou no "não use para". Mantenha as outras camadas e não passe de 1.024 caracteres. Me mostre o antes e o depois, e atualize a skill.
```

Depois, repita só a frase que errou, numa conversa nova.
