
O termo Onion Architecture, traduzido como arquitetura cebola, foi criado por Jeffrey Palermo com intuito de reduzir o forte acoplamento e separar os interesses da maioria da maioria das arquiteturas tradicionais, fornecendo um modelo confortável de construir aplicativos em perspectiva de testabilidade, manutenção e confiabilidade.

De acordo com a arquitetura tradicional, a camada de interface do usuário deve interagir com a lógica de negócios, que por sua vez conversa com a camada de dados, tendo todas as camadas misturadas e muito dependentes umas das outras. Sendo assim, nenhuma delas é independente, tornando muito difícil entender e manter sistemas com essa arquitetura, justamente por esse fluxo gerar um *acoplamento desnecessário*.

A Onion Architecture resolveu esse problema ao definir camadas que vão do núcleo à estrutura, tal qual uma cebola de fato, baseando-se no princípio de inversão de controle. Vamos analisar o seguinte exemplo que ilustra essa relação de camadas e suas comunicações:

![[Pasted image 20240322095458.png]]

No exemplo acima, podemos observar que:

- A camada de *Infraestrutura* conhece a camada de *Aplicação* e a de *Domínio*
- A camada de *Aplicação*, por sua vez, conhece a camada de *Domínio*, mas não a de *Infraestrutura*
- A camada de *Domínio*, por fim, conhece apenas a ele próprio, se tornando o núcleo da arquitetura.

Com essa análise, podemos pontuar como esse tipo de arquitetura incentiva o desenvolvimento orientado a domínio (DDD), visto que o negócio (nesse caso, o domínio) é o centro de tudo. Vale ressaltar, também, que a quantidade de camadas não possui uma regra exata, no entanto, *quanto mais perto do centro, mais estável o código*.

## Agora, como essas camadas se relacionam?

As camadas da arquitetura de cebola interagem entre si através do uso de *interfaces*. Para isso, cada camada envolve a outra de *fora para dentro*, sempre nesse mesmo sentido, interagindo entre si em direção ao núcleo (representação do domínio).

Durante o caminho da camada mais externa a mais interna, o input em uma camada é transformado para um input na camada seguinte, e assim sucessivamente, até chegar no centro. A partir disso, um output é processado e encaminhado de volta até sair do sistema pela camada mais externa.

Como trabalhamos com diferentes camadas, cada uma delas tem sua relevância e características. Algumas delas são:

##### Infraestructure Layer - (Adapters)

Camada mais externa da aplicação. Ela é quem interage com os limites de entrada e saído do sistema e é responsável por permitir o sistema de acessar recursos do *mundo externo*, como *banco de dados*, *web services*, *arquivos*, entre outros.

Nessa camada são encontrados objetos ORM, interfaces de persistência, factoies responsáveis por converter o modelo do banco para domínio, entre outros.

##### Application Services Layer

Também chamada de *camada de serviço*, ela é responsável por orquestrar o que chega da camada mais externa à ela (*Infraestructure Layer*).

É importante ressaltar ainda que, diferente da arquitetura tradicional, ela *não possui regra de negócio* e sua finalidade consistem em facilitar o acesso a algo, sendo nesse caso o domínio.

A camada de serviço é responsável por representar um *caso de uso*, que tem por objetivo o controle de transação de negócio. Além disso, também representa controllers, e objetos de InputModel/ViewModel.

##### Domain Services Layer

Essa camada define *eventos* específicos de *domínio*. Esses são eventos como concluir pedidos, enviar pedidos, devolver pedidos, e assim por diante. Podemos definir essas ações como *regra de negócio* que não se encaixa em uma *entidade*.

Como exemplo, podemos pensar que persistir uma entidade envolve acessar um componente externo, isso está além da responsabilidade de uma entidade, justamente por isso seu caminho final é na domain service.

##### Domain Model Layer

Consiste na parte central da arquitetura, e define o estado e os comportamentos das entidades. Assim, a lógica consiste em ter todos objetos de domínio nesse núcleo sem dependências externas, ou seja, essa camada deve depender apenas de si mesma. 

Dessa forma, deve ser possível determinar a finalidade da aplicação apenas ao observar as classes dessa camada.

## Benefícios do uso de Onion Architecture

- Essa arquitetura fornece melhor manutenção, visto que as camadas possuem baixo nível de acoplamento.
- Melhoria na testabilidade, já que o teste de unidade pode ser criado para camadas separadas sem o efeito de outros módulos do aplicativo
- Desenvolve um aplicativo fracamente acoplado, visto que a camada externa sempre se comunica com a interna por meio de interfaces, nunca dependendo da camada externa.
- Todas as dependências externas, como o acesso ao banco de dados, são representadas em camadas externas.
- As implantações são fornecidas durante o tempo de execução, levando em consideração que as camadas são conectadas por meio de interfaces.

