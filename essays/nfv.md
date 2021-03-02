---
layout: essay
type: essay
title: 'Breves comentários e análise sobre o artigo "NFV: Security Threats and Best Practices"​' 
# All dates must be YYYY-MM-DD format!
date: 2018-10-23
labels:
  - Network
  - Learning
  - CyberSec
summary: 'Breves comentários e análise sobre o artigo "NFV: Security Threats and Best Practices"​' 
---



<h3>OBRA ANALISADA</h3>

S. Lal, T. Taleb and A. Dutta, " NFV: Security Threats and Best Practices " in IEEE Communications
Magazine, vol. 55, no. 8, pp. 211- 217, 2017.

<h3>IDÉIAS CENTRAIS DA OBRA</h3>

A virtualização de funções de rede ( NFV, em inglês) provê numerosos benefícios, principalmente no
tocante às travas impostas pelos fornecedores de hardware de telecom, contudo, esse bônus, carrega o custo
de seu ônus na forma de falhas de segurança. As redes móveis virtualizadas, no paradigma do NFV, se tornam
vulneráveis a muitas ameaças. 
<p>Porém elas podem ser mitigadas com o auxílio de algumas técnicas e com o uso
de outras soluções que derivam dessas novas tecnologias de infraestrutura. Este resumo apresentará as
ameaças mais críticas que poderão surgir numa infraestrutura NFV e proporá as melhores práticas de
segurança para mitigar e proteger-se contra elas.</p>

<h3>PROBLEMAS PROVENIENTES DA IMPLANTAÇÃO NFV </h3>

Quando um atacante consegue acessar o hipervisor por comprometer algum das funções de rede
rodando em uma virtualização, temos uma falha de isolamento. Este ataque é possível quando há falhas no
isolamento entre o hipervisor e a virtualização, usando algumas ferramentas o atacante consegue ganhar
acesso à API de gerência do hipervisor e à ‘nuvem’ da rede de gerenciamento. Em um caso prático uma
aplicação rodando em NFV poderia enviar pacotes forjados com o propósito de explorar um estouro de buffer
(heap overflow), e deste processo virtualizado comprometido, ganhar acesso ao host.
<p>A facilidade de se criar serviços virtualizados de forma dinâmica podem resultar em erro humano,
quando um router é criado e usado para interconectar redes virtuais sem o uso de quaisquer firewalls, pode
ocorrer chamada falha na implementação e validação da topologia da rede. Com o conhecimento da topologia,
um atacante poderia transferir funções virtualizadas para locais de segurança reduzida.
Em uma estrutura formal de telecom não é possível forçar a existência desta fora de certas marcas
legais, contudo, usando NFV a violação de marcos regulatórios locais se torna possível pois é factível a troca de uma NFV de um local onde a legislação é favorável para outro onde não é. A consequência dessas violações
podem vir na forma do completo banimento do serviço ou na execução de alguma penalidade financeira grave.
Outra possibilidade é o ataque mirar na violação da privacidade do conteúdo de um banco de dados.
Negações de serviço podem ser direcionadas para as interfaces de redes virtualizadas de modo a exaurir seus
recursos e impactar na disponibilidade do serviço.</p>
<p>Uma NFV comprometida pode gerar grandes quantidades de LOG no hipervisor, causando ou a dificuldade de
leitura dos registros, ou em pior cenário, a exclusão de dados importantes de log devido a rotatividade de tempo
( logs mais antigos sendo excluídos quando gerados mais recentes).
Um grande risco que sempre existirá em qualquer infraestrutura será o atacante interno, quando um
administrador pode agir de forma negligente ou até mesmo maliciosa, como o administrador tem acesso raíz às
virtualizações, ele pode gerar dumps e deles extrair informações sensíveis.</p>

<h3>MELHORES PRÁTICAS PARA MITIGAR OS POSSÍVEIS PROBLEMAS</h3>

Usando uma plataforma modular confiável como a raíz do processo de confiança, componentes
sensíveis como firmware, BIOS, bootloaders, OS Kernel e outros, podem ser armazenados e verificados de
forma segura. A segurança se dá porque não é possível modificar tal plataforma em tempo de execução, e a
validação desta pode ser feita através de um servidor remoto ou de uma política de controle.
<p>O hipervisor habilita virtualização de funções entre camadas de hardware e máquinas virtuais. Com
essa centralização se torna mais fácil gerenciar a questão de atualizações e patches de segurança da
infraestrutura, outra prática que é facilitada pela centralização criada pelo hipervisor é desabilitar todos serviços que não estejam em uso, por exemplo SSH e acesso remoto não são necessários todo o tempo, portanto não
precisam estar disponíveis todo o tempo.</p>
<p>Uma boa prática a ser seguida é a separação do tráfego real do tráfego gerencial das virtualizações,
isso irá prevenir ataques vindos de um tráfego e direcionados ao outro. Também é boa prática separar as
VLANs em grupos e desabilitar o que não está em uso. As funcionalidades virtualizadas com similaridades
podem ser agrupadas em chamadas “zonas seguras”, onde o tráfego possa ser isolado e controlado por
firewalls de forma mais simplificada e assertiva.</p>
<p>O Kernel do sistema do ‘Host’ é um componente importantíssimo que provê isolamento entre
aplicações. A virtualização segura (sVirt) é uma nova forma de integrar novos hipervisores baseados em Linux.
O ‘sVirt’ promove o isolamento entre processos virtualizados e seus arquivos de dados, um exemplo bem prático
disso é o ‘hidepd’ que pode ser usado para prevenir usuários não autorizados de enxergarem processos
vinculados a outros usuários.</p>
<p>O hipervisor pode se comportar de forma ‘introspectiva’ para fazer o escrutínio das aplicações sendo
executadas dentro de virtualizações, de modo a verificar anomalias em suas atividades. Utilizando essa
habilidade, o hipervisor pode monitorar as atividades do tráfego de rede, os acessos aos arquivos em storages e
ler a memória em execução. É uma ferramenta poderosa que pode executar varreduras profundas em
virtualizações em execução.</p>
<p>Os discos virtuais que contém as virtualizações das VNFs podem conter dados extremamente
sensíveis, de modo que precisam ser protegidos. A melhor forma de proteger dados armazenados é utilizando
chaves criptográficas em locais seguros. o TPM pode ser usado para armazenar tais chaves e o hipervisor pode
ser configurado para ‘limpar’ os discos virtuais se certas condições de eventos acontecerem, segmentos de
memória podem ser movidos para o disco como uma memória secundária, caso haja quebra de segurança nos
módulos de memória alocados à virtualização.</p>
<p>Pela facilidade de se conseguir alterar uma imagem de virtualização ( afinal, trata-se de um sistema
operacional embarcado) enquanto ela é colocada no ar em um hipervisor ( seja através de um banco de dados
de imagens, seja através de um nodo computacional) deve-se sempre procurar formas de ‘assinar’ a imagem,
para que ela seja verificada após o deploy na virtualização e se consiga verificar a assinatura durante o boot damesma. Isso é possível com a ajuda de autoridades certificadoras e modificações no hipervisor para que haja
essa checagem antes do ‘boot’ de tal virtualização.</p>
<p>Uma ótima prática consiste no gerenciamento da segurança de forma orquestrada, que incorpore tanto
a segurança quanto os requisitos de confiabilidade desse novo modelo de infraestrutura. Essa ferramenta se
torna muito útil pois consegue configurar limites escalares na plataforma e no descritor de serviços da rede, de
modo que as restrições geradas protejam contra ataques, como uma amplificação de DNS, por exemplo.
Seguindo o conceito do TPM mencionado anteriormente, a confirmação de veracidade de forma remota
é uma técnica que verifica o status da plataforma NFV, ela pode ser usada tanto pelo dono da plataforma quanto
pelo cliente que queira confirmar que a plataforma foi inicializada de uma forma confiável.</p>

<h3>PROPOSTAS DE NOVOS MECANISMOS PARA SEGURANÇA</h3>

<p>Ainda há um longo caminho adiante, se bem adotada, uma rede controlada por software de fato pode
trazer redução de custos, mas a necessidade de integrar com equipes de TI e rede também aumenta muito,
existem ainda dificuldades como padronização de equipamentos entre múltiplos fornecedores, interoperabilidade
e protocolos abertos como aspectos essenciais (e ainda não plenamente atendidos) para que as redes definidas
por software e os serviços virtualizados se tornem uma realidade.</p>
<p>Nesse aspecto de interoperabilidade a Fundação Linux, organização sem fins lucrativos dedicada ao
Linux e ao desenvolvimento colaborativo, anunciou no fim de 2014, a criação do projeto Open Platform for NFV
(OPNFV - Plataforma Aberta para Network Functions Virtualization).</p> 
Ela será uma plataforma de código aberta altamente confiável e integrada, e terá o objetivo de acelerar a adoção de novos produtos e serviços na área, empresas como Ericsson, Juniper entre outras também se juntaram à essa ideia de interoperabilidade, essa plataforma aberta poderá gerar novas formas de hipervisores que consigam centralizar muitas soluções virtualizadas e que escalem.

<h3>BIBLIOGRAFIA COMPLEMENTAR</h3>
https://www.ericsson.com/res/region_RLAM/press-release/2016/2016-11-24-nfv-po.pdf 
<br/>http://www.junipernetworks.com.br/os-caminhos-para-o-sdn-e-nfv 
<br/>https://wiki.opnfv.org/ 

<a href="https://www.linkedin.com/pulse/breves-coment%C3%A1rios-sobre-o-artigo-nfv-security-threats-mario-neis/" target="_blank">Postagem inicial no meu perfil do LinkeDin</a>