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

- Chegamos ao final da parte de redes, mas antes quero apenas citar vários termos que aprendi até aqui. Não consegui explica-los aqui por "motivos da vida", mas saibam que **internet é um tema muito complexo e recheado** que está crescendo a cada década! Segue lista de termos:
    - NAT/PAT: Software que

---
Primeiro quero exemplificar o que de fato ocorre quando acessamos uma página da Web.
![Exemplo visual do funcionamento do protocolo de DNS](/imagem/git.png)