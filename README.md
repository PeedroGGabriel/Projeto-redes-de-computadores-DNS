# Projeto-redes-de-computadores-DNS
Projeto de implementação da cadeira de redes de computadores, do curso de Ciência da Computação UNIVASF-Salgueiro.

Descrição do conteúdo

SERVIÇO DNS (Domain Name System)

Página 2 - Pontos listados: Definição, Caracteristicas, Problemas, Protocolos relacionados e Implementação.

Página 3 - Definição 

    É uma sigla para sistema de nomes de domínio. Como o nome sugere, é um registro que contém nomes de sites e respectivos endereços IP associados. Essa correlação favorece a transferência de dados entre computadores e permite o acesso à internet. 
    Um entendimento mais simplificado do DNS requer apenas uma olhada na barra de endereços de um navegador. O domínio é o nome do site (rockcontent.com, por exemplo), e o servidor de nomes armazena um conjunto deles.Em suma: DNS nada mais é além do que uma abstração ao nível do usuário, que permite que páginas sejam encontradas na internet. Cada um deles é único para cada site.

Página 4 - Caracteristicas: 

Utiliza os protocolos de transporte UDP e TCP, Porta 53.
      
NIC (sigla para Network Information Center) é uma instituição encarregada de atribuir nomes de domínio na Internet, sejam eles nomes de domínio genéricos ou por país, permitindo que indivíduos ou empresas criem sites na Internet por meio de um ISP, por meio de um DNS.
    
O DNS opera por meio de dois componentes: Clientes DNS, Servidores DNS.
  Clientes DNS: São programas que um usuário executa e que geram solicitações de consulta para resolver nomes. Basicamente, eles pedem o endereço IP que           corresponde a um determinado nome.
  Servidores DNS: São serviços que respondem a consultas feitas por Clientes DNS. Existem dois tipos de servidores de nomes: 
  Servidor Mestre: Também chamado de Primário. Obtém dados de domínio de um arquivo hospedado no mesmo servidor.
  Servidor Escravo: Também chamado de Secundário. Ao iniciar, obtém os dados do domínio através de um Servidor Mestre (ou primário), realizando um processo             chamado de transferência de zona.
  Possui uma estrutura baseada em árvore.
  Os domínios são representados dentro de uma hierarquia de nomes.
  O nó mais alto dessa hierarquia é o Raiz representado por “.”.

Página 5 - Arvore de Hierarquia DNS

Página 6 - Problemas: 

- Time to live (TTL) inadequado
    Toda informação na rede tem uma “data de validade”. 
    Funciona assim: o servidor de cache solicita para o servidor, no modo autoritário, os registros de DNS. Então, o autoritário “explica” para o cache por quanto tempo eles estarão bons — o normal é que seja entre alguns minutos e um dia todo. Esse é o TTL. Suponha, então, que os registros de DNS mudem antes do TTL expirar. Esse gargalo entre os períodos faz com que o servidor de cache envie por um tempo os registros errados para diversos usuários, que terão problemas com DNS.
    Por outro lado, se o TTL for baixo demais, ele poderia sobrecarregar o servidor autoritário com solicitações de registro desnecessárias. A melhor maneira de solucionar, então, é atualizar os registros de DNS. Você pode fazer isso reduzindo o TTL temporariamente. Um bom número é de cinco minutos. Caso queira algo que mantenha os registros por mais tempo, aposte em um dia todo.
    
- Ataque DDOS
    Os ataques DDOS podem afetar qualquer provedor de internet. Trata-se de uma onda repentina de tráfego muito grande que atinge seu site e, consequentemente, causa problemas com DNS por sobrecarregar os servidores. Solucione isso solicitando um novo IP, limpando os logs e garantindo que seus registros novos estejam de acordo com o endereço solicitado.
    
- Latência do DNS
    A latência é, basicamente, o tempo que as solicitações dos servidores levam para serem transmitidas e, então, retornarem. Normalmente, quando as pessoas reclamam que “a internet está lenta hoje”, eles estão se referindo a problemas com latência, e as falhas com DNS podem estar relacionadas a isso. Um dos maiores fatores relacionados à velocidade da rede é simplesmente a distância que os dados precisam “viajar”, mas ainda assim é possível melhorar a latência checando se os seus servidores DNS trabalham com uma estrutura centralizada ou descentralizada.
    O TTL, que falamos acima, também tem um papel importante na melhora da latência. Mantê-lo mais alto permite que os registros DNS sejam mais consistentes e, assim, evita as solicitações desnecessárias de servidores, o que reduz o quanto se precisa do tráfego de dados.

Página 7 - Protocolos: 
    O DNS e alguns outros serviços funcionam em ambos os protocolos. Vamos dar um exemplo do serviço DNS. Dois protocolos são diferentes um do outro. O TCP é um protocolo orientado a conexão e requer que os dados sejam consistentes no destino e o UDP é um protocolo sem conexão e não requer que os dados sejam consistentes ou não precise estabelecer uma conexão com o host para consistência de dados. 
    Os pacotes UDP têm um tamanho menor. Os pacotes UDP não podem ter mais de 512 bytes. Portanto, qualquer aplicativo que precise que os dados sejam transferidos acima de 512 bytes requer TCP. Por exemplo, o DNS usa TCP e UDP por motivos válidos descritos abaixo. As mensagens UDP não são maiores que 512 bytes e são truncadas quando maiores que esse tamanho. 
    O DNS usa TCP para transferência de zona e UDP para nome e consulta normal (principal) ou reversa. O UDP pode ser usado para trocar informações pequenas, enquanto o TCP deve ser usado para trocar informações maiores que 512 bytes. Se um cliente não obtiver uma resposta do DNS, ele deverá retransmitir os dados por TCP após um intervalo de 3 a 5 segundos.
