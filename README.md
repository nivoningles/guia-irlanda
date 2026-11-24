# Guia Digital de Inclusão e Acesso a Serviços Públicos na Irlanda

Protótipo feito a partir do Trabalho Final da Atividade Extensionista I (UNINTER, CST em ADS):
*"Levantamento de Requisitos para Guia Digital de Inclusão e Acesso a Serviços Públicos na Irlanda"*.

- **Público:** imigrantes e novos residentes em Cork, com letramento digital básico.
- **ODS:** 4 (Educação de qualidade) e 10 (Redução das desigualdades).
- **Como abrir:** dê dois cliques em `index.html`. Funciona em qualquer navegador, inclusive no celular, sem instalar nada nem precisar de servidor.

## Barreiras do levantamento e como o guia responde

| Barreira identificada no trabalho | Resposta no guia |
|---|---|
| O fluxo PPSN → MyGovID → Revenue não é explicado de ponta a ponta | 5 etapas em ordem, com uma lista de passos que você marca e um link oficial em cada etapa |
| Verificação SAFE Nível 2 sem tutorial | Etapa 3 dedicada, com os pré-requisitos e o que fazer se der erro |
| Penalização financeira (Emergency Tax) | Etapa 5 explica o registro do emprego e a devolução do imposto pago a mais |
| Falta de tolerância ao erro | Caixas "Erro comum / Se der errado", progresso salvo e confirmação antes de apagar |
| Termos técnicos em inglês | Glossário com busca, que ignora acentos e maiúsculas; termos em inglês aparecem em itálico no texto |

## Requisitos funcionais (RF)

- **RF01:** mostrar o passo a passo em etapas ordenadas (documentos, PPSN, MyGovID verificado, Revenue, registro do emprego).
- **RF02:** deixar o usuário marcar cada passo e ver o progresso geral.
- **RF03:** salvar o progresso no aparelho entre uma visita e outra.
- **RF04:** mostrar os erros comuns e o que fazer em cada etapa.
- **RF05:** oferecer um glossário de termos em inglês, com busca.
- **RF06:** indicar onde pedir ajuda (Citizens Information, MyGovID, Revenue).
- **RF07:** permitir imprimir o guia.

## Requisitos não funcionais (RNF)

- **RNF01:** linguagem simples em português, com o termo em inglês ao lado.
- **RNF02:** acessibilidade: HTML semântico, navegação por teclado, link "Pular para o conteúdo", foco visível, áreas de toque de 44 px e suporte a leitor de tela (`aria-live` no progresso).
- **RNF03:** controle do tamanho da fonte e modo de alto contraste, que ficam salvos.
- **RNF04:** um único arquivo, sem dependências e sem servidor; funciona offline depois de baixado.
- **RNF05:** privacidade: nenhum dado sai do aparelho. Só o estado das caixas marcadas fica salvo, no `localStorage`.
- **RNF06:** respeita a configuração de reduzir movimento (`prefers-reduced-motion`).

## Os 7 Princípios do Desenho Universal

1. **Uso equitativo:** gratuito, funciona no celular e no computador, sem cadastro.
2. **Flexibilidade no uso:** permite ler na tela, imprimir, aumentar a fonte e usar alto contraste.
3. **Uso simples e intuitivo:** uma etapa por vez, numerada, na ordem certa.
4. **Informação perceptível:** os termos em inglês vêm explicados, e o estado de cada etapa aparece por cor e por texto.
5. **Tolerância ao erro:** alertas de erro comum, passos que você pode desmarcar e confirmação antes de apagar o progresso.
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
