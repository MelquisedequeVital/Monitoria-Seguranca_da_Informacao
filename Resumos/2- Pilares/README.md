# Pilares da Segurança da Informação

A Segurança da Informação é baseada em pilares essenciais, destacando-se a Confidencialidade, a Integridade e a Disponibilidade (Tríade CID), além dessas 3 ainda há a Autenticidade, o Não Repúdio(Irretratabilidade) e a Legalidade. O objetivo é proteger dados e sistemas contra acessos, alterações ou destruições não autorizadas, garantindo a autenticidade e a conformidade legal (como a LGPD).

## Confidencialidade

Garante que a informação seja acessada apenas por pessoas, sistemas ou processos autorizados, protegendo contra acessos não autorizados

### Como implementar

Utilize criptografia de dados, controle rigoroso de acesso e autenticação multifator.

- Exemplos: 
		- Criptografar o banco de dados de clientes para que invasores não consigam ler as informações mesmo se houver vazamento.
		- Exigir biometria ou tokens físicos para liberar o acesso a pastas restritas da rede corporativa. 

### Violação

Ocorre quando informações sigilosas caem nas mãos de quem não deveria ter acesso

- Consequências: Exposição de segredos industriais, processos por danos morais e perda de vantagem competitiva.
- Exemplos: Hackers invadem os servidores de uma clínica médica e vazam na internet os prontuários e resultados de exames de milhares de pacientes.

## Integridade

Assegura que a informação seja mantida em seu estado original, protegendo-a contra modificações, corrupções ou exclusões não autorizadas, garantindo sua veracidade

### Como implementar

Utilize funções de hash (como SHA-256), assinaturas digitais, sistemas de controle de versão e trilhas de auditoria.

- Exemplos:
		- Calcular o código hash de um arquivo de instalação de software para garantir que ele não foi modificado por um vírus.
		- Manter um histórico imutável (como em blockchain ou logs protegidos) que registra quem alterou um documento e em qual horário.

### Violação

Ocorre quando os dados são alterados, deletados ou corrompidos de forma não autorizada, propositalmente ou por acidente

- Consequências: Tomada de decisões baseada em dados falsos, perda de credibilidade e falhas graves de operação.
- Exemplo: Um funcionário mal-intencionado ou um invasor altera os valores de uma planilha financeira corporativa. A diretoria aprova investimentos com base nesses números inflados e a empresa sofre um rombo milionário.


## Disponibilidade

Garante que a informação e os sistemas estejam acessíveis para uso pelos usuários autorizados sempre que necessário, evitando interrupções.

### Como implementar

Faça redundância de servidores (Cluster), adote planos de backup frequentes e utilize proteção contra ataques DDoS.

- Exemplos:
		- Manter dois servidores rodando o mesmo site; se um falhar ou queimar, o outro assume o tráfego instantaneamente sem queda do serviço.
		- Armazenar backups diários e automatizados na nuvem para recuperar os dados da empresa em caso de ataque de ransomware.

### Violação

Ocorre quando os sistemas, redes ou dados ficam fora do ar e os usuários legítimos não conseguem trabalhar ou usar o serviço.

- Consequências: Prejuízos financeiros imediatos por travar vendas, multas contratuais por quebra de nível de serviço (SLA) e insatisfação de clientes.
- Exemplo: Um ataque de DDoS (Negação de Serviço) inunda o site de um grande e-commerce de acessos falsos. O portal cai durante a Black Friday, impedindo milhares de compras legítimas.

## Autenticidade

Confirma que a informação ou usuário é legítimo, garantindo que quem enviou ou acessou o dado é quem diz ser.

### Como implementar

Implemente certificados digitais SSL/TLS, logins com múltiplos fatores (MFA) e senhas fortes.

- Exemplos;
		- O cadeado verde no navegador (protocolo HTTPS) que comprova que você está acessando o site real do seu banco e não uma cópia falsa.
		- O envio de um código SMS temporário para o celular do usuário após ele digitar a senha correta no sistema da empresa.
		
### Violação

Ocorre quando alguém ou algum sistema finge ser outra pessoa (falsidade ideológica digital ou personificação).
 
- Consequências: Fraudes financeiras e facilidade para roubo posterior de dados internos.
- Exemplo: Um criminoso envia um e-mail falso se passando pelo Diretor Executivo (técnica de CEO Scam), solicitando que o setor financeiro faça um pagamento urgente para uma conta fantasma.

## Não Repúdio(Irretratabilidade)

Impede que alguém negue ter realizado uma ação (como enviar um e-mail ou assinar um documento), garantindo a responsabilidade legal.

### Como implementar

Force o uso de assinatura digital qualificada e registro minucioso e centralizado de logs de atividade.

- Exemplos;
		- Uso de certificado digital padrão ICP-Brasil para assinar um contrato de prestação de serviços digitalmente; o autor não pode alegar que não assinou.
		- Registrar em log inviolável que o "Usuário X" aprovou uma transferência financeira às 14h, impedindo-o de dizer que desconhece a transação.
	
### Violação

Ocorre quando o sistema não possui mecanismos para provar legalmente quem executou determinada transação
 
- Consequências: Impossibilidade de cobrar devedores judicialmente e brechas massivas para fraudes internas sem culpados identificáveis.
- Exemplo: Um cliente contrata um empréstimo volumoso de um banco ou assina um contrato de prestação de serviços clicando apenas em um botão de aceite ou enviando uma foto segurando o documento. Meses depois, o cliente para de pagar e alega na Justiça que nunca assinou aquele documento ou que outra pessoa utilizou a sua foto indevidamente. Como a empresa utilizou um método de assinatura eletrônica simples, sem o uso de certificados digitais qualificados ou biometria avançada, o juiz acaba dando ganho de causa ao cliente. Isso ocorre porque o sistema da instituição não foi capaz de oferecer garantias técnicas e legais irrefutáveis de que foi o próprio titular quem realizou a ação, permitindo que ele repudiasse o contrato com sucesso.

## Legalidade

Refere-se à conformidade com leis e regulamentos vigentes, como a LGPD, garantindo que os procedimentos de segurança sigam as normas legais.

### Como implementar

Realize auditorias jurídicas e técnicas periódicas, elabore políticas de privacidade e treine a equipe conforme as regulamentações.

- Exemplos;
		- Adequar os sistemas internos para atender às regras da LGPD (Lei Geral de Proteção de Dados), coletando apenas os dados estritamente necessários e com o consentimento do titular.
		- Implementar os controles da norma ISO/IEC 27001 para certificar que a empresa segue padrões internacionais de segurança.
		
### Violação

Ocorre quando a organização descumpre leis de proteção de dados, regulações de conformidade ou termos contratuais de privacidade
 
- Consequências:  Sanções administrativas, suspensão de atividades e multas pesadas aplicadas por órgãos reguladores.
- Exemplo:Uma empresa coleta dados pessoais sensíveis de menores de idade sem o consentimento explícito dos pais. A ANPD (Autoridade Nacional de Proteção de Dados) descobre a prática e aplica uma multa de até 2% do faturamento da empresa com base na LGPD.
