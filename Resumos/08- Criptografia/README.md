# **Criptografia**

A **criptografia** é a arte e a ciência de disfarçar uma informação para que apenas o destinatário legítimo possa compreendê-la. Ao contrário da esteganografia, que apenas esconde a existência da mensagem, a criptografia transforma o conteúdo original em algo ininteligível (texto cifrado).

---

## **1. O Pilar Garantido: Confidencialidade**

O objetivo primordial da criptografia é garantir a **Confidencialidade** (ou sigilo), assegurando que a informação seja inacessível a qualquer pessoa não autorizada. No entanto, sistemas modernos também utilizam a criptografia para garantir:
*   **Autenticidade:** Confirmar a identidade de quem enviou a mensagem.
*   **Integridade:** Garantir que o conteúdo não foi alterado.
*   **Não-repúdio:** Impedir que o emissor negue a autoria da mensagem.

---

## **2. Criptografia Simétrica vs. Assimétrica**

A grande divisão da criptografia moderna reside em como as chaves são gerenciadas para proteger o pilar da **Confidencialidade**.

### **A. Criptografia Simétrica (Chave Privada)**
Utiliza uma **única chave** para ambos os processos: cifrar e decifrar.

*   **Funcionamento:** É como um cofre físico onde a mesma chave que tranca é a que abre.
*   **Vantagem:** Extremamente rápida e eficiente para grandes volumes de dados.
*   **Desvantagem:** O problema da distribuição. Como enviar a chave para o destinatário de forma segura sem que ela seja interceptada?
*   **Exemplos:** DES, 3DES, AES.

#### **O Algoritmo AES (Advanced Encryption Standard)**

O **AES** é um algoritmo de cifragem de bloco simétrico que se tornou o padrão mundial devido à sua segurança inabalável e alta performance. Diferente de seus antecessores, ele não se baseia apenas em confusão bit a bit, mas em operações matemáticas complexas sobre matrizes.

##### **1. Estrutura e Funcionamento**
O AES trabalha com blocos de dados de **128 bits**, organizados em uma matriz 4x4 chamada de *State*. O processo de transformação do texto simples em texto cifrado ocorre através de várias "rodadas" (*rounds*) de processamento, dependendo do tamanho da chave escolhida:
*   **AES-128:** 10 rodadas.
*   **AES-192:** 12 rodadas.
*   **AES-256:** 14 rodadas.

##### **2. As Quatro Etapas de uma Rodada AES**
Em cada rodada (exceto na última), o algoritmo executa quatro transformações principais que garantem que os dados fiquem completamente irreconhecíveis:

1.  **SubBytes (Substituição):** Cada byte do bloco é substituído por outro de acordo com uma tabela fixa (S-box). Isso gera **confusão**, garantindo que não haja uma relação linear entre o texto original e o cifrado.
2.  **ShiftRows (Transposição):** As linhas da matriz de dados são deslocadas para a esquerda. A primeira linha não muda, a segunda desloca um byte, a terceira dois, e a quarta três. Isso garante que os bytes de uma coluna sejam espalhados por outras colunas.
3.  **MixColumns (Mistura):** Uma operação matemática combina os quatro bytes de cada coluna para formar novos bytes. É essa etapa que espalha a influência de um único byte por todo o bloco (**difusão**).
4.  **AddRoundKey:** Uma "subchave" (derivada da chave original) é combinada com o bloco através de uma operação lógica XOR.

##### **3. Por que ele substituiu o DES e o 3DES?**

Embora o DES e o 3DES tenham sido fundamentais no passado, o AES é superior por três motivos principais:

*   **Resistência à Força Bruta:** O DES usa chaves de 56 bits (bilhões de combinações), o que hoje é quebrado em minutos. O AES-256 possui $1.1 \times 10^{77}$ combinações possíveis; mesmo que todos os computadores do mundo tentassem quebrá-lo simultaneamente, levariam mais tempo do que a idade atual do universo.
*   **Eficiência de Design:** O 3DES é lento porque processa os dados três vezes para tentar compensar a fraqueza da chave curta. O AES foi projetado para ser "nativo" da computação moderna, sendo extremamente rápido em softwares e possuindo instruções específicas em processadores atuais (AES-NI).
*   **Segurança Matemática:** O AES utiliza uma **Rede de Substituição-Permutação (SPN)**, que é matematicamente mais robusta contra criptoanálise do que a estrutura de Feistel utilizada pelo DES.

---

### **B. Criptografia Assimétrica (Chave Pública)**
Utiliza um **par de chaves** matematicamente relacionadas: uma **Pública** (que todos podem saber) e uma **Privada** (que deve ser mantida em segredo absoluto pelo dono).

*   **Funcionamento:** A chave pública cifra a mensagem, mas **apenas** a chave privada correspondente pode decifrá-la. É como uma caixa de correio: qualquer um pode colocar uma carta (cifrar), mas só o dono tem a chave para abrir a caixa e ler (decifrar).
*   **Vantagem:** Resolve o problema da distribuição de chaves, pois você pode publicar sua chave pública para o mundo sem riscos.
*   **Desvantagem:** É muito mais lenta e consome mais processamento que a simétrica.
*   **Exemplos:** RSA, ElGamal, ECC (Curvas Elípticas).

#### **O Algoritmo RSA (Rivest-Shamir-Adleman)**

O **RSA**, criado em 1977, foi o primeiro algoritmo de criptografia assimétrica a ser amplamente utilizado e continua sendo a base da segurança na internet (como nos certificados SSL/TLS). Sua segurança não reside em "misturar" bits, mas sim em um problema clássico da teoria dos números: a **dificuldade de fatorar números primos gigantes**.

##### **1. O Fundamento Matemático**
A segurança do RSA baseia-se na **unidirecionalidade da multiplicação**:
*   É muito fácil para um computador multiplicar dois números primos extremamente grandes ($p$ e $q$) para obter um produto $n$.
*   No entanto, é computacionalmente "impossível" para um computador atual fazer o caminho inverso: descobrir quais eram os dois primos originais ($p$ e $q$) partindo apenas do resultado $n$.

##### **2. Como o Processo Funciona (Simplificado)**
O algoritmo segue três etapas principais:

1.  **Geração de Chaves:** Escolhem-se dois números primos grandes e secretos. A partir deles, gera-se o módulo $n$ (que faz parte da chave pública) e um expoente público. A chave privada é calculada usando uma fórmula matemática (Função Totiente de Euler) que "tranca" o segredo nos primos originais.
2.  **Cifragem:** O remetente transforma a mensagem em um número $m$ e eleva esse número à potência da chave pública, aplicando o módulo $n$:
    $$c = m^e \pmod{n}$$
3.  **Decifragem:** O destinatário, que possui a chave privada $d$, realiza a operação inversa para recuperar a mensagem original:
    $$m = c^d \pmod{n}$$

##### **3. Por que ele é essencial, mas usado com cautela?**

Embora seja extremamente seguro, o RSA possui características que definem como o usamos hoje:

*   **Segurança vs. Tamanho:** Devido ao avanço do poder de processamento, chaves RSA de 1024 bits não são mais consideradas seguras. Atualmente, o padrão mínimo recomendado é **2048 bits** ou **4096 bits**.
*   **Lentidão Matemática:** Por envolver exponenciação de números com milhares de dígitos, o RSA é milhares de vezes mais lento que o AES.
*   **Uso Híbrido:** Na prática, quase nunca usamos o RSA para cifrar um arquivo inteiro. Usamos o RSA apenas para **cifrar a chave do AES**. Assim, temos o melhor dos dois mundos: a facilidade de distribuição do RSA e a velocidade do AES.
*   **Assinatura Digital:** Além de cifrar, o RSA permite que o dono da chave privada "assine" um documento. Se a chave pública conseguir "abrir" a assinatura, o mundo tem a prova matemática de que apenas o dono da chave privada poderia ter criado aquele registro.

## **3. Evolução Cronológica dos Métodos**

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

## **4. O Protocolo Diffie-Hellman: Trocando Segredos em Público**

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


### **D. Por que ele é seguro? (O Problema do Logaritmo Discreto)**

A segurança do Diffie-Hellman reside no fato de que é muito fácil calcular $g^x \bmod p$, mas é humanamente impossível (com computadores clássicos) fazer o caminho inverso: descobrir o $x$ tendo apenas o resultado, o $g$ e o $p$.

*   **Em 2023/2024:** Usamos números tão grandes que levaria bilhões de anos para um supercomputador quebrá-los.
*   **Em 2026 (Panorama Atual):** Devido à ameaça de computadores quânticos que podem resolver esse problema matemático rapidamente, o Diffie-Hellman clássico está sendo substituído ou reforçado pelo **ML-KEM** (Kyber), que utiliza "problemas de reticulados", uma matemática que nem mesmo computadores quânticos conseguem reverter facilmente.

---

### **Resumo dos Pontos-Chave**
*   **DH não envia a chave:** Ele permite que dois lados *criem* a mesma chave simultaneamente.
*   **Canal inseguro:** Funciona perfeitamente mesmo que alguém esteja ouvindo toda a conversa.
*   **Fundamento da Web:** Sem o DH (ou seus sucessores), não existiria comércio eletrônico ou privacidade na internet.

---

## **5. O Cenário em 2026: Segurança Pós-Quântica (PQC)**

Em 2026, a migração para a Criptografia Pós-Quântica (PQC) e o uso de sistemas híbridos são as defesas essenciais para proteger os dados contra a capacidade de quebra de algoritmos clássicos (como o RSA) por computadores quânticos.

---

### **Comparativo de Métodos**

| Algoritmo | Tipo | Tamanho de Chave Comum | Segurança Atual | Eficiência | Resistência Quântica |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **DES** | Simétrico | 56 bits | **Inseguro** (quebrável em minutos) | Alta | Nenhuma |
| **3DES** | Simétrico | 168 bits | **Obsoleto** (uso apenas legado) | Muito Baixa | Baixa |
| **AES** | Simétrico | 128 / 256 bits | **Padrão Ouro** (Seguro) | Altíssima | **Alta** (se 256 bits) |
| **RSA** | Assimétrico | 2048 / 4096 bits | **Risco Alto** (exige chaves imensas) | Baixa | Nenhuma |
| **ECC** | Assimétrico | 256 / 384 bits | **Seguro (Clássico)** | Alta | Nenhuma |
