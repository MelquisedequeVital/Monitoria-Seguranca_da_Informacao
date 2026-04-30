# **Desenvolvimento Seguro de Software (Secure Development)**

O desenvolvimento seguro é a prática de integrar a segurança em todas as fases do Ciclo de Vida de Desenvolvimento de Software (SDLC). O código de qualidade é inerentemente seguro e a segurança deve ser vista como o pilar que garante que a inovação sobreviva no ambiente hostil da internet.

---

## **1. O que é Desenvolvimento Seguro?**

É a abordagem de construir software resiliente desde a sua concepção. Em vez de tratar a segurança como um "remendo" aplicado após a conclusão do código (abordagem reativa), ela se torna parte do tecido que conecta todo o ciclo de vida do software (abordagem proativa).

### **Por que é importante?**
* **Redução de Custos:** O custo de correção de uma vulnerabilidade cresce exponencialmente. Corrigir uma falha no **Design** é até 100x mais barato do que corrigi-la em **Produção**.
* **Prevenção de Incidentes:** 90% dos incidentes cibernéticos são causados por defeitos no design ou no código.
* **Confiança e Conformidade:** Atende a regulamentações e garante a integridade dos dados dos usuários.

---

## **2. Princípios Fundamentais (S-SDLC)**

A base para um software resiliente reside em quatro pilares fundamentais:

* **Segurança por Design (*Security by Design*):** A segurança é considerada desde a análise de requisitos.
* **Segurança por Código:** Escrita defensiva para evitar armadilhas lógicas e vulnerabilidades técnicas.
* **Segurança por Teste:** Identificação contínua e automatizada de falhas durante a construção.
* **Segurança por Operação:** Configuração de servidores, infraestrutura e controle de acesso rígidos.

---

## **3. Etapas Obrigatórias do SDL (Microsoft)**

O Microsoft Security Development Lifecycle (SDL) é um processo que incorpora segurança em todas as fases do desenvolvimento, dividido geralmente em sete etapas principais: Treinamento, Requisitos, Design, Implementação, Verificação, Lançamento e Resposta. O objetivo é reduzir vulnerabilidades, focando em modelagem de ameaças e testes rigorosos. :

1.  **Treinamento:** Capacitar a equipe em conceitos básicos de segurança e privacidade.
2.  **Requisitos:** Estabelecer requisitos de segurança e analisar riscos de privacidade.
3.  **Design:** Definir a arquitetura segura e realizar a **Modelagem de Ameaças (STRIDE)**.
4.  **Implementação:** Utilizar ferramentas aprovadas, realizar análise estática (SAST) e evitar funções inseguras.
5.  **Verificação:** Realizar análise dinâmica (DAST) e testes de invasão (Fuzz Testing).
6.  **Lançamento (Release):** Revisão final de segurança e plano de resposta a incidentes.
7.  **Resposta:** Executar o plano de resposta a incidentes em caso de vulnerabilidades pós-lançamento.

### **Conceitos Chave desta Etapa:**

*   **STRIDE:** É um modelo para categorizar ameaças. A sigla representa: **S**poofing (Falsificação), **T**ampering (Adulteração), **R**epudiation (Repúdio), **I**nformation Disclosure (Vazamento de Dados), **D**enial of Service (Negação de Serviço) e **E**levation of Privilege (Elevação de Privilégio).
*   **SAST (Static Application Security Testing):** É a análise do código "parado" (sem execução). O objetivo é encontrar falhas de segurança no código-fonte, bytes ou binários durante a fase de implementação.
*   **DAST (Dynamic Application Security Testing):** É o teste da aplicação "em movimento" (rodando). Ele simula ataques externos em uma aplicação web em tempo de execução para encontrar vulnerabilidades que só aparecem quando o sistema está operando.

---

## **4. Políticas de Design Seguro: Exemplos Corporativos**

Seguindo o modelo da **Microsoft SDL**, as políticas focam na redução da superfície de ataque:

* **Privilégio Mínimo por Padrão:** O software deve rodar com o menor nível de privilégio necessário para sua função.
* **Redução da Superfície de Ataque:** Desativar funcionalidades e portas não essenciais por padrão.
* **Padrões Seguros (*Secure Defaults*):** A configuração inicial deve ser a mais protegida; o usuário deve optar por abrir exceções.
* **Defesa em Profundidade:** Implementar múltiplas camadas de proteção independentes.

---

## **5. Checklist do Desenvolvedor Seguro (OWASP)**

A **OWASP** (*Open Web Application Security Project*) é uma fundação sem fins lucrativos que atua como uma comunidade global para melhorar a segurança do software. Ela é amplamente reconhecida por criar padrões e guias, como o **OWASP Top 10**, que lista as vulnerabilidades mais críticas em aplicações web para ajudar desenvolvedores a combater falhas recorrentes.

O Checklist do Desenvolvedor Seguro da OWASP é um guia prático de boas maneiras para programadores criarem sistemas protegidos contra invasões.

Em vez de focar apenas em como os hackers atacam (o que o famoso OWASP Top 10 faz), este checklist foca no que o desenvolvedor deve fazer durante a escrita do código para evitar que essas portas fiquem abertas.

* **[1] Entradas e Saídas:** Valide todas as entradas via *Allowlists* e codifique saídas conforme o contexto (HTML, SQL, JS).
* **[2] Identidade e Sessão:** Use cookies com flags `HttpOnly` e `Secure`. Troque IDs de sessão imediatamente após o login.
* **[3] Banco de Dados:** Use exclusivamente **Consultas Parametrizadas** (*Prepared Statements*). Nunca concatene strings em SQL.
* **[4] Configuração e Dados:** Jamais insira senhas ou chaves no código. Trate erros de forma genérica para não vazar dados técnicos.
