# Modelo de CLAUDE.md · o manual do sistema de laudos de exemplo do curso

> Este é o manual do sistema de laudos que você viu funcionando no encontro 3. Use como modelo de organização (as pastas, quem faz o quê, as frases que disparam cada tarefa e a cerca), não de regras: as regras da sua pasta são as da sua entrevista.

Esta pasta é um sistema local do controle de qualidade da Química Serra Azul, uma indústria de
saneantes fictícia. Os fornecedores, lotes e números são inventados.

**A dor:** "Todo mês, eu confiro à mão os laudos de 3 fornecedores contra a especificação, e quem
usa o resultado é a coordenadora da qualidade."

O sistema lê os laudos, compara cada resultado com a especificação e diz, lote a lote, o que
liberar, o que segurar e o que reclamar ao fornecedor. Quem usa não é programador. Explique o que
está fazendo em português simples, em frases curtas.

No começo de cada conversa, leia o 00-aqui-paramos.md antes de qualquer pedido.

## Onde rodar

Abra o Claude Code dentro desta pasta, a que tem este `CLAUDE.md`. Todos os comandos abaixo
partem dela. No Windows, troque `python3` por `python` ou `py`.

Primeira vez neste computador:

1. `python3 --version` tem que dar 3.9 ou mais novo.
2. `python3 -m pip install openpyxl pytest`, só com o OK da pessoa.
3. `python3 -m pytest testes -q` tem que terminar com "32 passed".

## Pastas

| Caminho | O que é |
|---|---|
| `novos-arquivos/` | Onde a pessoa solta os laudos novos dos fornecedores, em .xlsx. |
| `arquivos-lidos/` | Para onde o sistema move os laudos depois de ler. Nunca apagar. |
| `especificacao/` | A planilha com o limite de cada parâmetro de cada matéria-prima. |
| `dados/historico.csv` | Todos os lotes já lidos, um parâmetro por linha. Quem grava é o script. |
| `painel.html` | O painel da última leitura. Abre no navegador, sem internet. |
| `sistema/ler_laudos.py` | O script que faz a conta. |
| `testes/` | Os testes, com uma cópia dos laudos de exemplo em `testes/exemplos/`. |

## Quem faz o quê

| Trabalho | Quem faz |
|---|---|
| Ler os 3 formatos, comparar com a especificação, contar, montar o painel | o script |
| Explicar o resultado, avisar o que é novo, perguntar o que falta | o Claude |
| Liberar, devolver, reclamar ao fornecedor, mudar a especificação | a pessoa |

Você não faz conta de cabeça. Todo número sai da saída do script ou do painel.

## As regras da conta

- **Três situações por lote.** Liberar: todo resultado dentro. Segurar: algum resultado vazio,
  ilegível, sem especificação, ou o mesmo lote em mais de um laudo. Reclamar ao fornecedor:
  algum parâmetro fora.
- **O limite conta como dentro.** Cloro ativo 12,5 % com máximo de 12,5 % é dentro.
- **"<0,05" é dentro** quando o limite é um máximo maior ou igual a 0,05.
- **ppm é o mesmo que mg/kg.** Se o laudo vier em % e a especificação em mg/kg, multiplica por
  10.000. Unidade sem conversão vai para Segurar.
- **O código da Quimisol muda de nome.** QS-01 é o MP-01 da especificação, QS-02 é o MP-02.
- **A Carnaúba não manda código.** O sistema acha a matéria-prima pelo nome.
- **Lote é fornecedor mais número do lote.** Lote que já está no histórico não entra de novo.
- **Mesmo número de lote em dois laudos** vai para Segurar. O sistema não escolhe um dos dois.
- **Parâmetro que a especificação pede e o laudo não trouxe** vai para Segurar.
- **Especificação com texto que o sistema não entende** vai para Segurar. Limite não se adivinha.
- **Índice de conformidade** = lotes para liberar ÷ (liberar + reclamar). O lote em Segurar
  ainda não foi julgado e fica fora da conta.

## O painel

Abra `painel.html` no navegador. De cima para baixo:

1. **Os números da leitura:** lotes lidos, liberar, segurar, reclamar.
2. **Precisa de decisão:** cada lote a reclamar ou segurar, com fornecedor, lote, matéria-prima,
   parâmetro, resultado e limite. Vermelho é só o que está fora.
3. **Por fornecedor:** lotes, liberar, segurar, reclamar e índice de conformidade.
4. **Conferência:** para cada arquivo, os lotes contados direto na planilha do fornecedor contra
   os lotes que o sistema leu. Na Carnaúba, a conta direta é a soma dos rodapés
   "Total de lotes no mês". Tem que dizer **Bate** nos três.

**Como conferir com os próprios olhos:** abra o laudo da Carnaúba em `arquivos-lidos/`, some os
rodapés das abas e compare com a linha dela na Conferência. Depois escolha um lote da lista de
decisão e ache o resultado no laudo.

Se a Conferência disser **Não bate**, o painel não está errado em silêncio: ele mostra a
diferença. Explique o motivo que o script deu (por exemplo, o mesmo número de lote em dois laudos)
e não trate o painel como fechado até a pessoa decidir.

## Rito: "leia os novos arquivos"

1. **Liste `novos-arquivos/`.** Diga quais arquivos chegaram e de qual fornecedor é cada um. Se
   não houver nenhum, diga isso e pare.
2. **Confira o ano e o período.** Se o nome do arquivo não tem ano (ex.: `Carnauba out.xlsx`),
   pergunte à pessoa: "Esses laudos são de qual mês e ano?". Use a resposta como `--ano AAAA`.
   Se o script parar com `PERGUNTA`, é a mesma pergunta: nada foi gravado.
3. **Mostre o antes e o depois, sem gravar:**
   ```
   python3 sistema/ler_laudos.py --simular
   ```
   (com `--ano AAAA`, se for o caso). Conte para a pessoa a Conferência, os lotes fora, os lotes
   a segurar e o que vai mudar: o histórico vai de quantos lotes para quantos, e quais arquivos
   vão para `arquivos-lidos/`. Espere o OK.
4. **Depois do OK, rode de verdade:**
   ```
   python3 sistema/ler_laudos.py
   ```
5. **Leia a saída e conte:**
   - `OK conferência`: o arquivo bate com o painel.
   - `ATENÇÃO não bate`: diga a diferença e o motivo. Não esconda.
   - `FORA`: lote, parâmetro, resultado e limite. É candidato a reclamar ao fornecedor.
   - `PENDENTE ... sem especificação`: **avise com destaque.** É matéria-prima ou parâmetro que
     a especificação não tem (em outubro, o ácido cítrico anidro). O lote fica em Segurar. Nunca
     esconda e nunca reprove: pergunte se a especificação vai ganhar essa linha.
   - `PENDENTE` com outro motivo: resultado vazio, ilegível ou lote repetido. Diga qual.
   - `INFO na borda`: resultado igual ao limite. Conta como dentro, mas vale a pessoa saber.
   - `ERRO`: nada foi gravado e os arquivos continuam em `novos-arquivos/`. Explique em palavras
     simples.
6. **Abra o painel** e diga onde ele está.

## O que a pessoa pode mexer

- Soltar laudos novos em `novos-arquivos/`.
- A especificação: incluir uma matéria-prima nova, mudar um limite, numa revisão nova. Mostre a
  linha antes e grave só com o OK.
- Pedir uma saída nova a partir do histórico, sem mudar a conta.

## O que não se mexe à mão

- `dados/historico.csv`: quem grava é o script.
- `painel.html`: é refeito a cada leitura.
- `arquivos-lidos/`: guarda os laudos originais. Nunca apagar.
- `sistema/`: só com pedido explícito e com os testes passando depois.

## Fica para depois

- Guardar no histórico a decisão que a coordenadora tomou em cada lote (liberado, devolvido).
- Mostrar a evolução de cada fornecedor mês a mês.
- Um quarto fornecedor ou um formato novo de laudo.

## A cerca

- **Dado sigiloso não entra.** Fórmula, dado de cliente e dado pessoal ficam fora desta pasta e
  desta conversa.
- **Ele sugere, você decide.** Liberar, devolver e reclamar ao fornecedor é de quem a regra da
  casa diz. O painel é uma lista para alguém decidir, não uma ordem.
- **Nada muda sem OK.** Antes de gravar, mostra o antes e o depois.
- **Nada some.** O original nunca é movido de fora da pasta. O processado vai para
  `arquivos-lidos/`. Apagar, só a pessoa.
