# O seu sistema em 10 passos · prática 1D

**Claude na Indústria Química** · etapas 3 e 4

> **Fonte única dos prompts dos 10 passos.** O deck (`e3.py` e `e4.py`) e a página leem os blocos de código abaixo **na ordem**. O método veio do encontro de Claude Code de um treinamento in-company do professor, que partiu da prática 1D do curso *IA com Claude* (IEL Ceará). As frases são sugestões: adapte com as suas palavras.

**A regra:** cada passo tira uma adivinhação do Claude. Ele só constrói quando não sobra nada para adivinhar. Só passe para o próximo passo depois do OK.

| Tempo | Passos | Quando |
|---|---|---|
| **Preparar** · antes da conversa | 1 A dor · 2 A pasta · 3 O computador | etapa 3 |
| **Conversar** · ele entende o trabalho | 4 Ler · 5 A entrevista | etapa 3 |
| | 6 A referência · 7 A pesquisa | etapa 4 |
| **Construir** · só agora ele cria | 8 O plano · 9 Construir e conferir · 10 Validar | etapa 4 |

---

## Passo 1 · A dor

É a frase que você escreveu na etapa 1:

```
Toda [frequência], eu [a tarefa] à mão, e quem usa o resultado é [quem].
```

**Por quê:** sem a dor clara, ele resolve o problema errado, e muito bem feito. **Atenção:** pequena e frequente ganha de grande e rara.

## Passo 2 · A pasta

Crie uma pasta só para essa dor, em Documentos, com nome curto, sem acento e sem espaço (`meu-sistema`). Copie para ela, **sem mover o original**, um exemplo do arquivo que chega para você.

**Antes de copiar:** tem fórmula de produto, dado de cliente ou dado pessoal (nome, CPF, salário, matrícula)? No curso, só arquivo de exemplo, com os nomes trocados. **Por quê:** no chat, quem lembra é a conversa; no Claude Code, quem lembra é a pasta.

## Passo 3 · O computador

Na aba Code, na pasta, **conversa nova**:

```
Antes de começarmos: verifique se este computador tem Python 3.9 ou mais novo e as bibliotecas para ler e gravar Excel, Word e PDF e para rodar testes (openpyxl, python-docx, pypdf e pytest). Me diga o que falta e o comando para instalar, e só instale com a minha aprovação.
```

**Por quê:** para ler planilha, Word e PDF, o Claude escreve pequenos programas, e eles precisam do Python.

## Passo 4 · Ler

```
Coloquei nesta pasta um exemplo do arquivo que chega para mim no trabalho. Antes de qualquer pedido, leia o arquivo e me diga em poucas linhas o que tem nele, como está organizado e o que não fecha: coluna vazia, nome escrito de dois jeitos, unidade diferente, total que não bate. Não crie nada ainda. Só quero entender o que você enxerga.
```

**Por quê:** sem isso, ele constrói em cima de uma coluna que entendeu errado, e você só descobre no resultado.

## Passo 5 · A entrevista e o CLAUDE.md

Na mesma conversa, com o modo Plan **desligado**, porque no fim ele grava:

```
Agora quero criar um sistema simples, só neste computador, para essa dor. Me entreviste antes de propor qualquer coisa, uma rodada por vez, com perguntas de opção para eu escolher, um campo de outros e a sua recomendação em cada pergunta. Primeiro a dor: o que eu faço à mão, de quanto em quanto tempo, de onde vem o arquivo e quem usa o resultado. Depois, as regras da conta. Depois, o que o resultado mostra e como eu confiro que está certo. No fim, me mostre o resumo e, com o meu OK, grave no CLAUDE.md desta pasta a dor, as regras da conta e o que o resultado mostra.
```

**Por quê:** sem a entrevista, ele adivinha a regra, e erra em silêncio. **Atenção:** o CLAUDE.md é o manual da pasta; ele lê esse arquivo toda vez que você abre uma conversa ali. A entrevista é inspirada na skill grill-me, de Matt Pocock.

**Fim da etapa 3.** Feche a sessão (o prompt está no fim desta página). Na volta, conversa nova.

---

## Passo 6 · A referência

Copie para a sua pasta o `modelo-CLAUDE.md` (da etapa 4): é o manual do sistema de laudos que você viu funcionando. Conversa nova:

```
Nesta pasta está modelo-CLAUDE.md, o manual de um sistema que já funciona. Use o jeito dele de organizar como modelo para o nosso: as pastas, quem faz o quê, as frases que disparam cada tarefa e a cerca. Não copie as regras dele: as regras são as que combinamos na entrevista. Me mostre o que você aproveitaria e o que não serve para esta dor, e só mexa no CLAUDE.md com o meu OK.
```

**Por quê:** o jeito de organizar já foi testado. Sem o modelo, cada sistema nasce de um jeito.

## Passo 7 · A pesquisa, se fizer sentido

```
Pesquise como os sistemas do mercado resolvem essa dor e me diga, numa lista curta, o que cabe numa primeira versão simples e o que fica para depois. Se a pesquisa mudar algo do que combinamos, me pergunte antes de mexer no CLAUDE.md. Com o meu OK, anote no CLAUDE.md o que fica para depois.
```

**Por quê:** sem isso, você reinventa e esquece o básico, como não contar o mesmo lote duas vezes. **Atenção:** se a dor é muito própria da sua empresa, pule para o passo 8.

## Passo 8 · O plano

Ligue o modo **Plan** (Shift+Tab, ou o seletor ao lado do botão de enviar). Serve numa conversa nova: ele lê o CLAUDE.md.

```
Planeje a primeira versão só com o que está no CLAUDE.md: a pasta onde o arquivo entra, o programa que faz a conta, a tela que abre no navegador sem internet e a conferência que mostra que o número bate com o arquivo. Se faltar biblioteca, me peça antes de instalar. Me mostre o plano e espere o meu OK.
```

**Por quê:** corrigir o plano é barato; corrigir o sistema pronto, não.

## Passo 9 · Construir e conferir

Aprove o plano. Quando ele terminar de construir:

```
Rode com o meu arquivo de exemplo e me mostre a conferência: o total da tela e o total do arquivo, lado a lado. Depois, atualize o CLAUDE.md com o que cada pasta faz, o que eu posso mexer e a frase que atualiza a tela.
```

**Por quê:** é a contraprova antes de liberar o lote: sem ela, a tela parece certa e ninguém sabe se o número está.

## Passo 10 · Validar

Arquivo novo na pasta de entrada, **conversa nova**, e só a frase que ficou no manual (por exemplo, `leia os novos arquivos`). Cada incômodo vira um ajuste:

```
Quando [o que aconteceu], eu esperava [o que eu queria]. Proponha o ajuste, me mostre o antes e o depois, e espere o meu OK. Depois, acrescente uma linha no CLAUDE.md para isso não voltar.
```

**Por quê:** se a tela se refaz numa conversa nova, quem lembrou foi o CLAUDE.md, não a conversa.

---

## Entre um dia e outro · o fim de sessão

```
Vamos parar por aqui. Atualize o 00-aqui-paramos.md desta pasta (crie, se não existir): a data de hoje no topo e, em frases curtas, o que foi decidido, onde estamos, o próximo passo e o que depende de mim. Se o CLAUDE.md não diz para ler esse arquivo no começo de cada conversa, proponha essa linha. Me mostre antes de gravar.
```

## A cerca · vai escrita em todo CLAUDE.md

- **Dado sigiloso:** fórmula do produto, dado de cliente e dado pessoal não entram. No curso, só exemplo.
- **Ele sugere, você decide:** liberar, devolver e reclamar ao fornecedor é de quem a regra da casa diz.
- **Nada muda sem OK:** antes de gravar, ele mostra o antes e o depois.
- **Nada some:** o original nunca é movido; o processado vai para outra pasta; apagar, só você.
