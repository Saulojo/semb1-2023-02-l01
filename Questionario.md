# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
Compilação cruzada é o processo de compilação de um programa para execução em uma plataforma de destino diferente daquela na qual o processo de compilação foi executado. Em outras palavras, você compila o código-fonte em um sistema para que ele possa ser executado em uma arquitetura ou ambiente diferente.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
STM32 é baseado na arquitetura ARM Cortex-M e possui uma estrutura de inicialização padronizada. O código de inicialização é responsável por configurar o ambiente de execução do programa principal que é carregado no microcontrolador.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:
Makefile é um arquivo de configuração usado em projetos de software para automatizar o processo de compilação e construção. Ele contém regras e diretrizes sobre como compilar o código-fonte de um programa, quais arquivos são necessários e como vinculá-los para formar o arquivo executável final.

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
Análise de dependência:
Make examina o Makefile para identificar regras de construção e dependências entre diferentes arquivos no projeto.
Comparação de carimbo de data/hora:
Verifique os carimbos de data/hora dos arquivos de origem e de destino para determinar se alguma alteração foi feita desde a última compilação.
Execute as ações necessárias:
Se o arquivo fonte for modificado ou o arquivo objeto estiver faltando, make executará as operações especificadas no Makefile para compilar o código fonte correspondente.
Isso geralmente envolve invocar o compilador para gerar arquivos-objeto a partir de arquivos de origem.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
Depois de compilar todos os arquivos de origem relevantes, verifique se uma etapa de vinculação é necessária para criar o arquivo executável final.
Se necessário, faça chamadas ao vinculador para vincular os arquivos objeto e criar um arquivo executável.
Execução do aplicativo:
Se todos os passos anteriores forem concluídos com sucesso, o make pode optar por executar o programa recém-compilado.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
alvo: dependências
    comandos


#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
As dependências em um Makefile são pré-requisitos para uma definição de destino e representam arquivos ou outros destinos necessários para construir. Eles determinam se o destino precisa ser reconstruído verificando modificações nos arquivos listados. A ordem das dependências é importante, garanta compilações sequenciais.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
As regras no Makefile determinam como o destino é construído. Regras explícitas são definidas pelo desenvolvedor e possuem objetivos, dependências e comandos explícitos.
As regras implícitas, por outro lado, são predefinidas por make para tarefas comuns. Por exemplo, make possui regras implícitas para compilar automaticamente arquivos C

## 4. Sobre a arquitetura **ARM Cortex-M** responda:
O conjunto de instruções Thumb é uma extensão da arquitetura ARM projetada para fornecer instruções mais compactas. Estas instruções são mais curtas, economizando espaço de memória, otimizando a eficiência do cache e reduzindo o consumo de energia, especialmente em dispositivos alimentados por bateria. A alternância dinâmica entre os modos Thumb e ARM permite que o processador ARM selecione o conjunto de instruções mais eficiente com base no código que está sendo executado. Esta flexibilidade é muito valiosa para otimizar diferentes partes do programa. Os processadores ARM podem alternar dinamicamente entre os modos, e os desenvolvedores podem escolher instruções Thumb e mudar para instruções ARM para economizar espaço em peças que exigem maior desempenho. A combinação de Thumb e ARM fornece eficiência de código e benefícios de desempenho em uma variedade de aplicações.

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
A principal diferença entre as arquiteturas de carregamento/armazenamento e registro/registro ARM é a maneira como elas lidam com operações de carregamento e armazenamento. Em uma arquitetura load/store, apenas instruções load e store têm acesso direto à memória, enquanto operações aritméticas só podem ser realizadas em registradores. Por outro lado, em uma arquitetura registrador/registro, as operações de carga e armazenamento podem ser executadas diretamente nos registradores, simplificando algumas operações, mas potencialmente aumentando a complexidade do hardware. A abordagem carregar/armazenar é comum em arquiteturas RISC como ARM, onde a simplicidade e a eficiência das instruções são priorizadas. A escolha entre esses métodos depende dos objetivos e requisitos específicos do projeto do processador e da aplicação.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
Os processadores ARM Cortex-M facilitam a implementação de sistemas RTOS através de recursos como níveis de acesso de execução (níveis de privilégio) e modos de operação. Os níveis de acesso incluem o modo privilegiado, que permite acesso total aos recursos do sistema, e o modo não privilegiado, que restringe operações críticas para isolar tarefas. Quanto aos modos operacionais, o modo thread é proeminente e é usado principalmente para executar tarefas normais, enquanto o modo manipulador é usado para lidar com exceções e falhas. O modo monitor fornece um ambiente seguro que é útil para operações críticas em sistemas RTOS. Esses recursos granulares fornecem controle e isolamento para criar sistemas em tempo real poderosos e responsivos com eficiência.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
Os processadores ARM Cortex-M possuem um sistema hierárquico de prioridades para lidar com exceções e interrupções. Essas exceções podem ser de diferentes tipos, como interrupções, exceções e traps. Essas exceções são como diferentes tipos de chamados que o processador precisa atender.


### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
Para organizar essas exceções, o processador utiliza uma estratégia de priorização em níveis. Isso significa que as exceções são agrupadas em categorias com diferentes prioridades. Vamos pensar nisso como diferentes filas de atendimento, onde cada fila tem uma prioridade diferente. Por exemplo, uma fila pode ser para eventos urgentes e outra para eventos menos críticos.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
 Os processadores ARM Cortex-M possuem um sistema hierárquico de prioridades para lidar com exceções e interrupções. Essas exceções podem ser de diferentes tipos, como interrupções, exceções e traps. Imagine que essas exceções são como diferentes tipos de chamados que o processador precisa atender.
 Para organizar essas exceções, o processador utiliza uma estratégia de priorização em níveis. Isso significa que as exceções são agrupadas em categorias com diferentes prioridades. Vamos pensar nisso como diferentes filas de atendimento, onde cada fila tem uma prioridade diferente. Por exemplo, uma fila pode ser para eventos urgentes e outra para eventos menos críticos.
 Além disso, o processador também permite uma granularidade adicional na definição de prioridades através de uma abordagem chamada group priority e sub-priority. Isso significa que dentro de cada grupo de exceções, é possível fazer ajustes específicos de prioridade. Podemos comparar isso a ter diferentes níveis de urgência dentro de cada fila de atendimento. Por exemplo, dentro da fila de eventos urgentes, podemos ter eventos extremamente críticos e outros um pouco menos.
 O mecanismo de priorização funciona através de números associados a cada exceção. Esses números indicam a prioridade de cada exceção. O processador seleciona a exceção de maior prioridade pendente para ser executada. É como o processador escolhendo o chamado mais urgente para atender.
Essa estratégia de priorização é extremamente importante em sistemas em tempo real, onde é essencial ter respostas rápidas a eventos críticos. Pense em um sistema de segurança que precisa detectar um movimento suspeito rapidamente. Nesse caso, a priorização das exceções garante que o processador atenda primeiro as exceções mais urgentes, garantindo o desempenho e a confiabilidade do sistema embarcado.

### (f) Qual a finalidade do **LR** (***Link Register***)?
 O registrador LR (Link Register) no ARM é uma parte importante do processador que armazena o endereço de retorno de uma sub-rotina. Podemos pensar nele como uma espécie de "bilhete de volta" que nos permite retornar ao ponto de onde viemos após a execução de uma sub-rotina.
 Em resumo, o registrador LR é essencial para o controle do fluxo de execução em programas ARM. Ele armazena o endereço de retorno de uma sub-rotina e permite que o programa retorne de forma ordenada após a sua execução. 

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
 O Program Status Register (PSR) é um registrador muito importante nos processadores ARM, como o Cortex-M. Ele armazena informações cruciais sobre o estado do processador durante a execução de instruções. Podemos pensar nele como uma espécie de "diário" do processador, onde ele anota várias coisas que estão acontecendo.
 O PSR possui diferentes campos que nos dizem algumas coisas interessantes. Por exemplo, ele nos indica em que modo o processador está executando as instruções. É como se fosse um sinal dizendo se o processador está no modo normal, no modo de interrupção ou até mesmo no modo privilegiado.
 Em alguns casos, o PSR também pode nos dizer qual é a prioridade de exceção. Isso é importante quando o processador está lidando com várias exceções ao mesmo tempo e precisa decidir qual delas é mais importante.

### (h) O que é a tabela de vetores de interrupção?
 A tabela de vetores de interrupção é como um catálogo de endereços que os sistemas embarcados utilizam para saber qual rotina executar quando ocorre uma interrupção. Podemos pensar nessa tabela como uma lista de telefones, onde cada número está associado a uma pessoa específica. No caso da tabela de vetores de interrupção, cada entrada está associada a um tipo específico de interrupção e contém o endereço da rotina de tratamento correspondente.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
O NVIC é capaz de priorizar as interrupções com base em sua importância. Além disso, o NVIC também permite que interrupções mais críticas interrompam outras menos importantes.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
