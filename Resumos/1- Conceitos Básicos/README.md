# **Conceitos Básicos**

A base da Segurança da Informação moderna, orientada por padrões como a família ISO 27000 (conjunto internacional de normas para a gestão da segurança da informação), gira em torno de entender o que precisa ser protegido, do que precisa ser protegido e o que acontece quando essa proteção falha.

## **Ativo (Asset)**

Ativo, na segurança da informação, é qualquer recurso, dado ou elemento de valor para uma organização, como bancos de dados, servidores, softwares, contratos ou informações de clientes, que precisa de proteção contra ameaças para garantir sua confidencialidade, integridade e disponibilidade.
  
### **Exemplos**

- **Tangíveis**: Hardware, instalações físicas, documentos impressos, data centers.  
- **Intangíveis**: Informação (dados), software, propriedade intelectual, imagem e a reputação da marca no mercado.  
- **Humanos**: As próprias pessoas, suas habilidades e experiências também são ativos críticos.
  
### **Avaliação de Ativos**

A avaliação tem como objetivo identificar, classificar e valorar ativos. Baseado em normas como a ISO/IEC 27005, o processo envolve classificar ativos (ex: público, confidencial) para determinar controles de segurança adequados e mitigar riscos.

A avaliação de ativos é realizada para priorizar os ativos mais críticos, cumprir exigências legais(Compliance) e proteger ativos vitais durante incidentes.

#### Principais Etapas na Avaliação de Ativos

- **Identificação**: Mapear todos os recursos valiosos (físicos, software, informações).
- **Classificação**: Definir níveis de criticidade e sensibilidade (ex: Restrita, Uso Interno, Pública).
- **Valoração**: Atribuir valor com base no impacto de uma violação.
- **Análise de Riscos**: Avaliar ameaças e vulnerabilidades.
- **Controles**: Estabelecer medidas de proteção (criptografia, controle de acesso, backup).

## **Vulnerabilidade**

É a fraqueza de um ativo ou de um controle que pode ser explorada. A vulnerabilidade por si só não causa dano; ela é a "porta destrancada".  

- Pode ser uma falha de software (como ausência de atualizações e patches), portas de rede abertas desnecessariamente, senhas fracas ou até mesmo a falta de treinamento de conscientização de um funcionário.

## **Evento vs Incidente**

É vital separar o que é apenas o "ruído" do dia a dia do que é um problema real.

- **Evento de Segurança**: É qualquer ocorrência identificada que indica uma mudança de estado em um sistema, serviço ou rede. Pode ser o indício de uma possível violação de política ou uma falha de proteção, mas nem todo evento é um ataque. Exemplos práticos: Funcionário tentando acessar uma pasta restrita, múltiplos logins errados, varredura de porta (port scanning).
  
- **Incidente de Segurança**: É Um evento(ou uma série deles) que foi confirmado como uma violação ou ameaça real à segurança da informação. Exemplos práticos: Infecção por ransomware, vazamento de dados, exclusão maliciosa de arquivos, página web pichada.

Em resumo, o evento é o sinal de fumaça; o incidente é o fogo.

## **Ameaça**

Uma ameaça é a causa potencial de um incidente que pode resultar em dano ao sistema ou à organização.

- **Ameaças Humanas**: Podem ser intencionais (hackers, engenharia social, espionagem industrial, funcionários mal-intencionados) ou não intencionais (um funcionário que apaga um banco de dados por acidente ou clica em um link de phishing).

- **Ameaças Não Humanas**: Falhas de infraestrutura (queda de energia) ou desastres naturais (enchentes, incêndios, raios).

## **Risco e Exposição**

- **Risco**: É o efeito da incerteza sobre os objetivos. Em segurança, é expresso como a combinação da probabilidade de um evento ocorrer e a gravidade de sua consequência (o impacto). O risco existe quando uma Ameaça tem o potencial de explorar uma Vulnerabilidade em um Ativo, causando dano.
    - Exemplo: O risco de interrupção das vendas em um e-commerce. Se o servidor cair (evento) devido a um excesso de acessos (ameaça), o impacto financeiro será de R$ 10.000,00 por hora parado.

- **Exposição**: É a circunstância de estar exposto aos prejuízos oriundos de um agente ameaçador. 
    - Exemplo: Se o banco de dados tem senhas fracas (vulnerabilidade), a empresa está exposta ao risco de vazamento de dados caso um hacker (ameaça) ataque.

## **Ataque**

Enquanto a Ameaça é o potencial de dano, o Ataque é a materialização dessa ameaça; é a ação propriamente dita de explorar uma vulnerabilidade.

- **Definição Formal**: É uma tentativa de destruir, expor, alterar, inutilizar, roubar, obter acesso não autorizado ou fazer uso não autorizado de um ativo. 

- **Visão Prática**: Consiste em acessar dados ou usar recursos sem ter permissão, executar comandos se passando por outro usuário (escalada de privilégios) ou violar diretamente uma política de segurança pré-estabelecida.

### **Categorias de Ataque**

#### Por Comportamento

- **Ataques Passivos**: O atacante apenas "escuta" ou monitora o tráfego e a comunicação, sem alterar os dados. O objetivo é violar a confidencialidade. Exemplos: Sniffing (farejar pacotes de rede) ou Spyware. 

- **Ataques Ativos**: O atacante altera a informação, forja identidades ou interrompe o serviço. Eles violam a integridade, a disponibilidade e a autenticidade. Exemplos: Falsificação de mensagens (Spoofing), modificação de dados ou Negação de Serviço (DoS/DDoS). 

#### Por Origem

- **Ataques Externos**: Iniciados por agentes de fora da rede corporativa (hackers, concorrentes, governos). Eles precisam romper as barreiras de firewalls e defesas de borda.
  
- **Ataques Internos (Insider Threats)**: Realizados por pessoas que já possuem acesso autorizado à rede interna (como funcionários insatisfeitos, ex-colaboradores ou prestadores de serviço). São perigosos porque contornam a maior parte das defesas externas.

--- 

## **Controles, Contramedidas e Tratamento de Riscos**

Organizações aplicam controles e ferramentas automatizadas desde o início da criação de um software para mitigar riscos e evitar vulnerabilidades em produção. O tratamento desses riscos segue quatro estratégias principais:

- **Prevenção (Evitar)**: Elimina a falha na fase de design. Ex: uso de modelagem de ameaças e componentes padronizados que impedem ataques.
- **Redução (Mitigação)**: Minimiza o impacto de falhas existentes. Ex: uso de criptografia, sanitização de dados e testes automatizados (SAST/DAST).
- **Transferência**: Terceiriza a responsabilidade de partes críticas. Ex: uso de APIs externas de pagamento/autenticação e contratação de seguros cibernéticos.
- **Aceitação**: Mantém o risco intencionalmente quando o custo de refatoração do código é maior que o prejuízo potencial. O risco que permanece é o Risco Residual.