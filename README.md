O que eu aprendi até o momento
===
>Autor: Fábily Ideale

Começarei com o tema de redes
---
Quero exemplificar o que de fato ocorre quando acessamos uma página da Web. Claro que não consigo citar tudo que de fato ocorre em detalhes porque temos muito material sobre "Redes de Computadores" - Mesmo computação sendo uma ciência nova e ainda em desoberta.

À começar, vamos exemplificar o **DNS**:
![Exemplo visual do funcionamento do protocolo de DNS](/imagem/dns.png)
Tudo começa quando digitamos um endereço (URL) no navegador, no nosso exemplo utilizamos o site "example.com" - Que inclusive existe - para um melhor entedimento.  
Ao digitar "example.com" o navegador "pede" ao OS para fazer uma requisição DNS ao roteador através do protocolo UDP e então inicia-se o processo de resolução de DNS.  
O roteador (desde que esteja utilizando a tecnologia) "assume" a requisição através do NAT e olha para a URL digitada. No nosso caso, ele a "divide" em 3 partes separadas, "." (root), "com" e "example". Inicia-se um processo iterativo em que o DNS resolver (seja ele do ISP ou algum interno) "pergunta" aos servidores DNS até encontrar o endereço final - Isso ocorre nessa ordem respectivamente: Root DNS, ccTLD DNS (não se aplica à nossa URL), TLD e Servidor autoritativo.

Então o que ocorre depois?! Aí entra o servidor que oferece o serviço diretamente ou, conforme ilustramos abaixo, um sistema **CDN com PoPs** espalhados por uma área geográfica.
![Exemplo visual do funcionamento do sistema/modelo de CDNs](/imagem/cdn.png)
Após o DNS Resolver ter encontrado seu destino (que no nosso exemplo é um redirecionamento para uma rede CDN), nós somos redirecionados para o PoP mais próximo (ou o mais adequado) baseado em nossa localização.  
Obs.: São usados algoritmos complexos que juntos levam à criação de informação do melhor PoP baseado em nosso IP de acesso e alguns metadados - Entre eles, o BGP é o padrão do mercado.  
Porém ao requisitarmos ao PoP a página, ele observa em seu cache interno e percebe que não possui a página e inicia outra conexão P2P até ao servidor original. Essa conexão é mais otimizada do que se fôssemos fazê-la, pois já estão definidas "rotas ótimas" do PoP (da CDN) até o servidor original.  
Após obter a página e armazená-la (baseado em seu TTL), nós recebemos o que requisitamos em nossas máquinas, porém, vale ressaltar que um servidor DNS não armazena o serviço por completo - Afinal de contas ele não conseguiria processar os serviços de tudo que ele possui em cache - e sim o conteúdo estático.

Agora temos uma conexão estabelecida com o servidor (mais à frente detalharemos o processo de conexão inicial). Chegamos ao passo da **Internet!**
![Exemplo visual do funcionamento da internet sob uma conexão estabelecida](/imagem/internet.png)
Aqui temos um exemplo de conexão estabelecida que ao sinal do computador cliente, a requisição feita vai até o PoP e este serve algum serviço que esteja em seu "alcance" ou repassa à requisição ao servidor original se for um serviço que necessita de tal.

---
- Chegamos ao final da parte de redes, mas antes quero apenas citar vários termos que aprendi até aqui. Não consegui explica-los aqui por "motivos da vida", mas saibam que **internet é um tema muito complexo e recheado** que está crescendo a cada década! Segue lista de termos:
    - NAT/PAT: Software que "assume" requisições em uma rede local;
    - Modelo OSI: Modelo teórico que surgiu para estabelecer a internet, mas não chegou a ser utilizado na prática. Serve de "guia" para muitas aplicações/modelos/arquiteturas atualmente - Possui 7 camadas;
    - TCP/IP: Modelo implementado na prática para o início da internet, tem em sua fundação a base do OSI - Possui 4 camadas (mais recentemente têm surgido estudos que apontam 5 camadas);
    - RIP: Algoritmo de roteamento baseado em saltos (hop);
    - OSPF: Algoritmo de roteamento que usa latência e "contratos políticos" para a melhor performance;
    - BGP: Algoritmo de roteamento que usa vários parâmetros e oo conceito de "zonas" para otimizar o tráfego em massa - Padrão de grandes empresas;
    - IPv4: Sequência de 4 octetos que representa a identificação de um dispositivo em rede;
    - IPv6: Versão do IP com 8 hextetos e identifica dispositivos - Em estado de implementação, mas pretende ser o futuro da internet;
    - Máscara de rede/CIDR: Identifica qual parte de um IP representa a rede e qual representa o host;
    - Firewall: Software que analisa o tráfego que "passa" por ele. Exxistem os *stateless*, *stateful*, WAF e NGFW - Sendo mais eficientes nessa respectiva ordem, mas também aumentado o poder de processamento necessário nessa mesma ordem;
    - Proxy: Intermediador entre 2 pontos, pode ser do "lado" do usuário ou dos servidores (proxy reverso);
    - VPN: Criptografa a comunicação entre 2 dispositivos (Acesso remoto) ou duas redes (site-a-site) por completo, desde a mensagem até o "transporte" - *Tunneling*;
    - Hash: Modo de proteger/verificar algo através de uma "transformação" irreversível de uma informação para um dado - MD5, SHA-1 e SHA-256;
    - DDoS: Ataque em que várias requisições simultâneas são feitas à um servidor de serviços.  
    ...

---
Primeiro quero exemplificar o que de fato ocorre quando acessamos uma página da Web.
![Exemplo visual do funcionamento do protocolo de DNS](/imagem/git.png)