# **Criptografia**

A **criptografia** é a arte e a ciência de disfarçar uma informação para que apenas o destinatário legítimo possa compreendê-la. Ao contrário da esteganografia, que apenas esconde a existência da mensagem, a criptografia transforma o conteúdo original em algo ininteligível (texto cifrado).

---

## **1. O Pilar Garantido: Confidencialidade**

O objetivo primordial da criptografia é garantir a **Confidencialidade** (ou sigilo), assegurando que a informação seja inacessível a qualquer pessoa não autorizada. No entanto, sistemas modernos também utilizam a criptografia para garantir:
*   **Autenticidade:** Confirmar a identidade de quem enviou a mensagem.
*   **Integridade:** Garantir que o conteúdo não foi alterado.
*   **Não-repúdio:** Impedir que o emissor negue a autoria da mensagem.

---

## **2. Evolução Cronológica dos Métodos**

A história da criptografia é dividida em fases que acompanham o desenvolvimento tecnológico da humanidade.

### **A. Fase Artesanal (Antiguidade e Idade Média)**
Baseava-se em métodos manuais de substituição e transposição:
*   **Scytale (Grécia Antiga):** Um bastão onde uma tira de papiro era enrolada para transpor a ordem das letras.
*   **Código de César (Império Romano):** Uma cifra de substituição monoalfabética onde cada letra era deslocada um número fixo de posições no alfabeto.
*   **Cifras Monoalfabéticas (Idade Média):** Cada letra do alfabeto correspondia a um símbolo ou letra fixa. Tornaram-se vulneráveis após a descoberta da **análise de frequências** pelos árabes (séc. IX).

### **B. Fase Mecânica (Idade Moderna e Guerras Mundiais)**
O início da mecanização permitiu cifras polialfabéticas mais complexas:
*   **Cifra de Vigenère (1580):** Considerada a "cifra indecifrável" por séculos, utilizava múltiplos alfabetos de César simultaneamente.
*   **Máquina Enigma (Segunda Guerra Mundial):** Máquina alemã que utilizava rotores eletromecânicos para gerar bilhões de combinações de chaves simétricas. Sua quebra pelos aliados foi um marco na criptoanálise.

### **C. Fase Digital e Eletrônica (Séc. XX)**
Com os computadores, a segurança passou a residir na chave e não mais no segredo do algoritmo:
*   **DES (1974):** Padrão de chave simétrica de 56 bits. Tornou-se obsoleto devido ao curto tamanho da chave.
*   **AES (2001):** Sucessor do DES, com chaves de 128 a 256 bits. É o padrão mundial atual para criptografia simétrica.
*   **Criptografia de Chave Pública (RSA - 1977):** Revolucionou a área ao usar um par de chaves (pública e privada), eliminando a necessidade de trocar chaves secretas previamente por canais inseguros.

---

## **3. O Protocolo Diffie-Hellman: Trocando Segredos em Público**

Proposto em 1976, o protocolo **Diffie-Hellman** permitiu que duas partes criassem uma chave secreta compartilhada através de um canal monitorado, sem nunca terem trocado chaves antes.
*   **Como funciona:** Baseia-se na dificuldade matemática do **Logaritmo Discreto**. Alice e Bob trocam valores calculados a partir de chaves privadas secretas e parâmetros públicos (número primo e base). Ao final, ambos chegam matematicamente ao mesmo segredo compartilhado, enquanto um observador externo não consegue reverter o cálculo.
*   Para entender como ele faz essa "mágica", vamos usar a analogia clássica das cores e um exemplo de uso no dia a dia.

### **A. A Analogia das Cores (O conceito visual)**

Imagine que Alice e Bob querem combinar uma cor secreta, mas a espiã Eva está observando tudo o que eles trocam.

*   a.  **Acordo Público:** Alice e Bob escolhem uma cor inicial publicamente (ex: **Amarelo**). Eva agora sabe que a base é Amarelo.
*   b.  **Segredos Privados:**
    *   Alice escolhe uma cor secreta (ex: **Vermelho**) e não conta a ninguém.
    *   Bob escolhe sua própria cor secreta (ex: **Azul**) e também a mantém escondida.
*   c.  **A Mistura Pública:**
    *   Alice mistura seu segredo (Vermelho) com a base (Amarelo) e obtém **Laranja**. Ela envia o Laranja para Bob.
    *   Bob mistura seu segredo (Azul) com a base (Amarelo) e obtém **Verde**. Ele envia o Verde para Alice.
    *   *Eva vê passar o Laranja e o Verde, mas ela não consegue "separar" as cores para descobrir o Vermelho ou o Azul originais.*
*   d.  **O Segredo Final (A Mágica):**
    *   Alice pega o Verde de Bob e adiciona sua cor secreta (Vermelho).
    *   Bob pega o Laranja de Alice e adiciona sua cor secreta (Azul).
    *   **Resultado:** Ambos chegam exatamente à mesma cor final (um **Marrom** específico)!

Eva tem o Amarelo, o Laranja e o Verde, mas sem as cores secretas, ela nunca chegará ao Marrom final. **Na matemática, as cores são números e a "mistura" é a exponenciação modular.**

---

### **B. Caso Real: O "Cadeado" do Navegador (HTTPS)**

Sempre que você acessa um site seguro (como o seu banco ou o Gmail), o protocolo **TLS/SSL** entra em ação. O Diffie-Hellman é frequentemente usado na fase de "Handshake" (aperto de mão) desse processo.

**O cenário:**
Você (seu navegador) quer conversar com o servidor do banco. Vocês precisam de uma **chave simétrica** (como o AES-256) para criptografar as mensagens de forma rápida. Mas como enviar essa chave ao banco sem que um hacker no Wi-Fi do shopping a veja?

## **C. A Solução com Diffie-Hellman (DH)**

Para garantir que uma comunicação seja privada, o protocolo Diffie-Hellman segue estas etapas fundamentais:

*   **a. Parâmetros Públicos**  
    Seu computador e o servidor do banco concordam abertamente em um número primo imenso (ex: de **2048 bits**) e uma base matemática. Como esses números são públicos, qualquer um pode vê-los, mas eles sozinhos não revelam nada.

*   **b. Troca de Chaves Públicas**  
    Seu computador gera uma **chave privada temporária** e, a partir dela, calcula uma **chave pública** para enviar ao banco. O banco realiza exatamente o mesmo processo.

*   **c. Criação do Segredo**  
    Ambos os lados combinam suas próprias chaves privadas com a chave pública recebida do outro lado. Graças à aritmética modular, ambos chegam ao **mesmo número secreto** de forma independente.

*   **d. Conversa Segura**  
    Esse número secreto torna-se a **"Chave da Sessão"**. A partir desse momento, todos os dados sensíveis (senhas, saldos, transações) são criptografados com essa chave que **nunca viajou pela rede**, tornando-a impossível de ser interceptada.
---


### **C. Por que ele é seguro? (O Problema do Logaritmo Discreto)**

A segurança do Diffie-Hellman reside no fato de que é muito fácil calcular $g^x \bmod p$, mas é humanamente impossível (com computadores clássicos) fazer o caminho inverso: descobrir o $x$ tendo apenas o resultado, o $g$ e o $p$.

*   **Em 2023/2024:** Usamos números tão grandes que levaria bilhões de anos para um supercomputador quebrá-los.
*   **Em 2026 (Panorama Atual):** Devido à ameaça de computadores quânticos que podem resolver esse problema matemático rapidamente, o Diffie-Hellman clássico está sendo substituído ou reforçado pelo **ML-KEM** (Kyber), que utiliza "problemas de reticulados", uma matemática que nem mesmo computadores quânticos conseguem reverter facilmente.

---

### **Resumo dos Pontos-Chave**
*   **DH não envia a chave:** Ele permite que dois lados *criem* a mesma chave simultaneamente.
*   **Canal inseguro:** Funciona perfeitamente mesmo que alguém esteja ouvindo toda a conversa.
*   **Fundamento da Web:** Sem o DH (ou seus sucessores), não existiria comércio eletrônico ou privacidade na internet.

---

## **4. O Cenário em 2026: Segurança Pós-Quântica (PQC)**

Em 2026, o maior desafio da criptografia é o avanço da computação quântica (o chamado **Q-Day** ou **Y2Q**).
*   **Vulnerabilidade dos Sistemas Clássicos:** Computadores quânticos potentes podem quebrar rapidamente algoritmos baseados em fatoração (RSA) e logaritmos discretos (Diffie-Hellman/ECC).
*   **Transição para PQC:** Em 2024 e 2025, o NIST (EUA) padronizou os primeiros algoritmos de criptografia pós-quântica (como o **ML-KEM** e **ML-DSA**). Em 2026, empresas de tecnologia e órgãos governamentais estão em fase acelerada de migração para esses novos padrões, que se baseiam em problemas matemáticos resistentes a ataques quânticos (como criptografia baseada em reticulados).
*   **Criptografia Híbrida:** Atualmente, utiliza-se a abordagem híbrida: combina-se um algoritmo clássico (como AES/RSA) com um pós-quântico, garantindo segurança contra ameaças de hoje e de amanhã.

---

### **Comparativo de Métodos (Atualizado 2026)**

| Tipo de Criptografia | Exemplo de Algoritmo | Uso em 2026 | Resistência Quântica |
| :--- | :--- | :--- | :--- |
| **Simétrica** | AES-256 | Padrão para proteção de dados em massa. | Alta (se a chave for grande) |
| **Assimétrica Clássica**| RSA / Diffie-Hellman | Sendo substituída gradualmente. | Nenhuma |
| **Assimétrica PQC** | ML-KEM (Kyber) | Novo padrão para troca de chaves. | Alta |
| **Híbrida** | TLS 1.3 + PQC | Padrão para navegação web segura. | Máxima |
