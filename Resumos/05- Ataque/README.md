# **Ataques à Segurança da Informação**

Um **ataque** é definido como qualquer ação que comprometa a segurança das informações de uma organização. Eles ocorrem quando uma fonte de ameaça explora uma vulnerabilidade para causar impacto a um ativo (dados, sistemas ou pessoas).

Os ataques são classificados em duas grandes categorias, dependendo da forma como interagem com o sistema e a informação:

---

## **1. Ataques Passivos**

Os ataques passivos têm como objetivo a **interceptação** e a leitura de informações. O atacante não altera os dados nem interfere no funcionamento do sistema; o foco é a quebra da **confidencialidade**. Por serem furtivos, são extremamente difíceis de detetar, pois não deixam rastros óbvios.

### **Tipos de Ataques Passivos**

* **Sniffing (Interceptação de Tráfego):**
    * **Como ocorre:** O atacante utiliza um software ou hardware (*sniffer*) para monitorizar e capturar pacotes de dados que viajam pela rede. Se os dados não estiverem cifrados, o atacante pode ler logins, senhas e mensagens.
* **Spyware (Monitorização Furtiva):**
    * **Como ocorre:** Software malicioso instalado sem o conhecimento do utilizador para recolher dados.
    * **Keylogger:** Regista todas as teclas premidas no teclado.
    * **Screenlogger:** Captura imagens da tela do computador periodicamente.
* **Ataque de Ombro (Shoulder Surfing):**
    * **Como ocorre:** Observação direta de um utilizador enquanto este insere credenciais ou informações confidenciais em locais públicos.
* **Dumpster Diving (Mergulho no Lixo):**
    * **Como ocorre:** Recuperação de informações sensíveis através de documentos ou mídias físicas descartadas incorretamente no lixo.

### **Como se defender**
* **Criptografia:** Utilizar protocolos cifrados (como HTTPS, TLS, VPN) para que os dados capturados sejam ilegíveis.
* **Antimalware:** Manter ferramentas de proteção atualizadas para identificar e remover programas espiões.
* **Políticas de Descarte Seguro:** Utilizar fragmentadoras de papel e destruição física de dispositivos de armazenamento antigos.

---

## **2. Ataques Ativos**

Os ataques ativos envolvem a **modificação** de fluxos de dados ou a criação de informações falsas. Eles visam comprometer a **integridade**, a **disponibilidade** e a **autenticidade** dos sistemas.

### **Tipos de Ataques Ativos**

#### **A. Injeção e Manipulação de Dados**
* **Injection (Injeção de Código):**
    * **O que é:** Ocorre quando um atacante envia dados não confiáveis para um interpretador como parte de um comando ou consulta. A aplicação falha ao não validar a entrada, permitindo que o atacante "force" o sistema a executar instruções maliciosas.
    * **Exemplos de Injection:**
        * **SQL Injection (SQLi):** Inserção de comandos SQL em formulários para manipular ou extrair dados da base de dados.
        * **Cross-Site Scripting (XSS):** Injeção de scripts (Javascript) em páginas web que são executados no navegador da vítima para roubar sessões.
        * **Command Injection:** Injeção de comandos do sistema operativo através de campos de entrada da aplicação.
* **Buffer Overflow (Estouro de Buffer):**
    * **Como ocorre:** Envio de um volume de dados maior do que a memória (buffer) de uma aplicação consegue suportar. O excesso transborda para áreas adjacentes, permitindo ao atacante injetar e executar código malicioso ou causar o bloqueio do sistema.
* **Cross-Site Scripting (XSS):**
    * **Como ocorre:** Injeção de scripts maliciosos (Javascript) em páginas web legítimas, que são executados no navegador da vítima para roubar sessões de acesso.

#### **B. Falsificação (Spoofing) e Armadilhas**
* **Spoofing (Falsificação):**
    * **IP Spoofing:** O atacante mascara o endereço IP de origem para parecer que o tráfego vem de uma fonte confiável.
    * **E-mail Spoofing:** Alteração do cabeçalho de um e-mail para que o remetente pareça ser alguém conhecido.
    * **DNS Spoofing:** Envenenamento do cache do DNS para redirecionar utilizadores de sites legítimos para sites falsos.
* **Phishing:**
    * **Como ocorre:** Envio de mensagens (e-mail, SMS) que simulam entidades reais para enganar o utilizador e obter senhas ou dados bancários.
* **Cross-Site Request Forgery (CSRF):** ataque cibernético que engana o navegador de um usuário autenticado para realizar ações indesejadas em outro site, como alterar senhas ou transferir fundos. O invasor aproveita a sessão ativa do usuário, tornando a ação fraudulenta legítima para o servidor.
	* **Prevenção**: A forma mais eficaz é incluir um token único e aleatório em cada solicitação de formulário, que o servidor verifica.
	
#### **C. Negação de Serviço e Extorsão**
* **DoS e DDoS (Negação de Serviço):**
    * **Como ocorre:** Sobrecarga de um servidor com tráfego massivo para torná-lo indisponível. No **DDoS**, o ataque é feito de forma distribuída por milhares de máquinas infectadas (**Botnets**).
* **Ransomware:**
    * **Como ocorre:** Malware que cifra (bloqueia) os arquivos do utilizador e exige o pagamento de um resgate (geralmente em criptomoedas) para a devolução do acesso.

### **Como se defender**
* **Validação de Entradas:** Implementar filtros rigorosos e consultas parametrizadas (*Prepared Statements*) para evitar injeções.
* **Firewalls e IPS:** Configurar sistemas de prevenção de intrusão que detetem padrões de ataques conhecidos e bloqueiem tráfego de *spoofing*.
* **Autenticação Multifator (MFA):** Garante que, mesmo que o atacante tenha a senha (via Phishing), não consiga aceder à conta.
* **Gestão de Patches:** Manter softwares e sistemas operativos atualizados para fechar brechas de segurança.

---

# **O Fator Humano: Engenharia Social**

A **Engenharia Social** é a arte de manipular pessoas para que elas divulguem informações confidenciais ou realizem ações que comprometam a segurança. Em vez de usar força bruta contra um firewall, o atacante usa a psicologia contra o utilizador.

---

## **1. Principais Técnicas de Engenharia Social**

Os ataques variam desde disparos em massa até operações altamente personalizadas para alvos de alto valor.

### **A. Variantes de Phishing (Focadas em Comunicação)**

* **Phishing Comum:** Disparo em massa de e-mails ou mensagens genéricas para "pescar" qualquer vítima incauta.
* **Spear Phishing:** Ataque direcionado a um indivíduo ou departamento específico. O atacante pesquisa sobre a vítima (nome, cargo, projetos) para tornar a mensagem extremamente convincente.
* **Whaling (Caça à Baleia):** 
    * **O que é:** Um tipo de spear phishing que foca exclusivamente no **topo da pirâmide organizacional** (CEOs, CFOs, Diretores). O objetivo é roubar segredos corporativos de alto nível ou autorizar transferências financeiras massivas.
* **Vishing (Voice Phishing):** Engenharia social via chamadas telefônicas, onde o atacante usa urgência ou autoridade para obter dados.
* **Smishing (SMS Phishing):** Ataques realizados através de mensagens de texto com links maliciosos.

### **B. Técnicas de Proximidade e Interação**

* **Pretexting:** O atacante cria um cenário (pretexto) elaborado. Exemplo: Fingir ser um auditor de TI que precisa de acesso temporário para "corrigir uma falha crítica no perfil do usuário".
* **Baiting (Isca):** Oferecer algo atraente para a vítima. Exemplo: Deixar um pendrive com uma etiqueta "Bônus Salarial 2026" no estacionamento da empresa. Ao conectar o dispositivo, um malware é instalado.
* **Quid Pro Quo (Algo por Algo):** O atacante oferece um serviço em troca de informações. Exemplo: "Eu sou do suporte técnico, estou a ligar para resolver um problema de lentidão, só preciso que me dê a sua senha para rodar o diagnóstico".
* **Tailgating (Carona):** Uma técnica física onde o atacante segue um funcionário autorizado para entrar em uma área restrita antes que a porta se feche.

---

## **2. Os Gatilhos Psicológicos Utilizados**

Os engenheiros sociais exploram tendências comportamentais humanas básicas:

1. **Autoridade:** As pessoas tendem a obedecer a pedidos de quem parece ser um superior ou autoridade legal.
2. **Urgência:** Criar um senso de "faça agora ou sua conta será bloqueada" impede o pensamento crítico.
3. **Escassez:** Oferecer algo exclusivo que está prestes a acabar.
4. **Afeição/Confiança:** Atacantes costumam ser amigáveis e carismáticos para baixar a guarda da vítima.

---

## **3. Defesa: A Camada 8 da Segurança**

Como o alvo é humano, a solução técnica (firewalls/antivírus) é apenas parte da resposta. A verdadeira defesa está na cultura organizacional:

* **Programas de Conscientização:** Simulações periódicas de phishing para treinar o "olho clínico" dos colaboradores.
* **Cultura de Verificação:** Instituir que pedidos de dados sensíveis ou transferências devem ser confirmados por um segundo canal (ex: se recebeu e-mail, ligue para confirmar).
* **Políticas de "Mesa Limpa":** Evitar senhas anotadas em post-its ou documentos sensíveis expostos.
* **Princípio do Menor Privilégio:** Garantir que, mesmo que um usuário caia em um golpe, ele não tenha permissão para comprometer todo o sistema.

---

> **Nota:** Na segurança da informação, costuma-se dizer que "não existe patch para a estupidez humana", por isso a **educação contínua** é a única barreira eficaz contra a Engenharia Social.
