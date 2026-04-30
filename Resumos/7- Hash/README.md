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

### **B. Família SHA (Secure Hash Algorithm)**
Publicados pelo NIST, são os padrões globais.
*   **SHA-0 (1993):** Rapidamente abandonado após a descoberta de vulnerabilidades que permitiam colisões em supercomputadores.
*   **SHA-1 (1995):** Produz um resumo de **160 bits**. Projetado pela NSA, hoje é considerado obsoleto e vulnerável a ataques teóricos.
*   **SHA-2 (2001):** Composto por variantes como **SHA-256** e **SHA-512**. É o padrão de mercado atual e base de segurança para a maioria das criptomoedas.
*   **SHA-3 (2015):** Utiliza uma construção matemática diferente (função *sponge*), não derivada do MD4. Oferece saídas de tamanho variável (SHAKE128/256).

---

## **3. O Cenário em 2026: Segurança Pós-Quântica**

O avanço da computação quântica trouxe novas necessidades que complementam o conteúdo de 2023:

*   **Resiliência Quântica:** Diferente dos algoritmos de criptografia assimétrica (como RSA), o **SHA-256** e o **SHA-3** são considerados resistentes a ataques quânticos. Um computador quântico reduz a segurança, mas não a quebra completamente.
*   **BLAKE3 (Alta Performance):** Algoritmo que ganhou força em 2026 por ser muito mais rápido que o SHA-3 e aproveitar o processamento paralelo (multicore), sendo ideal para validar grandes volumes de dados (Big Data).
*   **SLH-DSA:** Novo padrão do NIST para assinaturas digitais baseadas em hash, projetado especificamente para ser seguro contra computadores quânticos (Pós-Quântico).

---

## **4. Comparativo de Segurança (Atualizado 2026)**

| Algoritmo | Tamanho (Bits) | Status de Segurança | Uso Recomendado |
| :--- | :--- | :--- | :--- |
| **MD5** | 128 | **Inseguro** | Apenas para somas de verificação não críticas. |
| **SHA-1** | 160 | **Obsoleto** | Deve ser evitado. |
| **SHA-256** | 256 | **Seguro** | Padrão ouro para indústria e blockchain. |
| **SHA-3** | 224 a 512 | **Altamente Seguro** | Sistemas governamentais e críticos. |
| **BLAKE3** | 256 | **Seguro e Veloz** | Grandes arquivos e alto tráfego de dados. |

---

## **5. Defesa: Salted Hash**

Para proteger sistemas contra bancos de dados de hashes pré-calculados (Rainbow Tables), utiliza-se o **Salted Hash**:
*   **Salt (Sal):** Um valor aleatório é adicionado à entrada (ex: senha) antes de gerar o hash. Isso garante que, mesmo que dois usuários usem a mesma senha, seus hashes finais no banco de dados sejam diferentes, impedindo ataques de comparação em massa.

---
> **Nota de Implementação:** Em linguagens como Python, o uso da biblioteca `hashlib` continua sendo o padrão para gerar esses resumos de forma eficiente e segura.