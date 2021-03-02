---
layout: essay
type: essay
title: "Pharming: quando o 'phishing'​ toma anabolizantes​"
# All dates must be YYYY-MM-DD format!
date: 2018-10-31
labels:
  - Network
  - Learning
  - CyberSec
summary: "Pharming: quando o 'phishing'​ toma anabolizantes​"
---

<img style='height: 100%; width: 100%; object-fit: contain' src="../images/pharming/pharming.jpg">

Pharming é um tipo específico de phishing que envolve a redireção da navegação do usuário para sites falsos, por meio de alterações no serviço de DNS (Domain Name System). Neste caso, quando você tenta acessar um site legítimo, o seu navegador Web é redirecionado, de forma transparente, para uma página falsa. Esta redireção pode ocorrer:

* Por meio do comprometimento do servidor de DNS do provedor que você utiliza;
* Pela ação de códigos maliciosos projetados para alterar o comportamento do serviço de DNS do seu computador;
* Pela ação direta de um invasor, que venha a ter acesso às configurações do serviço de DNS do seu computador ou modem de banda larga.

## Prevenção:

* Desconfie se, ao digitar uma URL, for redirecionado para outro site, o qual tenta realizar alguma ação suspeita, como abrir um arquivo ou tentar instalar um programa;
* Desconfie imediatamente caso o site de comércio eletrônico ou Internet Banking que você está acessando não utilize conexão segura. Sites confiáveis de comércio eletrônico e Internet Banking sempre usam conexões seguras quando dados pessoais e financeiros são solicitados;
* Observe se o certificado apresentado corresponde ao do site verdadeiro.

Existem outros casos de Pharming que não é utilizado envenenamento de DNS, por exemplo, a alteração de certificado do servidor de origem de uma CDN (ex: Akamai), que resulta na interceptação de qualquer informação trafegada, inclusive os dados de autenticação de um portal. O usuário final não vai perceber, pois em essas infraestruturas o certificado é pinado e fica transparente.

## Envenamento de cache DNS (DNS cache poisoning):

É o comprometimento na segurança ou na integridade dos dados em um Sistema de Nomes de Domínios (Domain Name System DNS). Esse problema acontece quando os dados que são introduzidos na cache de um servidor de nomes DNS (ou no próprio computador do usuário) não se originam do servidor de nomes DNS com autoridade real. Tal problema pode ser uma tentativa de ataque malicioso em um servidor de nomes, mas também pode ser o resultado de um erro não intencional de configuração na cache do servidor DNS.

Outros tipos de ataques ao processo de autenticação podem ser utilizados a partir desse segmento. Assim como ocorre com o roubo de credenciais há a possibilidade de manipulação de serviços fraudulentos que visam comprometer a identidade dos usuários.

## Prevenção:

Muitos ataques de envenenamento de cache podem ser evitados em servidores DNS, desde que os mesmos passem a confiar menos nas informações que são passadas para eles por outros servidores DNS, e ignorando qualquer registro DNS que não são relevantes para consulta. 

Por exemplo, as versões do BIND 9.5.0-P1 e acima, realizam esse tipo de checagem. Como dito acima, randomização da porta fonte para consultas DNS, combinado com o uso de criptografia segura para selecionar ambos, a porta fonte e o nonce 16-bit, pode reduzir bastante a probabilidade de que esses ataques sejam bem sucedidos. 

Contudo roteadores, firewalls, proxies, e outros dispositivos gateways que realizam tradução de endereços de rede (NAT), ou mais especificamente, tradução de endereço de portas (PAT), frequentemente reescrevem as portas fontes em ordem, a fim de acompanhar o estado da conexão. Quando modificam a porta de origem, os dispositivos PAT removem a aleatoriedade da porta de origem implementada por servidores de nome. 

Este tipo de ataque pode também ser mitigado na camada de transporte ou na camada de aplicação por realizar uma validação fim a fim, uma vez que uma conexão é estabelecida. Um exemplo comum disso é o uso da Transport Layer Security e das assinaturas digitais. Por exemplo, ao usar uma versão segura de HTTP, HTTPS, os usuários podem checar se o certificado digital do servidor é válido e pertence ao proprietário esperado do site. 

Da mesma forma, a segurança do Shell de programas de login remoto checam o certificado digital nos terminais (se conhecido) antes de proceder com a sessão. Para aplicações que baixam atualizações automaticamente, a aplicação pode incorporar um cópia do certificado assinado localmente e validar a assinatura armazenada na atualização do software.

Secure DNS (DNSSEC) usa criptografia de assinaturas eletrônicas assinadas com um certificado de chave públicas confiável para determinar a autenticidade dos dados. DNSSEC pode conter ataques de envenenamento de cache, porém a partir de 2008 ainda não era amplamente implantado. Em 2010 o DNSSEC foi implementado nos servidores root zone da Internet.

## Referências:

http://ieeexplore.ieee.org/abstract/document/6118551/ (Prevent DNS Cache Poisoning Using Security Proxy)

https://pt.wikipedia.org/wiki/DNS_cache_poisoning

Lux in Tenebris:. Saudações. 93!

<a href="https://www.linkedin.com/pulse/pharming-quando-o-phishing-toma-anabolizantes-mario-neis/" target="_blank">Postagem inicial no meu perfil do LinkeDin</a>

Cartilha do Cert diponivel em https://cartilha.cert.br/golpes/
