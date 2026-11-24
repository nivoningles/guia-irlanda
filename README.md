# Guia Digital de Inclusão e Acesso a Serviços Públicos na Irlanda

Protótipo feito a partir do Trabalho Final da Atividade Extensionista I (UNINTER, CST em ADS):
*"Levantamento de Requisitos para Guia Digital de Inclusão e Acesso a Serviços Públicos na Irlanda"*.

- **Público:** imigrantes e novos residentes em Cork, com letramento digital básico.
- **ODS:** 4 (Educação de qualidade) e 10 (Redução das desigualdades).
- **Online:** https://nivoningles.github.io/guia-irlanda/
- **Como abrir no computador:** dê dois cliques em `index.html`. Funciona em qualquer navegador, inclusive no celular, sem instalar nada.

## Como o guia funciona

1. **Início:** a pessoa escolhe entre descobrir o próximo passo ou ir direto a um problema comum (Emergency Tax, MyGovID que não verifica, tirar o PPS).
2. **Perguntas:** no máximo 5 perguntas de sim ou não, uma por tela. "Não sei" mostra uma dica de como descobrir a resposta, e "Voltar" corrige uma resposta.
3. **Plano:** o guia monta só os passos que aquela pessoa precisa, na ordem certa, e destaca "Faça isto agora". Cada passo explica por que ele importa, o que levar, os passos para marcar, o erro mais comum e o link oficial.
4. **Termos em inglês:** viram botões; ao tocar, a explicação aparece logo abaixo.

A regra que monta o plano é a função `montarPlano`. Para rodar o autoteste, abra a página com `?teste` no endereço e veja o console.

## Barreiras do levantamento e como o guia responde

| Barreira identificada no trabalho | Resposta no guia |
|---|---|
| O fluxo PPSN → MyGovID → Revenue não é explicado de ponta a ponta | Diagnóstico por perguntas que monta um plano personalizado, na ordem certa |
| Verificação SAFE Nível 2 sem tutorial | Passo dedicado, com os pré-requisitos e o que fazer se der erro, e um atalho direto na tela inicial |
| Penalização financeira (Emergency Tax) | Pergunta sobre o contracheque e um passo para recuperar o imposto pago a mais |
| Falta de tolerância ao erro | Botão "Voltar", opção "Não sei" com dica, alertas de cuidado, progresso salvo e confirmação antes de apagar |
| Termos técnicos em inglês | Cada termo é um botão que mostra a explicação em português |

## Requisitos funcionais (RF)

- **RF01:** perguntar a situação da pessoa (sim / não / não sei) e permitir voltar.
- **RF02:** montar um plano personalizado, só com os passos necessários e na ordem certa.
- **RF03:** destacar o próximo passo e mostrar o progresso.
- **RF04:** salvar o plano e o progresso no aparelho entre uma visita e outra.
- **RF05:** mostrar, em cada passo, o motivo, o que levar, os erros comuns e o link oficial.
- **RF06:** explicar os termos em inglês dentro do próprio texto.
- **RF07:** indicar onde pedir ajuda gratuita (Citizens Information).
- **RF08:** registrar os acessos e coletar feedback (Google Forms).
- **RF09:** permitir imprimir o plano.

## Requisitos não funcionais (RNF)

- **RNF01:** linguagem simples em português, falando diretamente com a pessoa, com o termo em inglês explicado.
- **RNF02:** acessibilidade: HTML semântico, navegação por teclado, link "Pular para o conteúdo", foco movido para o título de cada tela, botões de pelo menos 44 px e suporte a leitor de tela.
- **RNF03:** controle do tamanho da letra e modo de alto contraste, que ficam salvos.
- **RNF04:** um único arquivo, sem dependências e sem servidor.
- **RNF05:** privacidade: só o primeiro nome é enviado, para o registro de acessos. As respostas e o plano ficam apenas no aparelho.
- **RNF06:** respeita a configuração de reduzir movimento (`prefers-reduced-motion`).

## Os 7 Princípios do Desenho Universal

1. **Uso equitativo:** gratuito, funciona no celular e no computador, sem cadastro.
2. **Flexibilidade no uso:** permite ler na tela, imprimir, aumentar a fonte e usar alto contraste.
3. **Uso simples e intuitivo:** uma pergunta por tela e um plano que destaca só o próximo passo.
4. **Informação perceptível:** os termos em inglês vêm explicados, e o estado de cada etapa aparece por cor e por texto.
5. **Tolerância ao erro:** botão "Voltar", opção "Não sei" com dica, alertas de erro comum, passos que você pode desmarcar e confirmação antes de apagar.
6. **Baixo esforço físico:** botões grandes e uso completo pelo teclado.
7. **Tamanho e espaço para uso:** layout que se adapta ao tamanho da tela e áreas de toque amplas.

## Registro de acessos e feedback (comprovação da Atividade Extensionista II)

No primeiro acesso, o guia pede o primeiro nome da pessoa e avisa para que ele serve. A pessoa também pode entrar sem informar o nome. Depois, a cada acesso, o nome é enviado a um Google Forms, que grava a data e o horário sozinho. A planilha de respostas é o "fluxo de dados" (nome, data e horário) que o roteiro pede.

**Como ligar o registro (uma vez só):**
1. No Google Forms, crie um formulário chamado "Registro de acessos – Guia Irlanda" com uma única pergunta de **resposta curta**, chamada "Nome".
2. Clique em ⋮ → **Gerar link pré-preenchido**, digite `teste` na pergunta e clique em **Gerar link** → **Copiar link**. O link vai ter um trecho parecido com `entry.123456789=teste`.
3. No `index.html`, preencha o bloco `CONFIG`:
   - `formulario`: o link do formulário, trocando o final `viewform?...` por `formResponse`. Exemplo: `https://docs.google.com/forms/d/e/XXXX/formResponse`.
   - `campoNome`: o trecho `entry.123456789`.
   - `linkOpiniao`: o link de um segundo formulário, com as perguntas de feedback. Ele aparece como botão no rodapé.
4. Abra o guia, entre com um nome de teste e confira se ele aparece em **Respostas** no Forms. Apague o teste depois.

Para o relatório, tire print da aba **Respostas → Ver no Planilhas**, que mostra a data/hora e o nome de cada acesso, e print das respostas do formulário de feedback.

Com o `CONFIG` vazio, nada é enviado. O nome fica salvo só no aparelho, e o guia não pergunta de novo.

## Limites

- O conteúdo resume os procedimentos oficiais. As regras podem mudar, e o guia sempre manda o usuário conferir o link oficial.
- O guia está só em português. Outras línguas ficam para a fase de Projeto/Implementação.
