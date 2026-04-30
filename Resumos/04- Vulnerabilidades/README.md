# **Vulnerabilidades**

As vulnerabilidades são definidas como fraquezas de um ativo ou de um controle que podem ser exploradas por uma ou mais ameaças. Elas representam falhas ou lacunas em sistemas, processos ou comportamentos humanos que expõem a infraestrutura de TI a riscos de acesso não autorizado, roubo ou destruição de dados.

A gravidade dessas falhas é frequentemente catalogada pelo sistema **CVE** (*Common Vulnerabilities and Exposures*), que fornece um registro único para cada falha, e medida pela escala **CVSS** (*Common Vulnerability Scoring System*), que calcula uma nota de impacto de 0 a 10.

As vulnerabilidades são categorizadas em quatro grandes grupos funcionais:

---

## **1. Vulnerabilidades Humanas**

Envolvem falhas decorrentes da desatenção, falta de treinamento ou má fé dos usuários, sendo muitas vezes o ponto de entrada inicial para ataques complexos.

- **Senhas fracas ou previsíveis:** Uso de credenciais em branco, senhas que não utilizam requisitos mínimos de complexidade ou anotadas em locais inseguros (ex: post-it no monitor).
- **Exposição à Engenharia Social:** Falta de conscientização que torna colaboradores vulneráveis a golpes de persuasão e manipulação psicológica para entrega de dados.
- **Uso indevido de recursos:** Compartilhamento de informações sensíveis por canais não protegidos ou manuseio incorreto de mídias físicas.

---

## **2. Vulnerabilidades de Software e Aplicações (OWASP Top 10 - 2025)**

Decorrem de erros cometidos durante o design, desenvolvimento ou implementação de códigos. O padrão ouro para classificar as falhas mais críticas em aplicações web é o **OWASP Top 10**.

O **OWASP Top 10** é um documento de conscientização reconhecido mundialmente, listando os 10 riscos de segurança mais críticos para aplicações web. Elaborado pela fundação OWASP com base em consenso de especialistas, ele ajuda desenvolvedores e empresas a identificar, priorizar e mitigar as vulnerabilidades mais comuns, como injeção, falhas de autenticação e controle de acesso.

### OWASP Top 10

1. **Quebra de Controle de Acesso:** Falha que permite a usuários acessar recursos ou funções fora de suas permissões pretendidas.
   - **Como prevenir:** Implementar o princípio do privilégio mínimo, negar acesso por padrão e centralizar os controles de autorização no servidor.
   - **Exemplo:** Um usuário comum alterando a URL para acessar o painel de `/admin` ou acessando dados de outro cliente mudando um ID.

2. **Falhas Criptográficas:** Exposição de dados sensíveis devido à falta de criptografia, uso de algoritmos fracos ou gerenciamento incorreto de chaves.
   - **Como prevenir:** Utilizar protocolos atuais (TLS 1.3), hashes robustos com salt e não armazenar chaves de criptografia no código-fonte.
   - **Exemplo:** Armazenar senhas de usuários usando apenas o algoritmo MD5 ou transmitir dados de cartão de crédito via HTTP.

3. **Injeção (incluindo IA):** Ocorre quando dados não confiáveis (como comandos SQL ou prompts de IA) são enviados a um interpretador para manipular sua execução.
   - **Como prevenir:** Usar consultas parametrizadas (*Prepared Statements*), validar rigorosamente as entradas e utilizar filtros para saídas de modelos de linguagem.
   - **Exemplo:** Inserir `' OR '1'='1` em um campo de busca ou usar "Ignore todas as instruções anteriores" em um chatbot de IA.

4. **Design Inseguro:** Vulnerabilidades enraizadas em falhas de arquitetura e decisões de design tomadas antes mesmo da escrita do código.
   - **Como prevenir:** Implementar o Ciclo de Vida de Desenvolvimento Seguro (SDLC), modelagem de ameaças e padrões de design de segurança conhecidos.
   - **Exemplo:** Um sistema de e-commerce que confia no preço do produto enviado pelo navegador do cliente no momento da finalização da compra.

5. **Configuração Incorreta de Segurança:** Falta de endurecimento (*hardening*) do sistema, como permissões padrão, serviços desnecessários ativos ou mensagens de erro detalhadas.
   - **Como prevenir:** Desativar recursos não utilizados, alterar todas as senhas padrão e automatizar processos de configuração de ambiente.
   - **Exemplo:** Manter as credenciais de administrador padrão (ex: `admin/admin`) em um console de gerenciamento de nuvem ou banco de dados.

6. **Componentes Vulneráveis e Desatualizados:** Uso de bibliotecas, frameworks ou softwares de terceiros que possuem falhas de segurança conhecidas.
   - **Como prevenir:** Manter um inventário de ativos (SBOM), remover dependências desnecessárias e aplicar patches de segurança imediatamente.
   - **Exemplo:** Utilizar uma versão antiga de uma biblioteca de processamento de imagens que permite a execução remota de código (RCE).

7. **Falhas de Identificação e Autenticação:** Problemas na confirmação da identidade do usuário, como gestão de sessões fraca ou ausência de proteção contra força bruta.
   - **Como prevenir:** Implementar autenticação de múltiplos fatores (MFA), políticas de senhas fortes e rotatividade de IDs de sessão.
   - **Exemplo:** Permitir que um robô tente milhares de combinações de senhas sem bloquear a conta ou exigir um captcha.

8. **Falhas na Cadeia de Suprimentos de Software:** Riscos associados à integridade do código e infraestrutura de terceiros, incluindo plugins e pipelines de build.
   - **Como prevenir:** Verificar assinaturas digitais de atualizações, auditar dependências e garantir a segurança do ambiente de CI/CD.
   - **Exemplo:** Um invasor injeta código malicioso em um pacote popular do NPM que sua aplicação baixa automaticamente durante o deploy.

9. **Tratamento Incorreto de Condições Excepcionais:** Falhas na forma como o sistema lida com erros, podendo causar interrupções ou vazar dados técnicos sobre a infraestrutura.
   - **Como prevenir:** Implementar mensagens de erro genéricas para o usuário e garantir que exceções não parem o funcionamento de controles de segurança.
   - **Exemplo:** Um erro de banco de dados que exibe na tela do usuário a estrutura completa das tabelas e a versão do servidor SQL.

10. **Falsificação de Solicitação do Lado do Servidor (SSRF):** Ocorre quando a aplicação web busca um recurso remoto sem validar a URL fornecida pelo usuário, atingindo sistemas internos.
    - **Como prevenir:** Validar entradas contra listas permitidas (Allowlist) e restringir o acesso da aplicação a redes internas e metadados de nuvem.
    - **Exemplo:** Induzir o servidor a fazer uma requisição interna para obter as credenciais de acesso da instância de nuvem (AWS/Azure/GCP).

---

## **3. Vulnerabilidades de Rede e Infraestrutura**

Referem-se à arquitetura de comunicação e aos dispositivos que interconectam os sistemas.

- **Segurança Fraca no Perímetro:** Firewalls mal configurados ou portas de rede críticas expostas diretamente à internet.
- **Transporte de Dados sem Criptografia:** Tráfego de informações sensíveis em texto claro através da rede, facilitando a interceptação (*Sniffing*).
- **Roteadores sem Antispoofing:** Falta de configuração para impedir que atacantes forjem endereços IP de origem.

---

## **4. Vulnerabilidades Físicas e Processuais**

Dizem respeito ao ambiente físico e às normas de gestão da segurança organizacional.

- **Falta de Controle de Acesso Físico:** Ausência de travas, monitoramento por câmeras ou barreiras para proteger salas de servidores e equipamentos.
- **Inexistência de Cultura/Política de SI:** Falta de diretrizes gerenciais, processos de descarte seguro de mídias e planos de resposta a incidentes.
- **Deficiências Ambientais:** Falta de sistemas de energia ininterrupta (UPS/Geradores) ou refrigeração inadequada.