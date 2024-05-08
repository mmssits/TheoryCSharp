
Em primeira instância, devemos saber responder a seguinte questão: como a web funciona?

A internet funciona  a partir de um protocolo chamado HTTP, que consiste basicamente em uma comunicação entre cliente/servidor:

![[Pasted image 20240229103526.png]]

# Aplicações monolíticas

São as aplicações que possuem o projeto como um todo em uma aplicação só, separado apenas por classes de acordo com a funcionalidade, e armazenadas no banco de dados. Como o esquema a seguir:

![[Pasted image 20240229103751.png]]

No entanto, essa arquitetura de aplicação possui alguns problemas, como:
- Demoras no deploy.
- Falhar podem derrubar o sistema como um todo.
- Se há só 1 projeto, é usada apenas 1 tecnologia.

# O que são microsserviços?

> s.n: Microsserviços são uma abordagem arquitetônica e organizacional do desenvolvimento de software na qual o software consiste em pequenos serviços independentes que se comunicam usando APIs bem definidas. Esses serviços pertencem a pequenas equipes autossuficientes.

Em uma arquitetura de microsserviços, o sistema é dividido em pequenas partes de aplicações (serviços). Ou seja, esse tipo de arquitetura consiste basicamente em um arranjo de microsserviços (pequenas aplicações), onde cada um desempenha uma função e suas próprias responsabilidades.

Abaixo, temos o diagrama dessa arquitetura:

![[Pasted image 20240229140038.png]]

Assim como pode-se observar no diagrama acima, os serviços estão armazenados individualmente nos bancos de dados, podendo, assim, estar também armazenado em bancos de dados diferentes, causando ainda maior flexibilidade.

Os microsserviços, para gerarem uma aplicação completa, necessitam se comunicar entre si. Essa comunicação ocorre pelo reconhecimento do *endpoint*, ou seja, onde a aplicação sabe como acessar os detalhes de um produto ou coisa do tipo.

A comunicação entre esses serviços podem ser feitas de diversas formas, como, por exemplo, através de HTTP. Um serviço pode realizar requisições para outro através de HTTP, utilizando APIs rest, ou até protocolos um pouco mais complexos, específicos para esse tipo de coisa, como GRPC ou algo do tipo.

O que isso quer dizer é que eu posso muito bem, de forma muito tranquila, ter uma equipe inteira cuidando desse serviço de produto, com uma tecnologia, uma _stack_, uma equipe de gestão, ou uma metodologia ágil sendo aplicada e outra equipe completamente diferente cuidando do projeto de pagamentos, com outra _stack_, com outra metodologia de desenvolvimento.

### Vantagens do uso de microsserviços

- Projetos independentes = tecnologias diferentes.
- Falha em 1 serviço é isolada.
- Deploys menores e mais rápidos.


### Desvantagens do uso de microsserviços

- Maior complexidade de desenvolvimento e infra.
- Debug mais complexo.
- Comunicação entre os serviços deve ser bem pensada.
- Diversas tecnologias pode ser um problema.
- Monitoramento é crucial e mais complexo.


# Quando utilizar microsserviços?

Para determinar quando usar a arquitetura de microsserviços, é importante ressaltar que começar um projeto inicialmente com microsserviçõs pode ser muito complexo e perigoso. 
Portanto, partimos do princípio de ***monolito por padrão***, onde sempre que um sistema for ser desenvolvido, ele adota a arquitetura monolítica para que se entenda as necessidade e relação de regras de negócio como um todo e, sequencialmente, separá-las conforme os pedaços desenvolvidos forem tendo maior frequência de solicitação de requisitos.

Abaixo, temos um diagrama que demonstra esse processo de maneira eficiente:

![[Pasted image 20240229144711.png]]


# Tipos de serviços

Quando falamos em padrões reais, existem alguns tipos de microsserviços que podem ser adotados em nossas aplicações. Alguns deles são: **data service**, **business service**, **translation service** e **edge service**.

#### Data Services

Um data service, traduzido como serviço de dado, é um tipo de um serviço que simplesmente vai expor dados, como se fosse uma fina camada, antes de seu banco de dados. De maneira resumida, o que ele faz é receber dados e realizar o processamento necessário para manter aqueles dados consistentes.
Dessa forma, se precisamos armazenar a data de atualização de determinado produto, esse serviço vai tomar conta de preencher esse campo, e se algo estiver em um formato inválido, ele também cuidará disso. Por fim, são serviços que mantém os dados consistentes.

#### Business Services

Um business service, ou serviço de negócio, é um tipo de serviço que, além de consumir dados de alguma forma, seja consumindo um data service ou tendo acesso direto ao banco de dados, ele fornece operações mais complexas.
Nessa relação com o data service, um tipo de serviço só fornece dados e os mantém consistente, e outro tipo agrega dados e fornece operações mais complexas.

#### Translation Services

Os translations services são, basicamente uma forma de acessar algum recurso externo, mas mantendo determinado controle. 
Por exemplo, podemos ter um serviço que a minha aplicação vai consumir outro serviço e esse outro serviço consome um recurso externo, nos trazendo maior controle. Assim, se esse serviço externo mudar, modificaremos apenas em um só local, de forma que seja algo existente, que podemos implementar.

#### Edge Services

Um edge service, como o nome já diz: serviço de ponta, é algo que é entregue diretamente para o cliente e pode ter necessidades específicas.
Por exemplo, imaginemos que temos um sistema que funciona tanto para web quanto para mobile, ambos tipos de dispositivo/cliente possuem necessidades específicas. Justamente por isso, podemos ter um edge service específico para cada um desses clientes, conforme suas necessidades.


# Separando serviços

Quando pensamos em microsserviços e em como implementa-lo, é importante entender como podemos separar esses serviços, ou seja, como parte da aplicação monolítica deve virar determinado tipo de serviço.

### Serviços de domínio/Domain Services

Serviços de domínio são, de maneira resumida, um tipo possível de Data Services, cujo propósito é fornecer acesso a determinado domínio e suas regras.
Pegamos, por exemplo, um pequeno domínio da aplicação, e separamos em um serviço. Para isso, é importante destacar alguns pontos:

- Domain-driven Design - é importante entender esse conceito para que haja uma melhor compreensão/conhecimento do "desenho" da arquitetura e domínio.
- Começar modelando o domínio, sem pensar em sua persistência.
- Avaliar as ações que serão disponibilizadas.
- Construir o serviço, pensando primeiro no contrato.
- REST e RPC podem andar juntos.


### Serviços de negócio

Serviços de negócio, ou business services, são serviços adequados para operações que demandam mais de um domínio. De maneira resumida, é a junção de diversos data services/serviços de domínio.
Quando pensamos com a visão de negócio, esse serviço é representado por um processo que possui os seguintes passos:
- Provê uma funcionalidade do negócio de mais alto nível.
- Permite encapsular domínios relacionados.

Para a criação de um serviço de negócio, por sua vez, realizamos as seguintes etapas:
- Identificar o processo que será exposto.
- Identificar os domínios que serão necessários nesse serviço.
- Definir a API que será utilizada, focando no domínio e não nos dados.
- Consumir serviços de domínio para executar os processos.


### Padrões/Quebra do monolito

**Strangler Pattern:**

Traduzido como padrão de estrangulamento. Este consiste em um "estrangulamento" do monolito, de maneira a extrai-lo em pequenas partes. Ele funciona por dois passos:

- Iniciar o processo isolando os dados e seu banco, dessa forma podemos separar o banco conforme os dados de cada processo e depois conectar cada banco específico com seu serviço base.
- Ou iniciar o processo isolando seu domínio, de modo que cada domínio/processo seja separado e conectado ao banco de dados como um todo, em seguida quebrando o banco também em partes.

**Sidecar Pattern:**

Às vezes, por exemplo, um serviço que recebe muitas requisições vai também fazer muitas requisições de log. Já um outro serviço que recebe pouca coisa vai precisar fazer menos log. Então podemos ter um pedaço de código que ajuda os outros microsserviços, mas estando dentro mesmo. Então é um pedaço de código compartilhado entre todos eles. Isso é conhecido como sidecar pattern.
Ele funciona a partir dos seguintes passos:
 - Determinar o processo comum.
 - Construir um módulo compartilhável.
 - Aplicar esse sidecar nos serviços que precisam dele.


# Integrando serviços

Alguns microsserviços precisam se conhecer para realizar alguns processos, por isso é importante integrá-los entre si. Essa integração pode ocorrer de diferentes formas:

### API Gateway

Podendo ser identificada como um "ponto único de entrada", é uma API que funciona exatamente como uma portaria: recebendo as requisições e sendo uma intermediária para destinar cada uma a seu serviço em específico. Nesse conceito, podemos destacar alguns pontos:

- Gateway fornece um proxy, uma fachada, para as necessidades reais, não permitindo que os clientes tenham acesso livre aos serviços, evitando um caos.
- **Desvantagem**: Esse portão de entrada pode se tornar um ponto central de falha, por ser o ponto intermediário de todo funcionamento.

**Comportamentos do Gateway:**
- Simplesmente autorizar e redirecionas os requests.
- Uso de Decorator para adicionar informações necessárias aos requests ou o contrário.
- Limitar o tráfego (resposta) enviada.


### Agregar processos

Um serviço de negócio agrega vários serviços de domínio para que haja uma aplicação completa. Um agregador de processos, no entanto, é o que agrega vários processos, ou seja, vários serviços de negócio. Visto que, um serviço de domínio é agregado por serviços de negócio que, por sua vez, agregam esses serviços de domínio.
Esse método é bem menos comum, mas é utilizado em situações em que há processos mais complexos, onde vários processos dependem de outros processos. Essa prática possui algumas definições pontuais:

- Serviços de negócio agregam serviços de domínio.
- Process aggregators, por sua vez, agregam serviços de negócio.
- Agregadores fazem as chamadas para os serviços necessários e montam a resposta certa.
- Podem (e devem) ter lógica de processamento.

**Construção de um process aggregators:**
- Definição de um novo modelo para representar os dados agregados.
- A partir do modelo, pensar na API que fornecerá as operações.


### Gateway Específico

O gateway específico consiste nada menos que no Edge Pattern, obtendo o mesmo conceito de ser um gateway específico para determinado(s) cliente(s). Esse gateway possui foco nas necessidades reais determinados clientes.
Quando falamos clientes, nesse caso, podemos interpretar como um cliente HTTP, ou seja, que irá chamar nossa API, ou cliente de negócio mesmo.
Existem projetos, ainda, que só trabalham com edge patterns, com edge services e não com API Gateways, ou seja, não existe um ponto único de entrada, mas sim um ponto único de entrada para cada tipo de cliente.

**Construção de um edge service/serviço de ponta:**
- Identificamos o cliente e suas necessidades.
- Construímos contratos específicos para o cliente.
- Modificamos os dados que são transferidos para garantir a otimização do processo.

Ainda, é importante salientar que existem a possibilidade de ter apenas Edges, sem Gateways.


# Lidando com Dados

### Múltiplos banco de dados

Quando temos um projeto com a arquitetura de microsserviços, a ideia é que haja o estabelecimento de um conceito chamado ***Single Service Database***, onde cada serviço (que necessitar) terá e se relacionará com seu próprio banco de dados. 

Isso irá permitir uma escalabilidade mais granular, ou seja, podemos ajustas os recursos do banco de dados de acordo com as necessidades específicas de cada serviço. Um exemplo é que um serviço com menos requisições pode utilizar um banco de dados em um servidor menos robusto, enquanto um serviço com mais tráfego necessita de um banco de dados mais poderoso.

Cada serviço conecta-se apenas ao seu próprio banco de dados, garantindo independência e isolamento. Dessa forma, podemos gerenciar melhor escalabilidade e evitar gargalos de desempenho.

- **Problema:** Escalabilidade do serviço e do banco são fortemente relacionados.
- **Solução:** Cada serviço (que necessitar) terá seu próprio banco.

No entanto, em alguns casos, como por exigências contratuais ou necessidades de integração de dados, pode ser necessário adotar o ***Shared Service Database (Banco de Dados de Serviço Compartilho)***.

No cenário de um banco de dados compartilhado, é essencial tratá-lo como se fossem bancos separados em termos de acesso e operação. Mesmo que fisicamente seja o mesmo banco de dados, cada serviço deve interagir com ele de maneira independente, como se fossem bancos distintos. Essa prática, por sua vez, simplifica a manutenção e evolução do sistema, reduzindo o impacto de alterações nos contratos ou na estrutura dos dados.

- **Problema:** Ás vezes precisamos centralizar os dados (até por motivos contratuais).
- **Solução:** Trate esse banco em cada serviços como se ele fosse separado.

De maneira resumida, o princípio é sempre buscar seguir o padrão ***Single Service Database***, garantindo que cada serviço tenha seu próprio banco de dados dedicado. Nos casos de compartilhamento do banco, é fundamental adotar práticas que preservem a independência dos serviços, tratando o banco compartilhado como se fossem bancos separados.


### Padrões de codificação

Quando implementamos um microsserviço, é importante se atentar a alguns padrões de código que podem ser adotados em sua codificação. A seguir, vamos abordar brevemente alguns deles.


#### CQRS - Command Query Responsibilty Segragation

Esse padrão de codificação consiste, basicamente,  na segregação da responsabilidade entre um comando e uma busca. Uma dessas definições pode ser traduzida como:

No seu coração, no seu núcleo é a noção de que podemos utilizar modelos diferentes para buscar uma informação e para atualizar ou inserir uma informação.

Ou seja, temos modelos diferentes para escrever e para ler. Modelos de escrita, e modelos de leitura. Em algumas situações essa separação pode ser muito valiosa, podemos inclusive ter uma banco de dados de escrita e outro de leitura e, ainda, ter algum tipo de sincronização entre ambos.

A ideia por trás do CQRS é reconhecer que as operações de leitura e escrita têm diferentes necessidades e podem evoluir de forma independente. Portanto, ao separá-las, você pode otimizar cada uma delas para melhorar desempenho e manutenção.

Neste padrão, os comandos são responsáveis por alterar o estado do sistema, enquanto as consultas são responsáveis por recuperar dados do sistema. Isso permite que você modele e otimize cada lado de acordo com suas necessidades específicas. 

Além disso, o CQRS frequentemente é combinado com o padrão de Event Sourcing, onde o estado do sistema é determinado por uma sequência de eventos que representam todas as alterações que ocorreram no sistema ao longo do tempo.

Em resumo, o CQRS é uma abordagem que reconhece e abraça a diversidade de requisitos entre operações de leitura e escrita, facilitando a criação de sistemas mais flexíveis, escaláveis e de alto desempenho.


#### Eventos Assíncronos

Os eventos são um tema amplo por si só, abrangendo eventos de domínios e, até mesmo, incluindo o conceito de *event sourcing* (fonte de eventos).

O *Event Sourcing*, por sua vez, envolve o armazenamento de todos os dados de nossa aplicação por meio de eventos. Cada evento representa uma modificação nos dados e, caso seja necessário reconstruir nossos dados, podemos utilizar uma lista de eventos para isso.

Para lidar com eventos assíncronos, tecnologias como **filas de mensagens**, como RabbitMQ e ZeroMQ, e **serviços de streaming de dados**, como o Kafka, são frequentemente utilizados. Essas ferramentas permitem a distribuição eficiente de mensagens assíncronas entre os microsserviços, garantindo a escalabilidade e desempenho.

