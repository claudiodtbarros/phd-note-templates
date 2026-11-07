# Modelos de nota do PhD in Practice

Onze modelos de nota em Markdown para o acervo de quem estuda um programa do PhD in Practice. Cada modelo corresponde a um tipo da tabela "O que registrar, e quando", seção 2.1 do Manual do Praticante, e traz as seções que o Manual define para esse tipo, na mesma ordem, com o cabeçalho YAML que a manutenção do acervo usa (seção 2 do Manual).

O Manual diz quando cada nota se escreve e o que ela precisa conter; os modelos poupam o trabalho de copiar essas seções à mão a cada nota.

## Os modelos

| Modelo | Quando usar | Regime |
|---|---|---|
| [`ficha-fonte`](templates/ficha-fonte.md) | Ao concluir a leitura de uma fonte designada: questão, tese, método, evidência, limitações, lacunas e julgamento | Permanente |
| [`nota-conceito`](templates/nota-conceito.md) | Ao compreender um mecanismo a ponto de derivá-lo sem a fonte aberta | Prazo de revisão do tema |
| [`artefato-executavel`](templates/artefato-executavel.md) | Ao concluir um exercício de construção, com o que é preciso para reproduzi-lo | 12 meses a 3 anos |
| [`exercicio-autoral`](templates/exercicio-autoral.md) | Ao construir um exercício próprio, com a competência testada, os distratores e a solução | Permanente |
| [`analise-caso`](templates/analise-caso.md) | Na entrega de um caso, com hipóteses concorrentes, recomendação sob restrição e pré-registro | Imutável |
| [`post-mortem`](templates/post-mortem.md) | Ao receber a devolutiva de um caso, com as armadilhas e a regra extraída | Imutável |
| [`memorando`](templates/memorando.md) | Para parecer, posição negociada, relatório para decisor e registro de submissão ou de resposta externa | Imutável |
| [`peca-registro`](templates/peca-registro.md) | Para uma peça dirigida a não especialistas ou a um interlocutor adversarial | Imutável |
| [`registro-previsao`](templates/registro-previsao.md) | Para uma previsão datada, com confiança, critério de resolução e resolução | Até a resolução |
| [`disciplina`](templates/disciplina.md) | No início de uma disciplina, com objetivo, plano de horas e registro de execução | Atualizada a cada sessão |
| [`objeto-referencia`](templates/objeto-referencia.md) | Para um mapa de tema ou de disciplina: mapa de conteúdo, taxonomia, cronologia, tabela ou glossário | Prazo de revisão do tema |

A tabela do Manual tem ainda o `inbox`, a captura rápida de dúvidas e ideias. Ele não tem modelo porque não tem estrutura: basta um arquivo na pasta `inbox/`, processado em até uma semana.

## Como usar

1. Copie a pasta `templates/` para dentro do seu acervo, ou baixe só os modelos de que precisa.
2. Para cada nota, duplique o modelo do tipo, dê ao arquivo um nome em `kebab-case` que descreva o objeto (por exemplo, `attribute-lookup-algorithm.md`) e preencha o cabeçalho e as seções.
3. Mantenha as seções do modelo mesmo quando uma ficar curta: elas formam a estrutura mínima do tipo, e a revisão e a arguição contam com elas.

Os modelos usam dois marcadores, `{{title}}` e `{{date:YYYY-MM-DD}}`:

- **No Obsidian**, aponte o plugin nativo *Templates* para a pasta `templates/`; ao inserir um modelo, o plugin troca os marcadores pelo título da nota e pela data do dia.
- **Em qualquer outro editor** (VS Code, Zed, Typora, Vim ou outro), substitua os marcadores à mão: o título da nota e a data no formato `AAAA-MM-DD`.

Os marcadores do cabeçalho ficam entre aspas, e o YAML continua válido antes e depois da substituição, em qualquer ferramenta que leia o cabeçalho.

## O cabeçalho

Todo modelo declara o tipo (`type`), a última conferência (`last_verified`) e o prazo de revisão (`half_life`), além dos campos próprios do tipo. Os valores seguem este vocabulário:

| Campo | Valores |
|---|---|
| `estrato` | `S1` a `S9`, ou `transversal` quando a nota não pertence a um estrato |
| `estagio` | `E1` a `E4+`, ou `-` |
| `epistemic_status` | `semente`, `em-desenvolvimento`, `estavel`, `contestado` ou `revogado` |
| `half_life` | número seguido de `w` (semanas), `m` (meses) ou `y` (anos), como `2w`, `3m`, `12m`, `3y`; ou `permanente`, `imutavel`, `ate-resolucao` |
| `last_verified` | data no formato `AAAA-MM-DD` |
| `status` (em `disciplina`) | `planned`, `in-progress`, `active`, `paused`, `completed`, `archived` ou `abandoned` |
| `sources` | lista de identificadores resolvíveis (DOI, ISBN ou URL estável) |
| `up`, `related` | links para a nota superior e para as notas relacionadas |

Campo vazio ou lista vazia vale quando o campo não se aplica à nota. Um programa pode acrescentar campos próprios do domínio, declarados no seu Manual (seção 2.2), como a versão de referência da ferramenta que a nota descreve.

## Notas imutáveis

`analise-caso`, `post-mortem`, `memorando` e `peca-registro` registram o estado do julgamento numa data e não se editam depois de concluídos. Uma correção entra como nota nova, com link para a original e a razão da correção (Manual, seção 2.3). O aviso no topo desses modelos lembra essa regra.

## Revisão periódica

A combinação de `last_verified` e `half_life` indica quando uma nota vence: a nota precisa de revisão quando a data da última conferência mais o prazo de revisão já passou. A rotina semanal do Manual (seção 2.4) lista essas notas, por uma consulta do plugin Dataview no Obsidian ou por uma busca no cabeçalho em qualquer editor, e confronta cada uma com a fonte na versão corrente.
