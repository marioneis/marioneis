---
layout: essay
type: essay
title: 'Booters. Ou quando uma "bazuca"​ se torna "user friendly"'
# All dates must be YYYY-MM-DD format!
date: 2018-10-15
labels:
  - Network
  - Learning
  - CyberSec
summary: 'Booters. Ou quando uma "bazuca"​ se torna "user friendly"'
---

<img style='height: 100%; width: 100%; object-fit: contain' src="../images/booter/booter.jpg">

## DEFINIÇÃO DE UM BOOTER / STRESSER

Um Booter (também conhecido por Stresser) é um serviço web que efetua DDoS (Distributed Denial of Service) como um serviço para clientes sem conhecimento técnico com preços bastante baixos e de difícil detecção.

## CRITÉRIOS DE INVESTIGAÇÃO

A mitigação e os devidos processos legais contra o ecossistema dos Booters ( sites, proprietários, clientes e infraestruturas) tem em sua maioria, Booters que tenham lançados ataques que tenham causado dano à grandes organizações. Entretanto, há centenas de outros booters que ficam “abaixo desse radar” ( como revelado pela iniciativa da “booter blacklist”) e que raramente sofrem algum tipo de ação para mitigar seus feitos.

Evidentemente, com essa quantidade de booters disponíveis aos clientes ( e esse número só faz crescer), torna-se improvável a mitigação de todos, sendo necessária uma listagem de prioridades e de mecanismos que coloquem critérios na ordenação desta listagem. O que devem ser mitigados com prioridade são os que conseguem fazer os ataques mais poderosos, mas identificar esses Booters é uma tarefa muito restrita à companhias de segurança de redes de grande porte, que possuem a ‘expertise’ para classificar os ataques mais perigosos em seus clientes. Para classificar os booters do outro grupo ( que não são vistos pelas grandes corporações) foi descrita uma heurística que prioriza um grupo de booters baseados em três premissas.

O serviço de booters normalmente não são éticos ou legais: é debatível quando um ataque de stress de um Booter pode ser considerado legítimo ( atacando o próprio ip do cliente para testar sua capacidade de carga, por exemplo), entretanto, a infraestrutura utilizada pelos booters inclui botnets ou outras infras comprometidas com grande frequência;

A relação entre o número de acessos ao site do Booter e o número de ataques efetuados, são similares em todos booters: essa premissa nos leva a concluir que o booter mais acessado irá efetuar mais ataques;

A força de ataque propagandeada pode ser factual: foi observado que, de modo geral, Booters entregam bem menos que anunciam e prometem aos clientes, contudo, há Booters que atraíram atenção da mídia por terem efetuado ataques bem mais poderosos e efetivos que fora anunciado eu seus sites. A rede do xBox (LIVE) e do Playstation (PSN) foram atacadas durante o natal de 2013 com uma carga de 300 Gb/s pelo Booter ‘Lizard Stresser’, enquanto o site dele anunciava ataques com carga de 125 Gb/s. Para corroborar com essa premissa, foi argumentado que é bem simples e fácil de encontrar amplificadores para ataques de reflexão e comprometer um grande número de sistemas ( IoT como exemplo, no caso do Mirai, que utilizou senhas e usuários padrão de vários devices e conseguiu criar uma botnet de tamanho considerável), desse modo, um grupo de hackers que seja habilidoso e donos de Booters, conseguem facilmente escalar o poder de ataque de uma infraestrutura.


## O ECOSSISTEMA DE UM BOOTER

Todos elementos envolvidos nas atividades de um Booter compõem seu ecossistema.

Os serviços de Booter têm um frontend web onde o cliente, após o devido pagamento (normalmente efetuado via bitcoins ou carteiras virtuais, de modo a dificultar o rastreio do dinheiro), escolhe o site ou IP para atacar ( observe que o cliente não contrata a indisponibilidade de um endereço IP 'per si', ele contrata tempo de processamento de um Booter (normalmente indicada pelo site em ms(milisegundos) e a quantidade de tráfego esperada no endereço alvo.

Basicamente um painel de controle de usabilidade simplificada, onde estão presentes os hosts, na grande maioria servidores dedicados com ligações superiores a 1 Gbps, que executam o ataque, que por sua vez estão localizados noutro local, Não existe qualquer tráfego DDoS feito diretamente pelo ISP do site.

Todo o tráfego do ataque DDoS vem de uma infraestrutura separada que inclui muitos servidores espalhados (e computadores pessoais infectados) pela Internet, em que o Booter se conecta via proxies. Ou seja, temos uma aplicação web que se conecta a API preparada para lançar ataques de negação de serviço distribuído.

Os Booters por vezes são suportados por botnets (conjunto de máquinas infectadas (bots) que recebem instruções do seu operador para ataques remotos) de grandes dimensões, mas estes são muito difíceis de encontrar e de alugar.

## PROPOSTAS PARA MITIGAÇÃO DE BOOTERS

Quatro tipos de organizações devem ser analisadas em conjunto para entendermos como seria possível ocorrer um esforço organizado para mitigar os Booters, sejam elas: operadoras TLDs ( Top Level Domain), registradores de domínios, indexadores de sites, provedores de segurança baseados na nuvem e resolvedores DNS locais.

Eles devem ser analisados, basicamente, por dois motivos, primeiro eles estão ligados aos Booters principalmente pelos seus Domínios e em segundo lugar porque algumas destas companhias oferecem mais de um serviço, como por exemplo a ‘Cloudflare’ que é tanto um servidor web para sites como um provedor de segurança na nuvem ( praticamente todos os Booters se ‘escondem’ atrás dessa proteção na nuvem, em função dos ataques “da concorrência”), a GoDaddy que é uma das maiores empresas de registro de domínio e de serviços de hospedagem do mundo e a SIDN que tanto uma operadora TLD e uma registradora de domínios.

Uma lista de palavras chave, como “stresser”, “booter”, “ddos” etc, constantes nas composições dos nomes de domínio, pode ser utilizada pelas TLDs e pelos registradores de domínios para, por exemplo, retirar de operação domínios existentes ou para prevenir novos registros suspeitos. Poderia haver uma ferramenta que classificasse como suspeito domínios que utilizem termos essa lista de palavras e os submetessem ao escrutínio futuro para habilitação.

Booters por trás de sistemas de segurança na nuvem ( como o cloudflare) requerem investigações mais refinadas para determinar onde o site está de fato hospedado. Existe a iniciativa “CloudPiercer” que aplica várias métricas para tentar determinar o real endereço ip de um Booter protegido/hospedado pela cloudflare.

Os sistemas de pagamento são elementos basilares do ecossistema dos Booters, já existe um esforço conjunto das listas de booters disponibilizadas para a PayPal, onde contas alegadamente pertencentes a donos de Booter são desativadas mas, apesar do sucesso nessa cadeia, ela é momentânea, porque os Booters acabam migrando para outras formas de pagamento, principalmente as cripto-moedas, de toda forma essa atitude, encolheu drasticamente o número final de Booters disponíveis, pois poucos possuíam carteiras de BitCoins no momento das suspensões.

É extremamente fácil encontrar sites de Booters através de pesquisas públicas nos motores de busca disponíveis, uma forma de mitigar isso seria o motor de busca sinalizar o usuário que interagir com o site em questão (mesmo que seja somente acessar) pode trazer implicações legais, no formato que já ocorre com os sites sinalizados como inseguros pelo browser ‘Google Chrome’, pela paridade entre acessos e ataques, podemos presumir que, diminuindo o acesso, diminuirá o número final de ataques.

Uma forma muito prática de prevenir que usuários/clientes acessem Booters é criando uma lista negra de sites Booters nos resolvedores de domínios, quando um site é requisitado ao resolvedor de nomes, e este está numa lista, ele é recusado e o usuário não consegue chegar ao IP destino.

É importante frisar, entretanto, que todas as formas de mitigação de Booters sugeridas acima, dependem de autorizações judiciais/legais. CloudFlare, por exemplo, afirmou que “é perigoso quando organizações privadas tendem a agir como polícia”.

## OBRA ANALISADA

J.J. Santanna, R.d.O. Schmidt, D.Tuncer, A.Sperotto, L.Z.Granville and A. Pras, "Quiet Dogs Can Bite: Which Booters Should We Go After, and What Are Our Mitigation Options?" in IEEE Communications Magazine, vol. 55, no. 7, pp. 50-56, 2017. doi: 10.1109/MCOM.2017.1600992

## BIBLIOGRAFIA COMPLEMENTAR

https://blog.radware.com/security/2017/09/growth-of-ddos-as-a-service-stresser-services/

https://www.incapsula.com/ddos/booters-stressers-ddosers.html

https://pt.slideshare.net/jjcsantanna/civil-disobedience-ddos-attacks-booters-and-beyond

Exploring the Cybercrime Underground: Part 2 – The Forum Ecosystem

http://www.websegura.net/tag/stresser/

http://booterblacklist.com/
