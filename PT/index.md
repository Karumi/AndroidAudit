**Seu aplicativo Android como uma cena de crime!**

Auditorias técnicas dos aplicativos iOS e Android tornaram-se uma parte integrante do nosso trabalho diário aqui na Karumi. Mesmo que ela pode parecer fácil, há vários detalhes de implementação para rever ao realizar a auditoria. Neste documento, vamos rever o que nós acreditamos que são as coisas mais importantes para verificar , separados por área técnica. 

**Sistema de Controle de Versão:**
 
Se os engenheiros estão usando controle de versão, o sistema e processo usado define várias coisas sobre o processo de desenvolvimento de software.

* Há um arquivo *ignore configurado corretamente para que arquivos de metadados e outros elementos dispensáveis não estão sob controle de versão?

* Bibliotecas de terceiros estão versionadas no repositório ao contrário de configuradas como depedências externas?

* Você usa mensagens suficientemente concisas e descritivas para cada commit?

* É razoável o tamanho dos commits?

* Todos os arquivos de um commit estão relacionados a mesma issue ou feature?

* Você usa branches seguindo algum esquema de branching como "feature branch" ou "git-flow"?

* Os nomes dos branches são suficientemente descritivos?

* Você usa o pull request e code review antes do merge no master?

    * Você tem alguma orientação de análise de código para rever um PR?

    * Em média, há quantos comentários para cada PR?

    * Quantas pessoas revisam cada PR?

    * Quantos votos (+1) é necessário antes do merge?

    * Quem é o responsável por fechar o branch?

* Você usa release branches para preparar cada lançamento?

* Quanto tempo tem o seu processo de teste aberto?

* Quantos consertos você contempla em sua release candidate antes de liberá-la?

* Você consegue fazer o checkout do código usado para construir quaisquer versões publicadas de seu aplicativo?

* Quantos hotfixes você lançou no ano passado?

* Você está finalizando os commits no branch antes do merge no master/develop?

* Os branches master/develop estão preparados para ser lançados a qualquer momento?

**Ferramentas de Build:** 

Ser capaz de reproduzir o processo de compilação na máquina de cada desenvolvedor e qualquer outro sistema externo como integração contínua é fundamental.

* Quantas bibliotecas você usa no projeto?

* O projeto está dividido em diferentes módulos?

* O projeto consome suas dependências através do Maven ou Gradle ou está usando jars locais?

* O projeto está perigosamente se aproximando do limite de contagem do método dex? Já está além deste ponto?

* Você usa bibliotecas que o seu projeto não necessita?

* O projeto está usando multidex?

* As depedências externas estão atualizadas?

* Você está respeitando as licenças de cada bibliotecas de terceiros?

* O projeto está usando alguma biblioteca de terceiros depreciada ou abandonada/sem manutenção?

* O SDK mínimo é o exigido pela a descrição do produto?

* O SDK alvo está atualizado?

* Proguard ou qualquer outra ferramenta de ofuscação está habilitada e configurada corretamente?

* As credenciais da keystore e Google Play Store estão armazenadas em a lugar seguro?

* A aplicação está usando build types corretamente?

* A aplicação está usando flavors corretamente?

* O build type da release está configurado corretamente?

* A opção de backup está ativada?

* A opção de lint está ativada e está aprovado com sucesso?

* Há uma ferramenta de análise configurada e executando sem erros?

* Há algum checkstyle configurado e executado sem erros?

* O application id e nome e código da versão estão configurados corretamente?

* Você está usando alguma estrutura ou estrategia para versionamento de id?

* Há ferramenta de integração contínua configurada?

* Há processo de release automático?

**Uso de recursos do Android:**

Existe uma vasta gama de dispositivos no mundo Android, cada um com seu próprio tamanho de tela, recursos, etc. Você precisa ter cuidado dobrado e aproveitar algumas das ferramentas do Android para fornecer a melhor experiência possível para o usuário, independentemente do seu dispositivo .

* Está faltando algum recurso de densities, flavors or build types?

* Há suporte na aplicação para todas as densidades requeridas pelo a descrição do produto?

* A aplicação está usando drawable/mipmap, fontes ou recursos vetoriais?

* Está faltando alguma tradução?

* O processo de tradução está automatizado?

* Qual é a linguagem default para as traduções?

* A aplicação usa alguma fonte customizada?

* A aplicação usa valores configurados dentro do arquivo de String em resources?

* A convenção de nomenclatura usada para definir os nomes dos recursos estão homogênia?

* Os parametros configurados relacionados ao hardware do dispositivo está configurado corretamente?

* Você está fornecendo suporte para tablets?

**Uso de Layouts Android:**

Como já dito antes, há uma ampla gama de dispositivos Android no mundo, cada um com tamanho de tela própria e densidade. Usar Layouts corretamente é fundamental

* O número de camadas de layouts na aplicação pode produzir problemas de performance?

* Você usa temas e estilos?

* Você reusa layouts usando a tag "include"?

* Você usa corretamente o tipo view group na implementação de layouts?

* Os layouts estão configuradas para tamanhos de telas diferentes?

* Há convenção de nomenclatura usada nos layouts e widgets?

* As listas estão usando os componentes de ListView e RecyclerView?

* Está usando Android Support Library corretamente?

**Uso de Permissões:**

Solicitar permissões define uma confiança entre os seus usuários e pode ajudar o seu app a integrar com outros serviços para proporcionar uma experiência agradável para seus usuários.

* Todas as permissões solicitadas são realmente necessárias?

* Há alguma permissão usada maliciosamente?

* Está faltando alguma permissão?

* O alvo da SDK usada é maior que 23 e a "permissões perigosas" solicitadas está usando a compatibilidade com o sistema de permissão?

* As permissões estão sendo solicitadas no momento que será usada?

* Há feedback para o usuário explicando a necessidade da permissão?

**Issues de Segurança:**

Como desenvolvedores, precisamos ser conscientes sobre a sua segurança do app, nós não queremos que os dados ou sessões dos usuários sejam roubados

* O cliente HTTP está configurado para usar HTTPS?

* O cliente HTTP está configurado para usar pinning de certificado e autenticação de mensagens com o HMAC?

* Há persistência da aplicação de informação sensíveis do usuário? Onde?

* Há persistência de informação na aplicação fora o armazenamento interno do sistema?

* Há logs traces quando executar um novo build de release?

* A aplicação tem código ofuscado?

* A aplicação está expondo qualquer Android content provider, receiver ou serviço de outras aplicações?

* O valor de "debuggable" da aplicação está desativado para release build?

**Push Notifications:**

Push é um grande mecanismo para manter nossos usuários informados sobre conteúdo relevante, a qualquer momento, mas é um problema mais complexo que parece à primeira vista.

* O aplicativo usa uma biblioteca de terceiros para implementar o sistema de notificações push?

* O sistema GCM está sendo usado para enviar informações para o aplicativo dentro das push notifications ou para mostrar apenas mensagens para o usuário?

* Qual é o comportamento da aplicação quando uma push notification é recebida?

* Qual é o comportamento da aplicação se a informação associada ao push notification não é a esperada?

* As notificações são mostradas ao usuário usando a compatibilidade da API?

**Performance:**

Performance é critico. Ninguém quer usar um aplicativo ruim, lento em seu dispositivo de $ 400-600. Desempenho é $.

* A aplicação tem qualquer vazamento de memória?

* Há analisador de memória como "LeakCanary" configurado em build de desenvolvimento?

* O modo Android Strict está ativado e configurado em build de desenvolvimento?

* Qual é a aplicação de threading usada? Você está usando async tasks, intent services ou qualquer outra biblioteca de terceiros?

* O número de thread executadas em background está causando problemas de performance?

* Você usa algum scheduler policy ou apenas cria threads sob demanda?

* Você tem em mente o modo Android Doze?

* A aplicação tem eventos de listening relacionados a estado de rede ou qualquer evento repetitivo do sistema operacional?

* A thread principal usada para executar tasks somente relacionadas a código de interface do usuário?

* A aplicação está usando qualquer caching policy?

* O cliente HTTP está configurado para usar timeout?

* O cliente HTTP está configurado para usar o GZIP?

* A UI da aplicação está executando 60 frames por segundo?

* Existe alguma view personalizada implementada alocando muita memória ou executando threads caras na interface do usuário?

* Você está testando seu aplicativo em dispositivos lower-end?

* O scrolling de Recycler Views está lento? 

* A manipulação de imagens implementada está usando alguma biblioteca de terceiros ou você tem uma solução personalizada?

* As imagens consumidas estão redimensionadas para o tamanho da tela ou é necessário baixar a imagem associada à tela do dispositivo?

* O uso de memória está razoável?

* Você está usando o modificador "static" do java corretamente?

* Há qualquer tarefa relacionada com gestão de imagens com mais de uma imagem ao mesmo tempo?

* Is the stats tracking system working on a background thread configured with the correct priority?
* Há sistema de rastreamento de estatísticas configurado e rodando em uma thread em background como prioridade?

* O código está otimizado no build de release?

**Estrutura de Pacotes Java:**

Uma boa estrutura de pacotes irá fazer com que seu código seja escalavel.

* A divisão de código de pacotes usados é por features ou conceitos? Exemplo: Login vs Usuário?

* Há visibilidade dos modificadores usado para esconder os detalhes das implementações dentro dos pacotes?

* Os pacotes estão fora do root package?

* As pastas de testes estão seguindos a mesma estrutura de pacotes implementada na pasta de código fonte?

* As features estão organizadas e usando a mesma estrutura dos pacotes?

* Há alguma classe fora do pacote correto?

* A convenção de nomenclatura de pacotes está seguindo uma regra homogênia?

* O nome do root package está relacionado ao nome da empresa??

**Codestyle:**

A base de código consistente em termos de estilo ajuda os nossos engenheiros para ler o código de uma maneira mais fácil. Suponhe-se, que um engenheiro deverua ler mais código do que escrever. Sendo assim, este é um conceito importante.

* O codestyle está homogênio?

* Você está usando hungarian notation?

* Existe alguma ferramenta de checkstyle configurada e executando sem erros?

* O código está seguindo o Java codestyle?

* Você usa tabs ou espaços?

* Os nomes das classes estão corretas?

* Você está usando o prefixo "I" para interfaces ou “Impl” de sufixos para implementações?

* Você está usando o nome correto das variaveis?

* Você está usando o nome correto para os campos?

* Você está usando o nome correto para os metódos?

* Os atributos e metódos possuem modificadores de visibilidade usados corretamentes?

* O código está em inglês?

* Você está usando javadoc?

* Você escreve comentários no seu código?

* Você usa constantes ou enums para evitar literais duplicados?

**Implementação Offline:**

Prover uma experiência boa offline é um diferencial para suas aplicações.

* A aplicação é usável quando não há conexão com internet?

* Qual é o comportamento da aplicação quando a conexão com a internet está lenta?

* Qual é o comportamento da aplicação quando um request foi barrado por uma falha de rede?

* Modificações de dados na aplicação são sincronizadas com o backend da aplicação quando a conexão com a internet for restabelecida?

* Há algum timeout configurado relacionado a conexões com internet?

* Há algum HTTP caching policy configurado?

* A sessão do usuário é renegociada automaticamente?

**Arquitetura:**

A arquitetura de aplicação do ponto de vista de código é uma das partes de uma auditoria que nos dá uma ideia mais clara sobre o aplicativo. Durante a revisão da arquitetura que será focado em conceitos relacionados com os S.O.L.I.D e os principios de Clean Code.

**Implementação da Camada de Apresentação:**

* Há qualquer padrão relacionado com a implementação GUI utilizada na aplicação? Model View Presenter ou Model view ViewModel poderia ser dois dos padrões mais utilizados para desenvolver aplicações. Está implementado corretamente?

* A implementação da camada de apresentação está associada a implementação de views?

* A implementação de view está acoplada a implementação do model?

* A camada de apresentação implementa requisitos de negócios?

* A implementação de view utiliza as ferramentas do SDK do Android corretamente?

* Você usa biblioteca de terceiros para simplificar a implementação das views?

* As diferentes características estão implementadas em diferentes activities ou fragmentos?

* O comportamento comum da UI é centralizado?

* Você está usando views customizadas para reusar código de UI?

**Implementação de Negócio:**

* Existe alguma camada de domínio ou a lógica é toda de negócio implementada dentro da camada de apresentação?

* As regras de domínio e diferentes requisitos de aplicação expressa dentro das principais entidades de lógica de negócios?

* A camada de negócio implementada está usando os principios de orientação objeto?

* A camada de negócio está acoplada ao Android SDK ou qualquer outra biblioteca de terceiro?

* A camada de negócio está acoplada a camada de apresentação?

* O modelo de negócios é anêmico?

* Você está usando modelo de negócios em excesso? 

* O código está basead em baixo acoplamento e alta coesão de componentes?

* Há manipulação de erro implementada usando exceptions ou qualquer outro mecanismo de erro?

* Há mapeamento de dados entre diferentes camadas?

* Os componentes externos (como esquema de banco de dados ou json parsing) influenciam no padrão do modelo de negócios?

* Os desenvolvedores estão abusando de herança?

* Há código duplicado?

* Biblioteca de injeção de depedência ou service locator configurados?

* A complexidade de classe/metódo está muito alta?

**Implementação da API do Cliente:**

* A implementação da API do cliente está acoplada ao SDK Android?

* A implementação da API do cliente está vazando detalhes relacionados ao HTTP client ou a biblioteca usada para a implementação de camada de rede?

* A implementação da API do cliente está enviando os headers corretamente?

* Qual é o comportamento da API do cliente para diferentes respostas HTTP?

* A implementação da API do cliente contempla mecanismos de autenticação?

* O processo de renovação de sessão está implementado corretamente?

* O JSON serializer suporta ofuscação?

* A implementação da API do cliente está segregado em diferentes clientes?

**Implementação de Armazenamento:**

* Onde a informação é armazenada?

* Você está lendo/escrevendo dados armazenados usando transações?

* O salvamento de informações sensíveis do usuário acontece de forma segura?

* A camada de armazenamento está usando biblioteca de terceiros?

* A camada de armazenamento está vazando detalhes da implementação?

* As tabelas/esquemas de armazenamento está modelados corretamente?

* As consultas enviadas ao armazenamento estão otimizadas?

* As APIs de persistência do Android SDK estão armazenando os dados no local correto? E quanto aos dados do banco de dados, preferências ou os pequenos dados de shared preferences e os arquivos em disco?

**Testes:**

* A aplicação tem testes?

* A aplicação é testável?

* A cobertura de testes da aplicação é baseada em diferentes estrategias de teste (unidade/integração/end-to-end)?

* Os testes possuem nomenclatura corretamente?

* Os testes possuem escopo corretamente?

* Há testes sem especificação?

* O tempo de execução de testes é razoável?

* A cobertura de testes código é baixa?

* Existe algum teste ignorado?

* Existe algum flaky tests?

* Você usa frameworks de testes atualizados?

* Existem algum teste sem asserts?

* Os testes escritos pelos mesmos desenvolvedores implementam o código de produção?

* Você tem uma equipe de QA para testes manuais?

* Você tem uma equipe de QA automatizando parte dos testes?

* Você usa algum sistema de integração contínua?

* Você usa builders, factories ou mothers para reduzir o esforço necessário para criar algumas entidades que são necessários apenas para testes?

* Os tests assertions estão escritos corretamente?

* Você executa mais de um assert de lógica por teste?

* Você tem diferentes conjuntos de testes relacionados com o mesmo projeto?

* Você está usando diferentes abordagens de teste para testar diferentes partes da aplicação?

* Você está usando o monkeyrunner?

* Você está seguindo alguma metodologia de TDD ou BDD?

* Você usa java para escrever os casos de testes?

Com base nesta lista relacionando diferentes temas, podemos afirmar a qualidade do aplicativo. Há outros pontos que também é necessário revisar mas esta lista contém os mais importantes. Você está dando as respostas corretas para todas estas perguntas?

***Por Pedro Vicente Gómez Sánchez.***
