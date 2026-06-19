import { useState, useRef, useEffect } from "react";

const MODULES = [
  {
    id:1, title:"Fundamentos de IA", icon:"⚡",
    classes:[
      { id:1, title:"O que é IA de verdade — sem mitos", duration:"25 min",
        objective:"Entender o que a IA realmente faz — e por que essa clareza é sua primeira vantagem.",
        content:`A maioria das pessoas acha que a IA "pensa" como um humano. Esse é o erro mais comum — e vai te custar caro se você criar agentes com essa ideia na cabeça.\n\n**A IA não pensa. Ela prevê.**\n\nQuando você escreve algo no Claude ou ChatGPT, o modelo não "entende" sua pergunta como você entende uma conversa. O que ele faz é analisar padrões em bilhões de exemplos e prever qual é a resposta mais útil — gerando texto palavra por palavra.\n\nParece simples. Mas o resultado é extraordinariamente poderoso — porque esses padrões incluem linguagem, lógica, código, medicina, direito, negócios e muito mais.\n\n**Por que isso importa pra você:**\nA qualidade do agente depende quase completamente da qualidade das instruções que você dá. Um agente mal instruído não falha por causa da IA. Falha por causa do design.`,
        diagram:[{step:"ENTRADA",desc:"Sua mensagem ao agente",icon:"📝"},{step:"ANÁLISE",desc:"Detecta padrões em bilhões de exemplos",icon:"🔍"},{step:"PREVISÃO",desc:"Gera a resposta mais provável",icon:"⚙️"},{step:"SAÍDA",desc:"A resposta que você recebe",icon:"💬"}],
        exercise:{title:"Experimento das duas rodadas",instructions:['Rodada 1 — Escreva no Claude: "Me ajuda com informação sobre vidros"',"Copie a resposta completa.",'Rodada 2 — Escreva: "Atue como vendedor expert em vidros. Um cliente chegou e quer saber qual vidro usar numa porta residencial. Me faça 3 perguntas-chave antes de recomendar."',"Copie essa resposta também.","Traga as duas respostas aqui e analisamos juntos a diferença."]}},
      { id:2, title:"IA Generativa vs. Automação — qual usar quando", duration:"25 min",
        objective:"Entender a diferença entre IA generativa e automação — e como combinar as duas.",
        content:`Muita gente confunde IA generativa com automação. São ferramentas diferentes para problemas diferentes.\n\n**IA Generativa** cria conteúdo novo: texto, análises, respostas, resumos. É flexível, contextual, conversacional.\n\n**Automação** executa tarefas predefinidas: se acontece X, faz Y. É rígida, precisa, repetível.\n\n**A combinação é onde está o poder real.** Um agente profissional usa automação para se ativar e coletar dados, e usa IA generativa para processar, analisar e responder.\n\n**Exemplo prático:**\nCliente manda mensagem no WhatsApp → automação detecta e envia para o agente → IA generativa lê, entende e responde de forma inteligente → automação registra a conversa no sistema.`,
        diagram:[{step:"GATILHO",desc:"Mensagem, formulário, evento",icon:"🔔"},{step:"AUTOMAÇÃO",desc:"Coleta dados, organiza",icon:"⚙️"},{step:"IA GENERATIVA",desc:"Analisa, decide, redige",icon:"🧠"},{step:"AÇÃO",desc:"Responde, salva, alerta",icon:"✅"}],
        exercise:{title:"Classificar tarefas reais",instructions:["Pense numa empresa que você conhece (loja, clínica, restaurante).","Liste 5 tarefas que essa empresa faz repetidamente todo dia.","Para cada uma, classifique: é tarefa pra IA Generativa, Automação, ou as duas?","Traga sua lista aqui pra analisarmos juntos."]}},
      { id:3, title:"O que um agente pode — e o que não pode — fazer", duration:"20 min",
        objective:"Entender os limites reais de um agente IA para não prometer o que não existe.",
        content:`Um dos maiores erros de quem começa é superestimar o que um agente faz. Isso gera promessas que não se cumprem — e clientes insatisfeitos.\n\n**O que um agente PODE fazer:**\n— Responder perguntas com base em informações que você deu a ele\n— Seguir um roteiro de conversa de forma natural\n— Coletar e organizar informações do usuário\n— Gerar textos, resumos e análises\n— Tomar decisões simples dentro de regras definidas\n\n**O que um agente NÃO pode fazer:**\n— Acessar sistemas externos sem integração configurada\n— Saber o que aconteceu fora da conversa atual\n— Tomar decisões complexas sem orientação clara\n— Garantir 100% de precisão em dados críticos\n\n**A regra de ouro:**\nUm agente é tão bom quanto as instruções e informações que você deu a ele. Lixo entra, lixo sai.`,
        diagram:[{step:"PODE",desc:"Responder, coletar, organizar",icon:"✅"},{step:"DEPENDE",desc:"Integração com sistemas externos",icon:"⚠️"},{step:"NÃO PODE",desc:"Decidir sozinho sem regras",icon:"❌"},{step:"NUNCA",desc:"Substituir julgamento crítico",icon:"🚫"}],
        exercise:{title:"Teste de viabilidade",instructions:["Liste 3 ideias de agentes que você teria para algum negócio.","Para cada uma, avalie: é viável com o que um agente pode fazer?","Identifique o que seria possível e o que seria limitação real.","Traga suas ideias aqui para avaliarmos juntos."]}},
      { id:4, title:"Como a IA aprende — e por que o prompt é tudo", duration:"25 min",
        objective:"Entender como funciona o treinamento da IA e dominar o conceito de prompt como ferramenta de design.",
        content:`Você não programa um agente com código. Você programa com linguagem.\n\nIsso muda tudo. Significa que a habilidade mais importante não é saber programar — é saber se comunicar com precisão.\n\n**O que é um prompt:**\nÉ qualquer texto que você envia para a IA como instrução ou pergunta. Pode ser uma frase ou um documento completo de instruções.\n\n**A diferença entre prompt ruim e prompt bom:**\n\nPrompt ruim: "Atenda clientes da minha loja"\n\nPrompt bom: "Você é o assistente virtual da Loja X, especializada em produtos personalizados. Quando um cliente chegar, cumprimente com o nome da loja, pergunte o nome dele e qual produto está procurando. Se ele mencionar medidas, anote exatamente."\n\n**A diferença é específica, não longa.**\nUm bom prompt não precisa ser enorme. Precisa ser preciso.`,
        diagram:[{step:"CONTEXTO",desc:"Quem é o agente, onde está",icon:"🏢"},{step:"OBJETIVO",desc:"O que ele deve alcançar",icon:"🎯"},{step:"REGRAS",desc:"O que sempre/nunca fazer",icon:"📋"},{step:"FORMATO",desc:"Como deve responder",icon:"✍️"}],
        exercise:{title:"Reescrever prompts fracos",instructions:['Pegue este prompt fraco: "Responda perguntas dos clientes sobre produtos"',"Reescreva com contexto, objetivo, regras e formato.","Use uma loja fictícia de sua escolha como base.","Traga sua versão aqui para revisarmos."]}},
      { id:5, title:"Os 3 tipos de agente que existem no mercado", duration:"20 min",
        objective:"Conhecer as categorias principais de agentes IA para identificar oportunidades em qualquer negócio.",
        content:`Existem centenas de casos de uso para agentes IA. Mas quase todos se encaixam em 3 categorias principais.\n\n**Tipo 1 — Agente de Atendimento**\nFala com clientes. Responde perguntas, coleta informações, encaminha para humanos quando necessário.\nExemplo: Atendente virtual no WhatsApp de uma clínica.\n\n**Tipo 2 — Agente Administrativo**\nTrabalha com dados internos. Organiza, resume, gera relatórios, cria alertas.\nExemplo: Assistente que resume as vendas do dia e envia para o dono.\n\n**Tipo 3 — Agente de Processo**\nExecuta um fluxo específico passo a passo. Coleta, processa e entrega um resultado estruturado.\nExemplo: Agente que recebe pedido, valida informações, calcula preço e gera orçamento.\n\n**Você vai construir os 2 primeiros tipos neste curso.**`,
        diagram:[{step:"ATENDIMENTO",desc:"Fala com clientes externos",icon:"👤"},{step:"ADMINISTRATIVO",desc:"Trabalha com dados internos",icon:"📊"},{step:"PROCESSO",desc:"Executa fluxo estruturado",icon:"🔄"},{step:"HÍBRIDO",desc:"Combina 2 ou mais tipos",icon:"⚡"}],
        exercise:{title:"Identificar tipos de agente",instructions:["Pense em 3 empresas diferentes que você conhece.","Para cada uma, identifique: qual tipo de agente resolveria o maior problema?","Justifique sua escolha em 2 frases.","Traga sua análise aqui."]}},
    ]
  },
  {
    id:2, title:"Pensamento de Processos", icon:"🗺️",
    classes:[
      { id:6, title:"Como ler uma empresa em 10 minutos", duration:"25 min",
        objective:"Desenvolver a capacidade de entrar em qualquer negócio e detectar oportunidades rapidamente.",
        content:`Um designer de agentes não vende tecnologia. Vende clareza sobre problemas que o dono do negócio nem conseguiu nomear ainda.\n\n**As 4 sinais que você busca:**\n1. Tarefas que se repetem exatamente igual todo dia\n2. Informação que vive na cabeça de uma só pessoa\n3. Erros que acontecem sempre no mesmo ponto do processo\n4. Tempo perdido esperando, procurando ou explicando a mesma coisa\n\n**A pergunta mais poderosa:**\n"O que você faz todo dia que te toma tempo mas qualquer pessoa poderia fazer no seu lugar?"\n\nA resposta dessa pergunta sempre revela uma oportunidade para um agente.`,
        diagram:[{step:"OBSERVAR",desc:"O que a equipe faz o dia todo?",icon:"👁️"},{step:"PERGUNTAR",desc:"O que te toma mais tempo?",icon:"❓"},{step:"MAPEAR",desc:"Desenha o fluxo atual",icon:"🗺️"},{step:"DETECTAR",desc:"Marca os pontos de dor",icon:"🎯"}],
        exercise:{title:"Diagnóstico de empresa fictícia",instructions:["Imagine uma farmácia de bairro com 4 funcionários.","Clientes chegam, perguntam por remédios, às vezes não tem em estoque, às vezes precisam de receita.","Escreva: quais são os 3 maiores problemas que você vê?","Em qual dos 3 você colocaria um agente primeiro? Por quê?"]}},
      { id:7, title:"Como mapear um processo humano", duration:"30 min",
        objective:"Aprender a transformar um processo humano em um fluxo que um agente pode executar.",
        content:`Antes de criar um agente, você precisa entender exatamente o que o humano faz hoje. Isso se chama mapeamento de processo.\n\n**Por que mapear antes de criar:**\nSe você não entende o processo atual, vai criar um agente que resolve o problema errado.\n\n**Como mapear em 5 passos:**\n1. Escolha um processo específico\n2. Escreva cada passo que o humano dá, em ordem\n3. Identifique onde ele toma decisões\n4. Identifique onde ele precisa de informação externa\n5. Identifique onde ele perde tempo ou comete erros\n\n**Depois do mapeamento:**\nVocê vai ver claramente quais partes o agente pode assumir e quais ainda precisam de um humano.`,
        diagram:[{step:"PROCESSO ATUAL",desc:"Como o humano faz hoje",icon:"👨"},{step:"MAPEAMENTO",desc:"Cada passo documentado",icon:"📝"},{step:"ANÁLISE",desc:"Onde pode automatizar",icon:"🔍"},{step:"FLUXO DO AGENTE",desc:"O processo redesenhado",icon:"🤖"}],
        exercise:{title:"Mapeie um processo real",instructions:["Escolha: recepção de uma clínica ou atendimento de uma loja online.","Escreva passo a passo o que o atendente humano faz do início ao fim.","Marque com ✅ os passos que um agente poderia fazer.","Marque com ❌ os passos que ainda precisam de humano.","Traga seu mapeamento aqui."]}},
      { id:8, title:"Transformar processo em fluxo de agente", duration:"30 min",
        objective:"Converter um mapeamento de processo humano em um fluxo que um agente consegue executar.",
        content:`Você mapeou o processo humano. Agora vamos transformar isso em linguagem de agente.\n\n**A diferença fundamental:**\nO humano improvisa. O agente precisa de regras claras.\n\nIsso não é limitação — é vantagem. Quando você força a clareza nas regras, descobre inconsistências no processo que ninguém havia percebido.\n\n**Como converter:**\nCada passo humano vira uma instrução para o agente.\nCada decisão humana vira uma regra condicional.\nCada informação externa vira um dado que o agente precisa coletar ou receber.\n\n**Exemplo:**\nPasso humano: "Verifico se o cliente já é cadastrado"\nInstrução do agente: "Pergunte o nome completo do cliente. Se ele disser que já é cliente, informe que vai verificar o cadastro e peça para aguardar."`,
        diagram:[{step:"PASSO HUMANO",desc:"O que o humano faz",icon:"👤"},{step:"DECISÃO",desc:"Vira regra condicional",icon:"🔀"},{step:"INFORMAÇÃO",desc:"Vira dado a coletar",icon:"📋"},{step:"INSTRUÇÃO",desc:"Linguagem do agente",icon:"🤖"}],
        exercise:{title:"Converter processo em instruções",instructions:["Pegue o mapeamento que você fez na aula anterior.","Para cada passo marcado com ✅, escreva a instrução equivalente para o agente.","Use linguagem direta e específica — sem ambiguidade.","Traga suas instruções aqui para revisarmos."]}},
      { id:9, title:"Identificar o agente certo para cada problema", duration:"20 min",
        objective:"Desenvolver o julgamento para saber qual tipo de agente resolve qual problema — e quando não usar agente.",
        content:`Nem todo problema precisa de um agente. Saber quando NÃO criar um agente é tão importante quanto saber criar.\n\n**Quando um agente FAZ sentido:**\n— O processo se repete mais de 10 vezes por dia\n— As respostas seguem um padrão previsível\n— O erro humano tem impacto significativo\n— O tempo gasto poderia ser usado em algo mais estratégico\n\n**Quando um agente NÃO faz sentido:**\n— O processo é único e altamente variável\n— Requer empatia emocional profunda\n— Envolve responsabilidade legal ou médica direta\n— O volume é tão baixo que a automação não se paga\n\n**A regra prática:**\nSe você consegue escrever as regras do processo em uma folha de papel, provavelmente dá para criar um agente.`,
        diagram:[{step:"VOLUME ALTO",desc:"Repete +10x por dia?",icon:"📈"},{step:"PADRÃO CLARO",desc:"Tem regras definíveis?",icon:"📋"},{step:"IMPACTO REAL",desc:"Libera tempo estratégico?",icon:"⏰"},{step:"VIÁVEL",desc:"Cria o agente",icon:"✅"}],
        exercise:{title:"Triagem de oportunidades",instructions:["Liste 5 processos de qualquer empresa que você conhece.","Para cada um, aplique os 4 critérios: volume, padrão, impacto, viabilidade.","Classifique cada um como: Criar agente / Não criar / Investigar mais.","Traga sua triagem aqui."]}},
      { id:10, title:"Seu primeiro diagnóstico empresarial completo", duration:"35 min",
        objective:"Realizar um diagnóstico empresarial completo como faria com um cliente real.",
        content:`Esta aula é prática. Você vai fazer um diagnóstico completo de uma empresa fictícia.\n\n**A empresa:** Barbearia Estilo Certo\n3 barbeiros, 1 recepcionista, atendimento presencial e por WhatsApp.\n\nProblemas relatados pelo dono:\n— Clientes ligam e mandam mensagem o tempo todo perguntando horários disponíveis\n— Confirmação de agendamentos é feita manualmente\n— Às vezes o cliente não aparece e o horário fica vazio\n— O dono não sabe quantos clientes novos chegam por mês\n\n**Seu trabalho:**\nAnalisar essa empresa e entregar um diagnóstico com oportunidades reais para agentes IA com estrutura de 5 pontos:\n1. Processos identificados\n2. Pontos de dor principais\n3. Oportunidades para agentes\n4. Prioridade de implementação\n5. O que não automatizar`,
        diagram:[{step:"EMPRESA",desc:"Contexto e realidade atual",icon:"🏪"},{step:"PROBLEMAS",desc:"Dores identificadas",icon:"😤"},{step:"OPORTUNIDADES",desc:"Onde o agente ajuda",icon:"💡"},{step:"DIAGNÓSTICO",desc:"Documento estruturado",icon:"📄"}],
        exercise:{title:"Diagnóstico completo da Barbearia",instructions:["Leia o caso da Barbearia Estilo Certo acima.","Escreva o diagnóstico completo seguindo a estrutura dos 5 pontos.","Seja específico — cite processos reais, não generalidades.","Ao final, indique qual agente você criaria primeiro e por quê.","Este é o exercício mais importante do módulo."]}},
    ]
  },
  {
    id:3, title:"Design de Agentes", icon:"🏗️",
    classes:[
      { id:11, title:"Anatomia de um agente — as 7 partes", duration:"30 min",
        objective:"Aprender a construir a arquitetura completa de um agente antes de escrever uma única instrução.",
        content:`Um agente não é um prompt longo. É um sistema com partes bem definidas — igual a um funcionário que tem cargo, responsabilidades, limites e jeito de trabalhar.\n\n**As 7 partes de um agente:**\n\n1. **Missão** — Para que ele existe. Uma frase clara.\n2. **Personalidade** — Como ele fala e se comporta. Tom, estilo, nome.\n3. **Conhecimento** — O que ele sabe. Produtos, preços, políticas, FAQs.\n4. **Regras** — O que sempre faz e o que nunca faz.\n5. **Entradas** — Que tipo de informação ele recebe.\n6. **Saídas** — O que ele produz. Respostas, resumos, alertas.\n7. **Limites** — Onde termina a responsabilidade dele.\n\nSem missão clara, o agente divaga. Sem regras, ele improvisa errado. Sem limites, ele tenta fazer coisas que não consegue.`,
        diagram:[{step:"MISSÃO",desc:"Para que existe",icon:"🎯"},{step:"PERSONALIDADE",desc:"Como fala e age",icon:"😊"},{step:"CONHECIMENTO",desc:"O que sabe",icon:"📚"},{step:"REGRAS + LIMITES",desc:"O que pode e não pode",icon:"📋"}],
        exercise:{title:"Complete as 7 partes",instructions:["Escolha: loja de roupas, pet shop ou escola de idiomas.","Preencha as 7 partes para um agente de atendimento ao cliente.","Não precisa de código — só descrição clara de cada parte.","Traga seu design aqui para revisarmos."]}},
      { id:12, title:"Como escrever instruções que funcionam", duration:"35 min",
        objective:"Dominar a escrita de instruções precisas que geram comportamentos previsíveis no agente.",
        content:`Escrever instruções para um agente é uma habilidade. E como toda habilidade, tem técnica.\n\n**Os 5 princípios de uma boa instrução:**\n\n1. **Específica** — "Pergunte o nome do cliente" é melhor que "seja cordial"\n2. **Acionável** — Descreve um comportamento concreto, não uma qualidade abstrata\n3. **Sequenciada** — Quando a ordem importa, deixe claro\n4. **Com exemplos** — Mostre como uma boa resposta se parece\n5. **Com limites** — Diga o que fazer quando a situação foge do padrão\n\n**O erro mais comum:**\nInstruções vagas que parecem claras. "Seja profissional e atencioso" não diz nada ao agente. "Use linguagem formal, chame o cliente pelo nome e sempre confirme o que entendeu antes de responder" — isso sim funciona.`,
        diagram:[{step:"VAGO",desc:"Seja profissional",icon:"❌"},{step:"ESPECÍFICO",desc:"Use linguagem formal",icon:"✅"},{step:"COM EXEMPLO",desc:"Ex: 'Olá, Sr. João...'",icon:"💡"},{step:"COM LIMITE",desc:"Se duvidar, encaminhe",icon:"🔒"}],
        exercise:{title:"Reescrever instruções vagas",instructions:["Pegue estas 3 instruções vagas e reescreva cada uma:","1. 'Atenda bem os clientes'","2. 'Responda dúvidas sobre produtos'","3. 'Não prometa o que não pode cumprir'","Use os 5 princípios. Traga suas versões aqui."]}},
      { id:13, title:"Personalidade e tom de voz do agente", duration:"25 min",
        objective:"Criar uma personalidade consistente para o agente que represente a identidade do negócio.",
        content:`Um agente sem personalidade definida vai soar genérico. E genérico não vende, não fideliza, não representa a marca.\n\n**Por que personalidade importa:**\nO cliente não sabe que está falando com um agente. Ele está falando com "a empresa".\n\n**Como definir a personalidade — 4 perguntas:**\n1. Se o agente fosse uma pessoa, como ela seria? (formal/informal, jovem/experiente)\n2. Quais palavras ele NUNCA usaria?\n3. Como ele reage quando o cliente está frustrado?\n4. Como ele celebra quando o cliente fecha negócio?\n\n**Exemplo — Barbearia:**\nTom: Descontraído mas profissional. Usa gírias leves com clientes jovens, mais formal com clientes mais velhos. Nunca usa jargão técnico. Sempre termina com um convite para agendar.`,
        diagram:[{step:"IDENTIDADE",desc:"Quem é esse agente?",icon:"🪪"},{step:"TOM",desc:"Como ele fala?",icon:"🗣️"},{step:"REAÇÕES",desc:"Como responde a situações?",icon:"😊"},{step:"CONSISTÊNCIA",desc:"Sempre o mesmo jeito",icon:"🔄"}],
        exercise:{title:"Criar a personalidade do Agente 1",instructions:["Este é o início do seu Projeto 1 — o Agente Vendedor.","Escolha um negócio para ele representar (pode ser fictício).","Responda as 4 perguntas de personalidade.","Escreva 3 exemplos de como ele responderia a um cliente novo.","Traga aqui — vamos afinar juntos."]}},
      { id:14, title:"Fluxo de decisão — como o agente pensa", duration:"30 min",
        objective:"Criar o mapa de decisões que guia o comportamento do agente em diferentes situações.",
        content:`Um agente profissional não só responde perguntas. Ele toma decisões. E para tomar boas decisões, precisa de um mapa claro.\n\n**Como montar o fluxo:**\n1. Liste as situações mais comuns (80% das interações)\n2. Para cada situação, defina a resposta padrão\n3. Liste as situações de exceção (reclamação, pedido impossível, fora do escopo)\n4. Para cada exceção, defina o que fazer\n\n**A regra dos 80/20:**\nFoque em cobrir bem os 80% mais comuns. Os 20% de exceção, defina um comportamento padrão seguro: "Vou verificar isso com nossa equipe e te retorno em breve."`,
        diagram:[{step:"SITUAÇÃO",desc:"O que o cliente disse?",icon:"💬"},{step:"CLASSIFICAR",desc:"É comum ou exceção?",icon:"🔀"},{step:"RESPOSTA PADRÃO",desc:"80% dos casos",icon:"✅"},{step:"ESCALAR",desc:"20% de exceção",icon:"📞"}],
        exercise:{title:"Criar o fluxo de decisão do Agente 1",instructions:["Para o negócio que você escolheu na aula anterior:","Liste as 5 situações mais comuns que o agente vai encontrar.","Para cada uma, escreva a resposta padrão do agente.","Liste 2 situações de exceção e o que o agente deve fazer.","Traga seu fluxo aqui."]}},
      { id:15, title:"Testando e ajustando seu design", duration:"25 min",
        objective:"Aprender a testar um design de agente antes de construir — e como ajustar com base nos resultados.",
        content:`O design no papel nunca é perfeito. O teste é onde você descobre o que falta.\n\n**Como testar um design sem código:**\nSimples — você joga o papel do agente.\n\nPegue seu documento de design e peça para alguém fazer perguntas como se fosse um cliente real. Você responde usando APENAS o que está no seu design.\n\nOnde você travar, onde a resposta sair estranha, onde você precisar improvisar — esses são os pontos que precisam de ajuste.\n\n**O que ajustar:**\n— Instruções vagas: torne mais específicas\n— Situações não cobertas: adicione ao fluxo\n— Tom inconsistente: revise a personalidade\n\n**Regra prática:**\nFaça pelo menos 10 interações de teste antes de construir.`,
        diagram:[{step:"DESIGN",desc:"Documento de instruções",icon:"📄"},{step:"SIMULAÇÃO",desc:"Você joga o papel do agente",icon:"🎭"},{step:"FALHAS",desc:"Onde travou ou improvisou",icon:"🔍"},{step:"AJUSTE",desc:"Melhora o design",icon:"✏️"}],
        exercise:{title:"Simular o Agente 1",instructions:["Pegue o design completo do Agente 1 que você criou.","Peça para alguém fazer 10 perguntas como cliente.","Responda usando APENAS seu design — sem improvisar.","Anote onde você travou ou precisou improvisar.","Traga os pontos de falha aqui para ajustarmos o design."]}},
    ]
  },
  {
    id:4, title:"Construção Prática", icon:"🔨",
    classes:[
      { id:16, title:"Projeto 1 — Agente Vendedor: construindo o prompt central", duration:"45 min",
        objective:"Transformar o design do Agente 1 em um prompt real e funcional.",
        content:`Este é o momento que tudo se une. Você tem o design. Agora vamos transformar em prompt real.\n\n**Estrutura do prompt central:**\n\nIDENTIDADE\nVocê é [Nome], assistente virtual da [Empresa].\nSua missão é [missão em uma frase].\n\nPERSONALIDADE\nTom: [descreva]\nVocê nunca: [lista]\nVocê sempre: [lista]\n\nCONHECIMENTO\nProdutos: [lista]\nPolíticas: [regras importantes]\n\nFLUXO DE ATENDIMENTO\n1. [primeiro passo]\n2. [segundo passo]\n\nSITUAÇÕES ESPECIAIS\nSe o cliente reclamar: [resposta]\nSe você não souber: [resposta]\n\n**Agora é sua vez.**\nPreencha essa estrutura para o negócio que você escolheu.`,
        diagram:[{step:"DESIGN",desc:"Tudo que você criou",icon:"📐"},{step:"ESTRUTURA",desc:"Template do prompt",icon:"📋"},{step:"PREENCHIMENTO",desc:"Seus dados no template",icon:"✍️"},{step:"PROMPT REAL",desc:"Pronto para usar",icon:"🚀"}],
        exercise:{title:"Escrever o prompt completo do Agente 1",instructions:["Use a estrutura de prompt acima.","Preencha com os dados do negócio que você escolheu.","Seja específico em cada seção — sem generalidades.","Traga o prompt completo aqui — vamos testar juntos no Claude."]}},
      { id:17, title:"Projeto 1 — Testando o agente no Claude", duration:"40 min",
        objective:"Rodar o primeiro teste real do Agente 1 e ajustar com base nos resultados.",
        content:`Você tem o prompt. Agora vamos colocar o agente pra trabalhar de verdade.\n\n**Como testar no Claude:**\n1. Abra o Claude em uma nova conversa\n2. Cole seu prompt completo como primeira mensagem\n3. Escreva: "Confirme que entendeu seu papel respondendo como o agente pela primeira vez"\n4. O Claude vai assumir o papel do agente\n5. Agora simule ser um cliente real\n\n**O que observar durante o teste:**\n— O agente mantém o tom definido?\n— Ele segue o fluxo de atendimento?\n— Ele lida bem com situações de exceção?\n\n**Ciclo de melhoria:**\nTeste → Anota problemas → Ajusta prompt → Testa de novo\nFaça isso pelo menos 3 vezes antes de considerar o agente pronto.`,
        diagram:[{step:"PROMPT",desc:"Cola no Claude",icon:"📋"},{step:"TESTE",desc:"Simula cliente real",icon:"🎭"},{step:"PROBLEMAS",desc:"Anota falhas",icon:"📝"},{step:"AJUSTE",desc:"Melhora o prompt",icon:"🔧"}],
        exercise:{title:"3 rodadas de teste do Agente 1",instructions:["Rode o teste do Agente 1 no Claude.","Faça pelo menos 10 perguntas como cliente.","Documente 3 pontos que precisam de melhoria.","Ajuste o prompt e teste de novo.","Repita até o agente passar em 90% das situações.","Traga o prompt final aqui."]}},
      { id:18, title:"Projeto 2 — Agente Administrativo: design e estrutura", duration:"35 min",
        objective:"Iniciar o design do Agente 2 — o agente que trabalha com dados internos do negócio.",
        content:`O Agente 2 é diferente do Agente 1. Ele não fala com clientes — ele trabalha com dados internos.\n\n**O Agente Administrativo vai:**\n— Receber informações do dia (vendas, atendimentos, problemas)\n— Organizar e resumir essas informações\n— Gerar relatórios estruturados\n— Criar alertas quando algo fora do padrão acontece\n\n**Exemplo de uso real:**\nO dono da barbearia envia ao final do dia:\n"Hoje fizemos 12 cortes, 3 barbas. Tivemos 1 reclamação sobre espera. 2 clientes não apareceram."\n\nO agente responde com um resumo estruturado, compara com a média, aponta o alerta da reclamação e sugere ação.\n\n**Por que isso tem valor:**\nO dono economiza 30 minutos por dia de organização manual. Em um mês são 15 horas.`,
        diagram:[{step:"DADOS BRUTOS",desc:"Informações do dia",icon:"📥"},{step:"AGENTE",desc:"Processa e organiza",icon:"🤖"},{step:"RESUMO",desc:"Relatório estruturado",icon:"📊"},{step:"ALERTAS",desc:"Situações fora do padrão",icon:"🚨"}],
        exercise:{title:"Design do Agente 2",instructions:["Escolha o mesmo negócio do Agente 1 ou um diferente.","Complete as 7 partes do design para o Agente Administrativo.","Defina: que tipo de dados ele vai receber? Que relatório vai gerar?","Escreva 3 exemplos de alertas que ele deveria emitir.","Traga o design aqui."]}},
      { id:19, title:"Projeto 2 — Construindo e testando o Agente Administrativo", duration:"45 min",
        objective:"Construir o prompt do Agente 2 e testá-lo com dados reais simulados.",
        content:`Agora você vai construir o prompt do Agente Administrativo.\n\n**Estrutura específica:**\n\nIDENTIDADE\nVocê é o assistente administrativo da [Empresa].\nSua função é processar os dados diários e gerar relatórios estruturados.\n\nFORMATO DE ENTRADA\nVocê vai receber dados no seguinte formato: [descreva]\n\nPROCESSAMENTO\nAo receber os dados, você deve:\n1. [primeiro processamento]\n2. [segundo processamento]\n\nFORMATO DE SAÍDA\nSeus relatórios devem seguir este formato: [descreva]\n\nALERTAS\nEmita alerta quando: [condições]\n\nLIMITAÇÕES\nVocê não toma decisões. Você organiza informação para que o dono tome decisões.`,
        diagram:[{step:"ENTRADA",desc:"Dados brutos do dia",icon:"📥"},{step:"PROCESSAMENTO",desc:"Organiza e analisa",icon:"⚙️"},{step:"SAÍDA",desc:"Relatório estruturado",icon:"📊"},{step:"ALERTA",desc:"Situação fora do padrão",icon:"🚨"}],
        exercise:{title:"Construir e testar o Agente 2",instructions:["Escreva o prompt completo do Agente Administrativo.","Crie dados simulados de 3 dias de operação do negócio.","Cole o prompt no Claude e envie os dados simulados.","Avalie: o relatório gerado é útil? Está no formato correto?","Ajuste e teste mais 2 vezes.","Traga o prompt final e um exemplo de relatório gerado."]}},
      { id:20, title:"Refinamento final — os dois agentes prontos", duration:"40 min",
        objective:"Finalizar e documentar os dois agentes em versão apresentável para um cliente.",
        content:`Você tem os dois agentes funcionando. Agora vamos profissionalizar.\n\n**O que cada agente precisa ter na versão final:**\n1. Nome e identidade definidos\n2. Prompt testado e funcionando\n3. Casos de uso demonstráveis (3 exemplos reais)\n4. Limitações documentadas (honestidade vende)\n5. Resultado mensurável (quanto tempo economiza)\n\n**Como apresentar para um cliente:**\nNão mostre o prompt. Mostre o resultado.\n\n"Este agente atende seus clientes no WhatsApp 24 horas por dia, responde as 10 perguntas mais comuns, coleta informações de pedido e te envia um resumo toda manhã."\n\nIsso é o que o cliente compra. O prompt é seu segredo.`,
        diagram:[{step:"AGENTE 1",desc:"Vendedor finalizado",icon:"🤖"},{step:"AGENTE 2",desc:"Administrativo finalizado",icon:"📊"},{step:"DOCUMENTAÇÃO",desc:"Casos de uso e resultados",icon:"📄"},{step:"APRESENTAÇÃO",desc:"Pronto para mostrar ao cliente",icon:"🎯"}],
        exercise:{title:"Documentar os dois agentes",instructions:["Para cada agente, escreva uma ficha de 1 página com:","Nome, missão, 3 casos de uso demonstráveis, 2 limitações, resultado mensurável.","Esta ficha vai ser seu material de vendas.","Traga as duas fichas aqui para revisão final."]}},
    ]
  },
  {
    id:5, title:"Ferramentas", icon:"🛠️",
    classes:[
      { id:21, title:"O mapa de ferramentas — o ecossistema completo", duration:"30 min",
        objective:"Conhecer o ecossistema de ferramentas disponíveis e entender qual usar para cada situação.",
        content:`Não existe uma ferramenta para tudo. Existem ferramentas especializadas e seu trabalho é saber qual usar para cada problema.\n\n**As 4 categorias que você precisa dominar:**\n\n**1. Modelos de linguagem** (Claude, GPT-4, Gemini)\nO cérebro do agente. Processa linguagem e gera respostas.\n\n**2. Interfaces de conversa** (Typebot, Voiceflow, ManyChat)\nOnde o usuário interage. Cria o fluxo visual da conversa.\n\n**3. Automação** (Make, Zapier, n8n)\nOs conectores. Liga o agente com outros sistemas.\n\n**4. Bases de conhecimento** (Notion, documentos, planilhas)\nO que o agente sabe. Informações que você fornece.`,
        diagram:[{step:"CÉREBRO",desc:"Claude / GPT-4 / Gemini",icon:"🧠"},{step:"INTERFACE",desc:"Typebot / Voiceflow",icon:"💬"},{step:"CONECTORES",desc:"Make / Zapier / n8n",icon:"🔗"},{step:"CONHECIMENTO",desc:"Docs / Notion / Sheets",icon:"📚"}],
        exercise:{title:"Montar o stack para 3 clientes",instructions:["Cliente A: Loja pequena, orçamento mínimo, só WhatsApp.","Cliente B: Clínica média, precisa de agenda + histórico.","Cliente C: Empresa grande, múltiplos departamentos, CRM próprio.","Para cada um: quais ferramentas você usaria? Por quê?"]}},
      { id:22, title:"Como obter e configurar sua API key", duration:"25 min",
        objective:"Criar conta na Anthropic, obter API key e configurar o acesso ao modelo.",
        content:`Esta é uma aula técnica essencial. A API key é o que conecta sua plataforma ao cérebro da IA.\n\n**O que é uma API key:**\nÉ uma senha única que dá acesso ao modelo de IA. Sem ela, sua plataforma não consegue falar com o Claude.\n\n**Como obter sua API key na Anthropic:**\n1. Acesse console.anthropic.com\n2. Crie uma conta gratuita\n3. Vá em "API Keys" no menu lateral\n4. Clique em "Create Key"\n5. Copie e salve em local seguro — ela aparece só uma vez\n\n**Segurança:**\nNunca compartilhe sua API key publicamente. Trate como uma senha bancária.\n\n**Custo:**\nA Anthropic cobra por uso. Para um estudante testando, o custo mensal é de centavos.`,
        diagram:[{step:"CONTA",desc:"console.anthropic.com",icon:"🖥️"},{step:"API KEY",desc:"Sua chave de acesso",icon:"🔑"},{step:"CONFIGURAR",desc:"Cola na plataforma",icon:"⚙️"},{step:"ATIVAR",desc:"Mentor IA funcionando",icon:"✅"}],
        exercise:{title:"Obter e configurar sua API key",instructions:["Acesse console.anthropic.com e crie sua conta.","Gere sua primeira API key.","Configure na plataforma do curso (botão no topo direito).","Envie uma mensagem ao Mentor IA para confirmar que está funcionando.","Anote: quanto de crédito inicial a Anthropic oferece?"]}},
      { id:23, title:"Ferramentas no-code — fazer sem programar", duration:"35 min",
        objective:"Conhecer as principais ferramentas no-code para construir e distribuir agentes sem escrever código.",
        content:`Você não precisa saber programar para criar agentes profissionais. As ferramentas no-code resolvem isso.\n\n**As 3 ferramentas no-code mais importantes:**\n\n**Typebot**\nCria fluxos de conversa visuais. Drag and drop. Integra com Claude via API. Gratuito para começar.\n\n**Make (antigo Integromat)**\nConecta sistemas. Quando algo acontece em um lugar, faz algo em outro.\n\n**Notion**\nBase de conhecimento. Você escreve as informações do cliente lá, o agente consulta quando precisa.\n\n**Stack completo para um cliente real:**\nClaude (cérebro) + Typebot (interface) + Make (conectores) + Notion (conhecimento)`,
        diagram:[{step:"TYPEBOT",desc:"Interface de conversa",icon:"💬"},{step:"MAKE",desc:"Conecta sistemas",icon:"🔗"},{step:"NOTION",desc:"Base de conhecimento",icon:"📚"},{step:"CLAUDE",desc:"Processa e responde",icon:"🧠"}],
        exercise:{title:"Explorar o Typebot",instructions:["Acesse app.typebot.io e crie uma conta gratuita.","Crie um fluxo simples de 5 passos: boas-vindas, nome, problema, resposta, despedida.","Não precisa integrar com IA ainda — só o fluxo visual.","Tire um print e traga aqui."]}},
      { id:24, title:"Integrando o agente com WhatsApp", duration:"40 min",
        objective:"Entender como conectar um agente ao WhatsApp — o canal mais usado no Brasil.",
        content:`No Brasil, WhatsApp é onde o negócio acontece. Um agente que não funciona no WhatsApp tem alcance limitado.\n\n**As 3 formas de integrar com WhatsApp:**\n\n**1. WhatsApp Business API (oficial)**\nA forma profissional. Requer aprovação do Meta. Custo mensal. Ideal para empresas médias e grandes.\n\n**2. Typebot + Z-API ou Evolution API**\nA forma mais usada por criadores de agentes no Brasil. Custo baixo. Mais simples de configurar.\n\n**3. ManyChat**\nPlataforma com integração nativa ao WhatsApp Business. Mais cara, mas muito mais simples.\n\n**Para começar:**\nRecomendo Z-API + Typebot. Custo de cerca de R$50/mês para clientes pequenos e médios.`,
        diagram:[{step:"CLIENTE",desc:"Manda mensagem no WhatsApp",icon:"📱"},{step:"Z-API",desc:"Captura e encaminha",icon:"🔗"},{step:"TYPEBOT",desc:"Processa o fluxo",icon:"⚙️"},{step:"CLAUDE",desc:"Gera resposta inteligente",icon:"🧠"}],
        exercise:{title:"Pesquisar e comparar integrações",instructions:["Pesquise os preços atuais de: Z-API, Evolution API e ManyChat.","Para um cliente com 500 mensagens/mês, qual seria o custo de cada opção?","Qual você escolheria para um primeiro cliente pequeno? Por quê?","Traga sua análise aqui."]}},
      { id:25, title:"Montando o stack completo para um cliente real", duration:"45 min",
        objective:"Montar o stack técnico completo para um cliente real de ponta a ponta.",
        content:`Esta é a aula de síntese do módulo.\n\n**O cliente:** Salão de beleza Bella Arte\n— 3 profissionais, 1 recepcionista\n— Atendimento por WhatsApp e presencial\n— Problema: muito tempo perdido com agendamentos manuais\n— Orçamento: até R$200/mês em ferramentas\n\n**O que você vai definir:**\n1. Qual modelo de IA usar\n2. Qual interface de conversa\n3. Qual integração WhatsApp\n4. Se precisa de automação\n5. Se precisa de base de conhecimento\n6. Custo total mensal das ferramentas\n\n**Este exercício é o mais próximo de um projeto real que você vai fazer no curso.**`,
        diagram:[{step:"CLIENTE",desc:"Necessidade real",icon:"🏪"},{step:"STACK",desc:"Ferramentas escolhidas",icon:"🛠️"},{step:"CUSTO",desc:"R$ total por mês",icon:"💰"},{step:"PROPOSTA",desc:"Solução completa",icon:"📄"}],
        exercise:{title:"Stack completo para o Salão Bella Arte",instructions:["Defina o stack completo de ferramentas para o Salão Bella Arte.","Justifique cada escolha em 1 frase.","Calcule o custo total mensal das ferramentas.","Escreva em 5 linhas o que o agente vai fazer para esse cliente.","Traga sua proposta técnica completa aqui."]}},
    ]
  },
  {
    id:6, title:"Vender Soluções", icon:"💼",
    classes:[
      { id:26, title:"Vender resultado, não tecnologia", duration:"25 min",
        objective:"Aprender a apresentar agentes IA como soluções a problemas reais — não como produtos tecnológicos.",
        content:`O erro mais comum ao vender IA: falar de IA.\n\nNenhum dono de restaurante quer "um agente de linguagem natural com integração API". Ele quer parar de perder reservas. Quer que sua equipe pare de repetir a mesma coisa 50 vezes por dia.\n\n**Venda o resultado, não a tecnologia.**\n\n"Este sistema vai atender seus clientes no WhatsApp, responder as 10 perguntas que eles sempre fazem, e te mandar um resumo toda manhã de quantos contatos novos você teve."\n\n**Os 4 resultados que vendem:**\n1. Economia de tempo (horas/mês liberadas)\n2. Redução de erros (menos retrabalho)\n3. Atendimento 24/7 (sem custo extra)\n4. Organização de informação (dados que você nunca teve)`,
        diagram:[{step:"PROBLEMA",desc:"O que dói no negócio",icon:"😤"},{step:"RESULTADO",desc:"O que muda com o agente",icon:"✨"},{step:"NÚMERO",desc:"Quanto tempo/dinheiro economiza",icon:"💰"},{step:"DECISÃO",desc:"Cliente compra",icon:"🤝"}],
        exercise:{title:"Transformar tech em valor",instructions:['Pegue esta frase técnica: "Agente IA com NLP integrado para atendimento multicanal"',"Reescreva como um vendedor falaria com o dono de uma padaria.","Calcule: se o agente economiza 1h30min por dia, quanto vale em 1 mês?","Crie uma frase de abertura de vendas para esse cliente.","Traga tudo aqui."]}},
      { id:27, title:"Como fazer o diagnóstico com um cliente real", duration:"30 min",
        objective:"Aprender a conduzir uma reunião de diagnóstico com um cliente para identificar oportunidades e construir confiança.",
        content:`A reunião de diagnóstico é onde você transforma um prospect em cliente.\n\n**As 5 perguntas do diagnóstico:**\n1. "Me conta um dia típico de operação aqui — do momento que abre até fechar."\n2. "Onde você perde mais tempo? O que você faz todo dia que qualquer pessoa poderia fazer no seu lugar?"\n3. "Já aconteceu de perder cliente ou venda por falta de agilidade no atendimento?"\n4. "Se você pudesse eliminar uma tarefa repetitiva amanhã, qual seria?"\n5. "Quanto você acha que essa ineficiência custa por mês — em tempo ou dinheiro?"\n\n**Por que essas perguntas funcionam:**\nElas fazem o cliente calcular o custo do problema. Quando ele percebe o custo, sua solução fica barata.`,
        diagram:[{step:"ESCUTAR",desc:"Deixa o cliente falar",icon:"👂"},{step:"PERGUNTAR",desc:"As 5 perguntas-chave",icon:"❓"},{step:"CALCULAR",desc:"Custo do problema",icon:"🧮"},{step:"PROPOR",desc:"Solução específica",icon:"💡"}],
        exercise:{title:"Simular uma reunião de diagnóstico",instructions:["Peça para alguém jogar o papel de dono de um negócio simples.","Conduza o diagnóstico usando as 5 perguntas.","Anote as respostas e identifique 2 oportunidades para agentes.","Esboce em 5 linhas a solução que você proporia.","Traga o resultado aqui."]}},
      { id:28, title:"Como criar e apresentar uma proposta", duration:"35 min",
        objective:"Criar uma proposta comercial profissional para venda de implementação de agentes IA.",
        content:`Uma proposta profissional não é um documento longo. É um documento claro.\n\n**Estrutura de proposta que fecha:**\n\n1. **O problema** (em palavras do cliente)\nUse exatamente o que ele disse no diagnóstico.\n\n2. **A solução** (em linguagem simples)\nO que o agente vai fazer. Sem jargão técnico.\n\n3. **O resultado esperado** (com números)\nQuanto tempo economiza, quantos atendimentos automatiza.\n\n4. **O que está incluído**\nDesign, configuração, testes, treinamento da equipe, suporte.\n\n5. **Investimento**\nImplementação (pagamento único) + Manutenção mensal (recorrente).\n\n6. **Próximo passo**\nUma ação clara: "Para começar, precisamos de uma reunião de 1 hora para mapeamento."`,
        diagram:[{step:"PROBLEMA",desc:"Palavras do cliente",icon:"💬"},{step:"SOLUÇÃO",desc:"O que o agente faz",icon:"🤖"},{step:"RESULTADO",desc:"Números concretos",icon:"📊"},{step:"INVESTIMENTO",desc:"Implementação + Manutenção",icon:"💰"}],
        exercise:{title:"Escrever uma proposta completa",instructions:["Use o diagnóstico que você fez na aula anterior.","Escreva uma proposta seguindo os 6 blocos da estrutura.","Defina um preço para implementação e um para manutenção mensal.","A proposta deve caber em 1 página.","Traga aqui para revisão."]}},
      { id:29, title:"Como definir seus preços", duration:"25 min",
        objective:"Aprender a precificar implementação e manutenção de agentes IA de forma sustentável.",
        content:`Preço errado mata o negócio. Barato demais: você trabalha muito e ganha pouco. Caro demais: não fecha.\n\n**Como pensar no preço:**\nNão pense no custo do que você fez. Pense no valor do que o cliente ganha.\n\nSe o agente economiza R$800/mês para o cliente em tempo de funcionário, cobrar R$500 de implementação e R$150/mês de manutenção é um negócio óbvio para ele.\n\n**Referências de mercado (Brasil):**\n— Agente simples (FAQ + coleta): R$800–R$1.500 implementação\n— Agente médio (fluxo + integrações): R$1.500–R$3.000 implementação\n— Agente complexo (múltiplos sistemas): R$3.000–R$8.000 implementação\n\n**Manutenção mensal:**\n20–30% do valor de implementação por mês.`,
        diagram:[{step:"VALOR GERADO",desc:"Quanto o cliente economiza",icon:"💰"},{step:"COMPLEXIDADE",desc:"Quanto trabalho é",icon:"⚙️"},{step:"MERCADO",desc:"O que outros cobram",icon:"📊"},{step:"SEU PREÇO",desc:"Justo e sustentável",icon:"🎯"}],
        exercise:{title:"Precificar 3 projetos",instructions:["Projeto 1: Agente de FAQ para loja pequena. Sem integrações.","Projeto 2: Agente de agendamento para clínica. Com Google Calendar.","Projeto 3: Agente vendedor + administrativo para empresa média.","Para cada um: defina implementação e manutenção mensal com justificativa.","Traga sua tabela de preços aqui."]}},
      { id:30, title:"Do Zero ao Negócio — seu plano para os próximos 30 dias", duration:"30 min",
        objective:"Criar um plano de ação concreto para conseguir os primeiros clientes nos próximos 30 dias.",
        content:`Você chegou até aqui. Tem dois agentes funcionando, sabe diagnosticar, sabe propor, sabe precificar. Agora é executar.\n\n**Os 3 erros que impedem a primeira venda:**\n1. Esperar o portfólio perfeito para começar a prospectar\n2. Ter medo de cobrar antes de se sentir "expert"\n3. Prospectar todo mundo ao invés de um nicho específico\n\n**Seu plano para 30 dias:**\n\nSemana 1: Escolha 1 nicho. Estude 5 empresas desse nicho.\nSemana 2: Entre em contato com 10 empresas. Ofereça diagnóstico gratuito de 30 minutos.\nSemana 3: Faça os diagnósticos. Envie propostas para os interessados.\nSemana 4: Feche o primeiro cliente.\n\n**A meta realista:**\n1 cliente fechado em 30 dias. Mesmo que seja por um preço baixo — o primeiro é para portfólio e aprendizado.`,
        diagram:[{step:"SEMANA 1",desc:"Escolher nicho + estudar",icon:"🎯"},{step:"SEMANA 2",desc:"Prospectar 10 empresas",icon:"📞"},{step:"SEMANA 3",desc:"Diagnósticos + propostas",icon:"📄"},{step:"SEMANA 4",desc:"Primeiro cliente fechado",icon:"🎉"}],
        exercise:{title:"Seu plano de 30 dias",instructions:["Escolha seu nicho — qual tipo de empresa você vai atender primeiro?","Liste 10 empresas desse nicho na sua cidade que você poderia contatar.","Escreva a mensagem de abordagem inicial (WhatsApp ou e-mail).","Defina: qual agente você vai oferecer para esse nicho como solução padrão?","Este é seu plano de lançamento. Traga aqui para revisão final."]}},
    ]
  },
];

const SYS = `Você é o professor e mentor do curso "Agentes IA: Do Zero ao Negócio". Seu papel é exclusivamente educativo: ensinar, guiar, corrigir exercícios e responder dúvidas sobre o conteúdo do curso. Responda SEMPRE em português do Brasil. Seja direto, claro e prático. Tom: como um mentor experiente — honesto, direto, sem rodeios, mas sempre construtivo. Quando corrigir um exercício, explique O QUE está bom, O QUÊ melhorar e POR QUÊ.`;

export default function App() {
  const [mi, setMi] = useState(0);
  const [ci, setCi] = useState(0);
  const [done, setDone] = useState(new Set());
  const [msgs, setMsgs] = useState([]);
  const [inp, setInp] = useState("");
  const [loading, setLoading] = useState(false);
  const [tab, setTab] = useState("lesson");
  const [sidebar, setSidebar] = useState(true);
  const [apiKey, setApiKey] = useState("");
  const [apiInp, setApiInp] = useState("");
  const [showApi, setShowApi] = useState(false);
  const endRef = useRef(null);

  const mod = MODULES[mi];
  const cls = mod?.classes[ci];
  const key = `${mi}-${ci}`;
  const total = MODULES.reduce((a,m)=>a+m.classes.length,0);
  const pct = Math.round((done.size/total)*100);

  useEffect(()=>{ endRef.current?.scrollIntoView({behavior:"smooth"}); },[msgs]);
  useEffect(()=>{
    setMsgs([{role:"assistant",content:`Bem-vindo à aula **${cls?.title}**.\n\nEstou aqui pra te guiar. Pode trazer dúvidas ou seu exercício aqui.`}]);
    setTab("lesson");
  },[mi,ci]);

  async function send() {
    if(!inp.trim()||loading) return;
    if(!apiKey){setShowApi(true);return;}
    const um={role:"user",content:inp};
    const nm=[...msgs,um];
    setMsgs(nm); setInp(""); setLoading(true);
    try {
      const ctx=`Módulo: ${mod.title}\nAula: ${cls.title}\nConteúdo: ${cls.content}\nExercício: ${cls.exercise.title} — ${cls.exercise.instructions.join(" | ")}`;
      const r=await fetch("https://api.anthropic.com/v1/messages",{
        method:"POST",
        headers:{"Content-Type":"application/json","x-api-key":apiKey,"anthropic-version":"2023-06-01","anthropic-dangerous-direct-browser-access":"true"},
        body:JSON.stringify({model:"claude-sonnet-4-6",max_tokens:1000,system:SYS+"\n\n"+ctx,messages:nm.map(m=>({role:m.role,content:m.content}))})
      });
      const d=await r.json();
      const reply=d.content?.find(b=>b.type==="text")?.text||"Não consegui processar.";
      setMsgs(p=>[...p,{role:"assistant",content:reply}]);
    } catch { setMsgs(p=>[...p,{role:"assistant",content:"Erro de conexão. Verifique sua API key."}]); }
    setLoading(false);
  }

  function next() {
    setDone(p=>new Set([...p,key]));
    const all=MODULES.flatMap((m,i)=>m.classes.map((_,j)=>({i,j})));
    const idx=all.findIndex(x=>x.i===mi&&x.j===ci);
    const nx=all[idx+1];
    if(nx){setMi(nx.i);setCi(nx.j);}
  }

  function rt(text) {
    return text.split('\n').map((line,i)=>{
      const parts=line.split(/\*\*(.*?)\*\*/g);
      return <p key={i} style={{margin:line===''?'8px 0':'2px 0'}}>{parts.map((p,j)=>j%2===1?<strong key={j}>{p}</strong>:p)}</p>;
    });
  }

  const S={fontFamily:"'Inter',-apple-system,sans-serif",background:"#0a0a0f",minHeight:"100vh",color:"#e8e8f0",display:"flex",flexDirection:"column"};

  return (
    <div style={S}>
      {showApi&&(
        <div style={{position:"fixed",inset:0,background:"rgba(0,0,0,0.85)",display:"flex",alignItems:"center",justifyContent:"center",zIndex:100}}>
          <div style={{background:"#111118",border:"1px solid #2a1a4a",borderRadius:"16px",padding:"32px",maxWidth:"440px",width:"90%"}}>
            <div style={{fontSize:"11px",color:"#7c3aed",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",marginBottom:"12px"}}>🔑 Ativar Mentor IA</div>
            <h2 style={{fontSize:"18px",fontWeight:"700",margin:"0 0 12px",color:"#e8e8f0"}}>Configure sua API Key</h2>
            <p style={{fontSize:"13px",color:"#888",lineHeight:"1.6",margin:"0 0 20px"}}>Acesse <strong style={{color:"#c084fc"}}>console.anthropic.com</strong>, crie uma conta gratuita e gere sua API key. Cole abaixo para ativar o Mentor IA.</p>
            <input value={apiInp} onChange={e=>setApiInp(e.target.value)} placeholder="sk-ant-..." style={{width:"100%",background:"#0a0a0f",border:"1px solid #2a2a4a",borderRadius:"8px",padding:"12px 14px",color:"#e8e8f0",fontSize:"13px",marginBottom:"16px",boxSizing:"border-box",outline:"none"}}/>
            <div style={{display:"flex",gap:"10px"}}>
              <button onClick={()=>setShowApi(false)} style={{flex:1,background:"#1a1a2e",border:"1px solid #2a2a4a",borderRadius:"8px",padding:"11px",color:"#888",fontSize:"13px",cursor:"pointer"}}>Cancelar</button>
              <button onClick={()=>{if(apiInp.trim()){setApiKey(apiInp.trim());setShowApi(false);}}} style={{flex:2,background:"linear-gradient(135deg,#7c3aed,#c084fc)",border:"none",borderRadius:"8px",padding:"11px",color:"white",fontSize:"13px",fontWeight:"700",cursor:"pointer"}}>Ativar Mentor IA</button>
            </div>
          </div>
        </div>
      )}

      <div style={{background:"#111118",borderBottom:"1px solid #1e1e2e",padding:"0 20px",height:"54px",display:"flex",alignItems:"center",justifyContent:"space-between",flexShrink:0}}>
        <div style={{display:"flex",alignItems:"center",gap:"10px"}}>
          <button onClick={()=>setSidebar(!sidebar)} style={{background:"none",border:"none",color:"#666",cursor:"pointer",fontSize:"18px"}}>☰</button>
          <span style={{fontSize:"14px",fontWeight:"700",color:"#c084fc",letterSpacing:"-0.3px"}}>AGENTES IA</span>
          <span style={{color:"#222",fontSize:"12px"}}>|</span>
          <span style={{fontSize:"12px",color:"#555"}}>Do Zero ao Negócio</span>
        </div>
        <div style={{display:"flex",alignItems:"center",gap:"10px"}}>
          <button onClick={()=>setShowApi(true)} style={{background:apiKey?"#0f2010":"#1a1a2e",border:`1px solid ${apiKey?"#166534":"#2a2a4a"}`,borderRadius:"6px",padding:"5px 10px",color:apiKey?"#4ade80":"#666",fontSize:"11px",cursor:"pointer",fontWeight:"600"}}>
            {apiKey?"✅ Mentor IA ativo":"🔑 Ativar Mentor IA"}
          </button>
          <span style={{fontSize:"11px",color:"#444"}}>{done.size}/{total}</span>
          <div style={{width:"80px",height:"3px",background:"#1e1e2e",borderRadius:"2px"}}>
            <div style={{width:`${pct}%`,height:"100%",background:"linear-gradient(90deg,#7c3aed,#c084fc)",borderRadius:"2px",transition:"width 0.5s"}}/>
          </div>
          <span style={{fontSize:"11px",color:"#c084fc",fontWeight:"600"}}>{pct}%</span>
        </div>
      </div>

      <div style={{display:"flex",flex:1,overflow:"hidden"}}>
        {sidebar&&(
          <div style={{width:"252px",background:"#0d0d15",borderRight:"1px solid #1a1a2a",overflowY:"auto",flexShrink:0}}>
            {MODULES.map((m,i)=>(
              <div key={i}>
                <div style={{padding:"14px 14px 4px",fontSize:"10px",color:"#444",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",display:"flex",alignItems:"center",gap:"6px"}}>
                  <span>{m.icon}</span> Módulo {i+1} — {m.title}
                </div>
                {m.classes.map((c,j)=>{
                  const k=`${i}-${j}`;
                  const active=mi===i&&ci===j;
                  const isDone=done.has(k);
                  return(
                    <div key={j} onClick={()=>{setMi(i);setCi(j);}}
                      style={{padding:"8px 14px",cursor:"pointer",background:active?"#1a1a2e":"transparent",borderLeft:active?"2px solid #c084fc":"2px solid transparent",display:"flex",alignItems:"flex-start",gap:"8px",transition:"all 0.15s"}}>
                      <span style={{fontSize:"11px",marginTop:"3px",flexShrink:0,color:isDone?"#4ade80":active?"#c084fc":"#444"}}>{isDone?"✓":active?"▶":"○"}</span>
                      <div>
                        <div style={{fontSize:"11px",color:active?"#e8e8f0":"#666",lineHeight:"1.4"}}>{c.title}</div>
                        <div style={{fontSize:"10px",color:"#333",marginTop:"2px"}}>{c.duration}</div>
                      </div>
                    </div>
                  );
                })}
              </div>
            ))}
          </div>
        )}

        <div style={{flex:1,display:"flex",flexDirection:"column",overflow:"hidden"}}>
          <div style={{padding:"18px 24px 0",borderBottom:"1px solid #1a1a2a",background:"#0d0d15",flexShrink:0}}>
            <div style={{fontSize:"10px",color:"#7c3aed",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",marginBottom:"5px"}}>
              {mod?.icon} {mod?.title} — Aula {cls?.id} de {total}
            </div>
            <h1 style={{fontSize:"18px",fontWeight:"700",color:"#e8e8f0",margin:"0 0 14px",letterSpacing:"-0.4px"}}>{cls?.title}</h1>
            <div style={{display:"flex"}}>
              {["lesson","exercise","chat"].map(t=>(
                <button key={t} onClick={()=>setTab(t)}
                  style={{padding:"7px 18px",fontSize:"12px",fontWeight:"600",background:"none",border:"none",borderBottom:tab===t?"2px solid #c084fc":"2px solid transparent",color:tab===t?"#c084fc":"#444",cursor:"pointer",transition:"all 0.15s"}}>
                  {t==="lesson"?"📖 Aula":t==="exercise"?"✏️ Exercício":"💬 Mentor IA"}
                </button>
              ))}
            </div>
          </div>

          <div style={{flex:1,overflowY:"auto",padding:"22px 24px"}}>
            {tab==="lesson"&&(
              <div style={{maxWidth:"700px"}}>
                <div style={{background:"#111118",border:"1px solid #1e1e2e",borderRadius:"10px",padding:"16px 20px",marginBottom:"22px"}}>
                  <div style={{fontSize:"10px",color:"#7c3aed",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",marginBottom:"7px"}}>🎯 Objetivo</div>
                  <p style={{fontSize:"13px",color:"#999",lineHeight:"1.7",margin:0}}>{cls?.objective}</p>
                </div>
                <div style={{fontSize:"14px",color:"#ccc",lineHeight:"1.9",marginBottom:"26px"}}>{rt(cls?.content||"")}</div>
                {cls?.diagram&&(
                  <div style={{marginBottom:"26px"}}>
                    <div style={{fontSize:"10px",color:"#333",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",marginBottom:"12px"}}>Fluxo do processo</div>
                    <div style={{display:"flex",alignItems:"center",flexWrap:"wrap",gap:"6px"}}>
                      {cls.diagram.map((s,i)=>(
                        <div key={i} style={{display:"flex",alignItems:"center"}}>
                          <div style={{background:"#111118",border:"1px solid #1e1e2e",borderRadius:"10px",padding:"12px 14px",textAlign:"center",minWidth:"100px"}}>
                            <div style={{fontSize:"20px",marginBottom:"5px"}}>{s.icon}</div>
                            <div style={{fontSize:"9px",fontWeight:"700",color:"#c084fc",marginBottom:"3px",textTransform:"uppercase",letterSpacing:"0.5px"}}>{s.step}</div>
                            <div style={{fontSize:"10px",color:"#555",lineHeight:"1.3"}}>{s.desc}</div>
                          </div>
                          {i<cls.diagram.length-1&&<div style={{color:"#1e1e2e",fontSize:"16px",margin:"0 2px"}}>→</div>}
                        </div>
                      ))}
                    </div>
                  </div>
                )}
                <button onClick={()=>setTab("exercise")} style={{background:"linear-gradient(135deg,#7c3aed,#c084fc)",border:"none",borderRadius:"8px",padding:"11px 22px",color:"white",fontSize:"13px",fontWeight:"700",cursor:"pointer"}}>
                  Ir para o exercício →
                </button>
              </div>
            )}

            {tab==="exercise"&&(
              <div style={{maxWidth:"700px"}}>
                <div style={{background:"#0f0f1a",border:"1px solid #2a1a4a",borderRadius:"12px",padding:"22px",marginBottom:"18px"}}>
                  <div style={{fontSize:"10px",color:"#7c3aed",fontWeight:"700",textTransform:"uppercase",letterSpacing:"1px",marginBottom:"10px"}}>✏️ Exercício Prático</div>
                  <h3 style={{fontSize:"15px",fontWeight:"700",color:"#e8e8f0",margin:"0 0 16px"}}>{cls?.exercise.title}</h3>
                  <div style={{display:"flex",flexDirection:"column",gap:"10px"}}>
                    {cls?.exercise.instructions.map((s,i)=>(
                      <div key={i} style={{display:"flex",gap:"12px",alignItems:"flex-start"}}>
                        <div style={{width:"22px",height:"22px",borderRadius:"50%",background:"#1e1e3a",border:"1px solid #7c3aed",display:"flex",alignItems:"center",justifyContent:"center",flexShrink:0,fontSize:"10px",fontWeight:"700",color:"#c084fc"}}>{i+1}</div>
                        <p style={{fontSize:"13px",color:"#bbb",lineHeight:"1.6",margin:0}}>{s}</p>
                      </div>
                    ))}
                  </div>
                </div>
                <div style={{background:"#111118",border:"1px solid #1a1a2a",borderRadius:"8px",padding:"12px 16px",marginBottom:"16px"}}>
                  <p style={{fontSize:"12px",color:"#444",margin:0}}>💡 Complete o exercício e traga suas respostas para a aba <strong style={{color:"#c084fc"}}>Mentor IA</strong>.</p>
                </div>
                <div style={{display:"flex",gap:"10px"}}>
                  <button onClick={()=>setTab("chat")} style={{background:"#1a1a2e",border:"1px solid #2a2a4a",borderRadius:"8px",padding:"10px 20px",color:"#c084fc",fontSize:"12px",fontWeight:"600",cursor:"pointer"}}>💬 Consultar mentor</button>
                  <button onClick={next} style={{background:done.has(key)?"#0f2010":"linear-gradient(135deg,#166534,#16a34a)",border:done.has(key)?"1px solid #166534":"none",borderRadius:"8px",padding:"10px 20px",color:done.has(key)?"#4ade80":"white",fontSize:"12px",fontWeight:"700",cursor:"pointer"}}>
                    {done.has(key)?"✅ Concluída":"Marcar como concluída →"}
                  </button>
                </div>
              </div>
            )}

            {tab==="chat"&&(
              <div style={{maxWidth:"700px",display:"flex",flexDirection:"column",height:"calc(100vh - 220px)"}}>
                {!apiKey&&(
                  <div style={{background:"#0f0f1a",border:"1px solid #2a1a4a",borderRadius:"10px",padding:"14px 18px",marginBottom:"14px",display:"flex",alignItems:"center",justifyContent:"space-between"}}>
                    <p style={{fontSize:"12px",color:"#666",margin:0}}>Configure sua API key para ativar o Mentor IA.</p>
                    <button onClick={()=>setShowApi(true)} style={{background:"linear-gradient(135deg,#7c3aed,#c084fc)",border:"none",borderRadius:"6px",padding:"7px 14px",color:"white",fontSize:"11px",fontWeight:"700",cursor:"pointer",flexShrink:0,marginLeft:"10px"}}>Configurar</button>
                  </div>
                )}
                <div style={{flex:1,overflowY:"auto",marginBottom:"12px",display:"flex",flexDirection:"column",gap:"10px"}}>
                  {msgs.map((m,i)=>(
                    <div key={i} style={{display:"flex",justifyContent:m.role==="user"?"flex-end":"flex-start"}}>
                      <div style={{maxWidth:"85%",padding:"11px 15px",borderRadius:m.role==="user"?"12px 12px 2px 12px":"12px 12px 12px 2px",background:m.role==="user"?"linear-gradient(135deg,#7c3aed,#9333ea)":"#111118",border:m.role==="assistant"?"1px solid #1e1e2e":"none",fontSize:"13px",lineHeight:"1.6",color:"#e8e8f0"}}>
                        {rt(m.content)}
                      </div>
                    </div>
                  ))}
                  {loading&&(
                    <div style={{display:"flex",gap:"4px",padding:"11px 15px",background:"#111118",border:"1px solid #1e1e2e",borderRadius:"12px 12px 12px 2px",width:"fit-content"}}>
                      {[0,1,2].map(i=><div key={i} style={{width:"5px",height:"5px",borderRadius:"50%",background:"#7c3aed",animation:`pulse 1s ease-in-out ${i*0.2}s infinite`}}/>)}
                    </div>
                  )}
                  <div ref={endRef}/>
                </div>
                <div style={{display:"flex",gap:"8px",background:"#111118",border:"1px solid #1e1e2e",borderRadius:"10px",padding:"9px 12px"}}>
                  <textarea value={inp} onChange={e=>setInp(e.target.value)}
                    onKeyDown={e=>{if(e.key==="Enter"&&!e.shiftKey){e.preventDefault();send();}}}
                    placeholder={apiKey?"Escreva sua dúvida ou traga seu exercício aqui...":"Configure sua API key para usar o mentor..."}
                    style={{flex:1,background:"none",border:"none",outline:"none",color:"#e8e8f0",fontSize:"13px",resize:"none",minHeight:"40px",maxHeight:"100px",lineHeight:"1.5",fontFamily:"inherit"}} rows={2}/>
                  <button onClick={send} disabled={loading||!inp.trim()}
                    style={{background:inp.trim()?"linear-gradient(135deg,#7c3aed,#c084fc)":"#1e1e2e",border:"none",borderRadius:"7px",width:"36px",height:"36px",cursor:inp.trim()?"pointer":"default",fontSize:"15px",alignSelf:"flex-end",flexShrink:0,transition:"all 0.2s"}}>↑</button>
                </div>
              </div>
            )}
          </div>
        </div>
      </div>
      <style>{`@keyframes pulse{0%,100%{opacity:.3;transform:scale(.8)}50%{opacity:1;transform:scale(1)}}*{box-sizing:border-box}::-webkit-scrollbar{width:4px}::-webkit-scrollbar-thumb{background:#2a2a3a;border-radius:2px}textarea::placeholder{color:#333}`}</style>
    </div>
  );
}
