# 01 - Fundamentos dos Sistemas Operacionais modernos

## Sistemas Operacionais
- "Programas implementados, como software ou firmware, que tornam o hardware utilizável."
- Camada de software intermediária entre os componentes de hardware, os usuários e seus programas.
- Deve controlar os recursos do computador, otimizando sua utilização.

    1. HARDWARE
        - dispositivos do computador
        - parte física do sistema

    2. SOFTWARE 
        - conjunto de programas do computador em operação

    3. FIRMWARE
        - programas especiais, permanentes no hardware


* Tipos de Sistemas Operacionais:
    1. Bath
    2. De rede
    3. Distribuido
    4. Multiusuário
    5. Desktop **
    6. Servidor
    7. Embarcado
    8. Tempo real


## Objetivos de um Sistema Operacional
- Recursos do sistema
- Gerenciamento dos recursos existentes
- Integridade e segurança dos dados
- Interface que possibilita a utilização pelos usuários

* Inicialmente não havia o conceito de _programa armazenado_. Um computador era projetado para uma única determinada função

## Arquitetura de um computador
* Arquitetura capaz de armazenar programas (Arquitetura de Von Neumann):

    1. Unidade de Processamento Central (CPU)
        - Registradores
        - Unidade de controle (UC)
        - Unidade lógica aritmética (ULA)
        - Controlador de programa (PC)

    2. Sistema de memória principal

    3. Sistema de entrada e saída
        1. O __PC__ é utilizado pela __UC__ para determinar a próxima interação
        2. A __UC__ busca a instrução do programa na memória principal
        3. A decodificação será feita para a __ULA__ interpretar
        4. Os dados são transferidos da memória e alocados nos __Registradores__ da CPU
        5. A __ULA__ executa a instrução e coloca os resultados na __Memória__ ou nos __Registradores__


* Gargalo de Von Neumann
    - Atrofiamento no canal de transmissão entre a CPU e a memória, pois essa não consegue trabalhar em frequências tão altas quanto a CPU]

* Os computadores atuais utilizam arquiteturas __derivadas__ da de Von Neumann
    - Separação entre HD e memoria RAM, por exemplo, é uma mudança.

## Sincronização e comunicação de processos
* Década de 1960 - Primeiros Sistemas operacionais multiprogramados
    - Programação concorrente: O S.O precisa controlar a execução parelela de programas

### Comunicação por compartilhamento de memória
- É um mecanismo de comunicação entre processos que usa uma área da memória, um buffer, compartilhado entre os vários processos
- É preciso um mecanismo de controle para evitar conflitos de concorrência


### Soluções de hardware
* Processamento de Transações
    * Operações atômicas
        - Não podem ser interrompidas
        - Não é possivel ver as "partes", somente seu efeito final



### Mecanismos de sincronização
- Fundamenta-se na utilização de operações atômicas para garantir o funcionamento correto de processos concorrentes

         _________________       _____________       _______________
        |                 |     |             |     |               |
        |PROCESSO GRAVADOR|<----|SINCRONIZAÇÃO|---->|PROCESSO LEITOR|
        |_________________|     |_____________|     |_______________|
            |                                                   |
            |                      ________                     |
            |--------DADOS------->| BUFFER |<--------DADOS------|
                                  |________|

* Esse processo é importante para garantir a integridade e confiabilidade na execução de aplicações concorrentes

## Gerência de memória

1. Controle das partes da memória que estão sendo usadas e quais não
2. Alocar e liberar espaços em memória
3. Controle do swapping de informação

    - Hierarquia de memória
    - Memórias voláteis e não voláteis

### Unidade de Gerência de memória (Memory Management Unit)
- Faz o mapeamento entre os endereços lógicos (memória virtual) e os endereços físicos (memória RAM)

         _____                 _____                _________
        |     |   Endereço    |     |   Endereço   |         |
        | CPU |--- Lógico --->| MMU |--- Físico -->| Memória |
        |_____|               |_____|              |_________|

## Multiprogramação
- Existem dois tipos de gerenciadores de memória:
    1. os que permitem trocas de processos entre a memoria principal e o disco
    2. aquelas que não permitem

### Monoprogramação sem troca de processos ou paginção
* A memória é compartilhada entre o S.O e o programa executado
* Somente um programa de usuário é carregado na memória e executado por vez

### Multiprogramação com partes fixas
* Mais de um processo ao mesmo tempo
* Partiçoes fixas: "restante" da memória é perdido (__Fragmentação interna__)
* __Fragmentação externa__

### Multiprogramação com partições variáveis
* O tamanho dos processos e das partições variam dinamicamente
* Evita desperdícios de memória
* A gerência de espaços é mais dificil: 
    - First-fit
    - Best-fit
    - Worst-fit
    - Next-fit
* Podem deixar "buracos" na memória
    - Compactação
        - O processo é lento, por isso não deve ser executado com muita frequência