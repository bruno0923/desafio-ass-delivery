# desafio-ass-delivery
Resumo do aprendizado do desafio de projeto criando assistente de delivery

O assistente de entrega deve responder a perguntas comuns, como status de pedido, recomendações de jantar, como cancelar pedidos, entre outras. Cada cliente determinado tem um paladar e preferências diferentes, e o assistente oferece respostas adequadas para resolver o problema ou dúvida rapidamente.

Código:

{ "Versão": "2024-10-14", "StartAt": "AtendimentoCliente", "Estados": { "AtendimentoCliente": { "Tipo": "Escolha", "Escolhas": [ { "Variável": " $.pergunta", "StringEquals": "Qual o status do meu pedido?", "Next": "StatusPedido" }, { "Variable": "$.pergunta", "StringEquals": "Como faço para cancelar meu pedido ?", "Next": "CancelarPedido" }, { "Variable": "$.pergunta", "StringEquals": "O que você recomenda para o jantar?", "Next": "RecomendacaoJantar" }, { "Variable ": "$.pergunta", "StringEquals": "Como aplicar um cupom de desconto?", "Next": "AplicarCupom" }, { "Variable": "$.pergunta", "StringEquals": "Meu pedido está atrasado. O que posso fazer?", "Next": "PedidoAtrasado" } ], "Default": "PerguntaNaoEncontrada" }, "StatusPedido": { "Type": "Task", "Resource": "VerificarStatusDoPedido", "End": true }, "CancelarPedido": { "Type": "Task", "Resource": "CancelarPedido" , "Fim": verdadeiro }, "RecomendacaoJantar": { "Tipo": "Tarefa", "Recurso": "RecomendarRestaurante", "Fim": verdadeiro }, "AplicarCupom": { "Tipo": "Tarefa", " Recurso": "AplicarCupomDeDesconto", "End": true }, "PedidoAtrasado": { "Type": "Task", "Resource": "AjudarComPedidoAtrasado", "End": true }, "PerguntaNaoEncontrada": { "Type": "Fail", "Error": "PerguntaNaoEncontrada", " Cause": "A pergunta feita não está cadastrada no sistema." } } }

Informações dos Clientes 👥 e Respostas do Assistente: 💬🤖

Nome: Ana Clara Souza Idade: 25 anos Sexo: Feminino Preferência de paladar: Vegetariana Pergunta: "O que você recomenda para o jantar?" Resposta: "Ana, que tal experimentar o restaurante Green Garden? Eles oferecem opções deliciosas de saladas e pratos vegetarianos, como o 'Risoto de Cogumelos'. Uma ótima escolha para um jantar leve e saudável!"

Nome: João Marcos Silva Idade: 30 anos Sexo: Masculino Preferência de paladar: Comida apimentada Pergunta: "Qual o status do meu pedido?" Resposta: "João, seu pedido está a caminho! O entregador chegará em aproximadamente 15 minutos com o seu 'Tacos Mexicanos Apimentados'. Fique de olho no mapa de rastreamento!"

Nome: Pedro Alencar Idade: 40 anos Sexo: Masculino Preferência de paladar: Comida italiana Pergunta: "Meu pedido está atrasado. O que posso fazer?" Resposta: "Pedro, verificamos que seu pedido está com 10 minutos de atraso. Entramos em contato com o restaurante para obter mais informações e garantir que o entregador receba o quanto antes. Agradecemos sua paciência!"

Nome: Fernanda Costa Idade: 22 anos Sexo: Feminino Preferência de paladar: Sobremesas e doces Pergunta: "Como aplicar um cupom de desconto?" Resposta: "Fernanda, para aplicar o seu cupom, vá até o carrinho de compras e insira o código no campo 'Adicionar Cupom'. Não se esqueça de verificar a validade do cupom e o valor mínimo de compra!"

Nome: Carlos Mendes Idade: 35 Sexo: Masculino Preferência de paladar: Comida brasileira Pergunta: "Como faço para cancelar meu pedido?" Resposta: "Carlos, você pode cancelar o pedido acessando a aba 'Meus Pedidos' e selecionando o botão 'Cancelar Pedido'. Caso o pedido já tenha sido confirmado pelo restaurante, entre em contato com o suporte para verificar a possibilidade de cancelamento."

👷📋 Uso de Engenharia de Prompt neste desafio de Projeto!

A intenção do Prompt neste projeto foi criar uma simulação de um ciclo 🔄 de atendimento em um aplicativo 📲 de entrega 🚚 de refeições online , o recorte foi feito com 5 pessoas ficticias consultadas com idades entre 20-50 anos de ambos os sexos.

📋 Prompt Usado: Crie uma orquestração de fluxos de trabalho referente a um Projeto de um Assistente de Delivery! Crie perguntas pertinentes que um cliente faria em um aplicativo (Ifood etc.) e gere respostas eficazes para solucionar o problema do cliente. Crie 5 clientes fictícios de forma pesquisada dos sexos, com paladares diferentes.
O que é o AWS Step Functions? ➡️⬆️⬅️⬇️🔄
O AWS Step Functions é um serviço de orquestração de fluxos de trabalho que ajuda a criar, executar e monitorar fluxos de trabalho automatizados, facilitando a coordenação de múltiplos serviços da AWS e sistemas distribuídos. Ele permite definir fluxos de trabalho com etapas bem delineadas e estados controlados, sendo ideal para a automação de processos complexos .

O AWS Step Functions foi lançado pela Amazon Web Services em 2016 para ajudar desenvolvedores a criar fluxos de trabalho robustos e escaláveis ​​sem a necessidade de gerenciar manualmente a infraestrutura subjacente. A ideia central do serviço é fornecer um ambiente para definir a lógica de processos de negócios e fluxos de dados complexos através de uma abordagem de "State Machine" (máquina de estados) . Esse serviço foi desenvolvido para facilitar a criação de aplicações distribuídas, quebrando grandes processos em etapas discretas e automatizadas.

O AWS Step Functions é usado principalmente para:

Orquestração de serviços: Permite que diferentes serviços da AWS trabalhem juntos de forma coordenada, como Lambda , S3 , DynamoDB , ECS , entre outros.

Automação de fluxos de trabalho: Automatiza processos complexos que envolvem várias etapas, como pipelines de dados , fluxos de trabalho em aprendizado de máquina e processamento de eventos .

Divisão de processos: Permite dividir aplicações monolíticas em fluxos de trabalho modulares e reutilizáveis.

Controle de estados: Cada tarefa dentro de um fluxo de trabalho pode ser configurada para executar de acordo com as condições específicas, permitindo o gerenciamento de processos de longa duração, reexecuções e erros.

A linguagem do Step Functions é um tipo de linguagem de definição de estados chamada Amazon States Language ( ASL ), que permite descrever a forma declarativa do fluxo de trabalho que será executado . Essa linguagem é baseada em JSON e é usada para definir o comportamento do fluxo de trabalho, incluindo estados, transições, manipulação de erros, e muito mais.

A ASL define como os passos do fluxo de trabalho são coordenados e executados. Nessa linguagem, você descreve uma série de estados e transições entre eles, além de condicionar como cada estado pode ser acionado ou repetido.

Cada estado pode ser de um tipo específico, como:

Task: Executa uma tarefa, como uma função Lambda, ou invoca outro serviço da AWS.
Escolha: Implementa uma lógica condicional (if/else), permitindo que o fluxo tome caminhos diferentes.
Paralelo: Permite a execução de tarefas em paralelo.
Espere: Introduz um atraso temporário.
Mapa: Executa um conjunto de operações em cada item de uma lista.
Falha: encerra o fluxo de trabalho em caso de erro.
Sucesso: finaliza o fluxo de trabalho com sucesso.
Exemplo Simples de ASL (em JSON):

{ "Comment": "Exemplo simples de fluxo de trabalho do Step Functions", "StartAt": "PrimeiraTarefa", "States": { "PrimeiraTarefa": { "Type": "Task", "Resource": "arn:aws :lambda:REGION:ACCOUNT_ID:function:PrimeiraFuncao", "Next": "SegundaTarefa" }, "SegundaTarefa": { "Type": "Task", "Resource": "arn:aws:lambda:REGION:ACCOUNT_ID:function :SegundaFuncao", "End": true } } }

Como funciona o Workflow Studio: 🏢🎨
O Workflow Studio é uma interface low-code e visual do AWS Step Functions , onde os usuários podem desenhar seus fluxos de trabalho de maneira intuitiva , arrastando e soltando componentes, sem necessariamente escrever o código JSON da Amazon States Language manualmente . O Workflow Studio simplifica a construção de fluxos de trabalho, especialmente para usuários que não têm experiência com compromissos.

Principais Funcionalidades do Workflow Studio:

Editor Visual: Permite a construção de fluxos de trabalho arrastando componentes como tarefas, estados de decisão (Escolha), ciclos (Mapa), entre outros.

Ajustes no JSON: Apesar de ser uma ferramenta visual, o Workflow Studio ainda permite que você veja e edite o código JSON gerado em tempo real, permitindo ajustes manuais avançados, se necessário.

Templates e Exemplos: O Workflow Studio disponibiliza vários templates prontos para tarefas comuns (ex: processamento de imagens com Lambda, pipeline de dados com S3 e Glue), facilitando a criação de workflows sem a necessidade de partir do zero.

Simulação e Depuração: Permite simular a execução do fluxo de trabalho antes de implantá-lo, facilitando o ajuste fino e a detecção de erros antes de entrar em produção.

👷📋 Uso de Engenharia de Prompt neste desafio de Projeto!

Como este é um projeto ligado a um curso sobre Engenharia de Prompt e Claude 3 , eles naturalmente devem ser usados ​​nesta etapa de finalização. Para o prompt foi usado o modelo Claude 3 Haiku da Anthropic. Por questões de permissão e disponibilidade regional, não são todos os modelos do Bedrock que estão disponíveis para todos os usuários (ex: Amazon Titan), de maneira que ao escolher o modelo a ser usado, deve-se verificar quais estão disponíveis ao seu perfil , e devem ser dadas as devidas permissões para uso de algum novo modelo desenvolvido pela Bedrock.

