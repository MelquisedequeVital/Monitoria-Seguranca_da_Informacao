# **Algoritmos de Hash: Integridade e Evolução**

Um **algoritmo de hash** é uma função matemática que mapeia dados de entrada de tamanho arbitrário para uma saída de tamanho fixo, geralmente representada por uma sequência de caracteres hexadecimais.

A principal característica do hash é ser **unidirecional**: uma hash não pode ser transformada novamente no texto que lhe deu origem.

---

## **1. O Pilar Garantido: Integridade**

O hash é a ferramenta fundamental para garantir a **Integridade** da informação. Ele permite verificar se os dados foram alterados ou corrompidos durante a transmissão.

*   **Efeito Avalanche:** Se um único bit na entrada for alterado, o hash resultante muda drasticamente.
*   **Assinatura Digital:** Funciona como uma "impressão digital" única. Em 2026, com o avanço de *deepfakes* e IA generativa, o hash tornou-se vital para autenticar a procedência de mídias e documentos oficiais.

---

## **2. Evolução Cronológica e Algoritmos**

A segurança dos algoritmos evoluiu conforme a capacidade de processamento aumentou, tornando versões antigas vulneráveis a ataques de **colisão** (duas entradas diferentes gerando o mesmo hash).

### **A. Família MD (Message Digest)**
*   **MD5 (1991):** Gera um hash de **128 bits**. Criado por Ronald Rivest para suceder o MD4. Atualmente é considerado **inseguro** para sistemas de senhas e segurança crítica devido à facilidade de encontrar colisões.
*   **MD6 (2008):** Versão moderna com saídas de até 512 bits. Foi retirado do concurso SHA-3 por ser considerado lento para a época.

## Algoritmo MD5 (Message Digest Algorithm 5)

O **MD5** é um algoritmo de hash amplamente utilizado que gera uma saída fixa de **128 bits** a partir de uma entrada de dados de qualquer tamanho. O resultado é comumente exibido como um número hexadecimal de 32 dígitos.

#### Funcionamento do MD5

O processo de hashing é dividido em quatro etapas fundamentais:

1.  **Preparação (Padding)**
    A mensagem original é preenchida para que o seu comprimento total seja congruente a 448 mod 512. Isso garante que a mensagem esteja a apenas 64 bits de ser um múltiplo de 512. Em seguida, o tamanho da mensagem original é anexado nesses 64 bits restantes.

2.  **Inicialização**
    O algoritmo utiliza quatro variáveis de 32 bits, conhecidas como registros de encadeamento (**A, B, C, D**). Estes registros são inicializados com constantes hexadecimais específicas.

3.  **Processamento**
    A mensagem é processada em blocos de 512 bits. Cada bloco passa por quatro rodadas de operações. Em cada rodada, funções não lineares (como **AND, OR, XOR e NOT**) são aplicadas aos registros, combinando-os com partes da mensagem e constantes baseadas na função seno.

4.  **Saída**
    Após o processamento de todos os blocos, os valores finais dos registros A, B, C e D são concatenados para produzir o valor de hash final.

---

##### Vulnerabilidades e Segurança

Atualmente, o MD5 não é mais considerado seguro para aplicações que dependem de resistência a colisões.

*   **O que é uma colisão?**
    Ocorre quando duas entradas diferentes produzem exatamente o mesmo hash de saída. No caso do MD5, é possível gerar colisões de forma computacionalmente barata.
*   **Ataques Atuais:**
    Com o poder de processamento moderno, um atacante pode criar arquivos maliciosos com o mesmo hash de um arquivo legítimo em questão de segundos.
*   **Uso Recomendado:**
    Devido a essas falhas, o MD5 deve ser evitado para assinaturas digitais ou armazenamento de senhas, sendo substituído por algoritmos mais robustos como o **SHA-256** ou **SHA-3**.
    
---

### B. Família SHA (Secure Hash Algorithm)

Publicados pelo NIST (National Institute of Standards and Technology), estes representam os padrões globais de hashing.

*   **SHA-0 (1993):** Rapidamente abandonado após a descoberta de vulnerabilidades que permitiam colisões em supercomputadores.
*   **SHA-1 (1995):** Produz um resumo de **160 bits**. Projetado pela NSA, hoje é considerado obsoleto e vulnerável a ataques teóricos.
*   **SHA-2 (2001):** Composto por variantes como **SHA-256** e **SHA-512**. É o padrão de mercado atual e a base de segurança para a maioria das criptomoedas.
*   **SHA-3 (2015):** Utiliza uma construção matemática diferente (função *sponge*), não derivada do MD4. Oferece saídas de tamanho variável (SHAKE128/256).

---

#### Funcionamento do SHA-3

Diferente de seus antecessores, o SHA-3 utiliza a **Construção Sponge (Esponja)**, dividida em três etapas principais:

1.  **Absorção (Absorbing):**
    A mensagem é "absorvida" por um estado interno de **1600 bits**. Cada bloco da mensagem sofre uma operação XOR com o estado, seguido de uma permutação complexa que embaralha os bits de forma irreversível.

2.  **Permutação:**
    O "motor" do algoritmo foca em operações lógicas bit a bit (**AND, NOT, XOR**). Isso o torna imune a ataques que exploram propriedades aritméticas presentes no SHA-2.

3.  **Compressão (Squeezing):**
    Após absorver toda a informação, a "esponja" é espremida. O estado interno é lido para gerar a saída final. Caso seja necessário um hash de comprimento maior, novas permutações são realizadas entre as leituras.

---

## **3. O Cenário em 2026: Segurança Pós-Quântica**

Em 2026, O avanço da computação quântica trouxe novas necessidades para os algoritmos de hash, a segurança foca na resistência a computadores quânticos, mantendo o uso de SHA-256/SHA-3, adotando o veloz BLAKE3 para Big Data e o novo padrão SLH-DSA para assinaturas digitais protegidas.

---

## 4.  **Comparativo de Algoritmos de Hash**

| Algoritmo | Tamanho da Saída | Status Atual | Uso Comum |
| :--- | :--- | :--- | :--- |
| **MD5** | 128 bits | Inseguro | Verificação de integridade simples (Checksums) |
| **SHA-1** | 160 bits | Obsoleto | Legado de certificados digitais |
| **SHA-256** | 256 bits | Seguro | Bitcoin, SSL/TLS, Assinaturas Digitais |
| **SHA-3** | Variável | Altamente Seguro | Sistemas de alta segurança e Plano B ao SHA-2 |

---

> **Nota de Segurança:** Embora o MD5 e o SHA-1 ainda sejam vistos em sistemas antigos, eles são vulneráveis a ataques de colisão e não devem ser utilizados para proteger senhas ou garantir a autenticidade de dados críticos. Para novos projetos, o **SHA-256** ou o **SHA-3** são as escolhas padrão.

---

## 5. Proteção de Dados: Salt e Rainbow Tables

Para garantir a segurança de senhas em um banco de dados, não basta apenas usar um algoritmo forte; é preciso mitigar ataques de pré-computação.

### 1. O que são Rainbow Tables?
As **Rainbow Tables** (Tabelas Arco-íris) são bancos de dados gigantescos que armazenam trilhões de combinações de senhas comuns e seus respectivos hashes já calculados. 
* **O Ataque:** Em vez de tentar adivinhar a senha, o invasor compara o hash roubado com os valores da tabela. Se houver um "match", ele descobre a senha original instantaneamente.
* **Vantagem para o Hacker:** É uma troca de processamento por memória. O esforço maior ocorre apenas uma vez (na criação da tabela), permitindo quebras de senhas em segundos posteriormente.

### 2. A Solução: Salted Hash (Salting)
O **Salt (Sal)** é um valor aleatório e único que é adicionado à entrada (ex: a senha do usuário) antes de gerar o hash final.

* **Saídas Únicas:** Mesmo que dois usuários tenham a mesma senha (ex: `123456`), o Salt de cada um será diferente. Isso resulta em hashes completamente distintos no banco de dados.
* **Inutilizando as Tabelas:** Como as Rainbow Tables são geradas com base em hashes puros (sem sal), elas se tornam inúteis. O invasor teria que gerar uma nova Rainbow Table específica para cada Salt encontrado, o que é computacionalmente inviável.

---

> **Conclusão:** Enquanto o algoritmo de hash (como **SHA-256**) define a "força" da criptografia, o uso de **Salt** define a resistência contra ataques em massa. Em sistemas modernos, nunca se armazena um hash sem a aplicação de um sal aleatório.


> **Nota de Implementação:** Em linguagens como Python, o uso da biblioteca `hashlib` continua sendo o padrão para gerar esses resumos de forma eficiente e segura.
