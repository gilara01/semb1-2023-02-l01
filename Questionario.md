# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
 É o processo de compilar código-fonte em um sistema de desenvolvimento diferente daquele onde o código será executado.
 A compilação cruzada é importante porque permite que os desenvolvedores criem software para sistemas embarcados sem a necessidade de configurar um ambiente de desenvolvimento complexo diretamente no hardware de destino.
 Ela torna possível desenvolver e testar software em um ambiente mais conveniente e poderoso, como um PC, enquanto se produz binários executáveis que podem ser implantados em sistemas embarcados ou outros dispositivos que possuem recursos limitados de processamento e armazenamento. Isso simplifica o processo de desenvolvimento e distribuição de software para uma ampla variedade de plataformas e arquiteturas.

 
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
Inicialização do Hardware: O código de inicialização configura e inicializa o hardware do sistema, incluindo processadores, periféricos, memória, temporizadores e outras interfaces. Isso pode envolver a configuração de registradores, inicialização de temporizadores, configuração de pinos GPIO e outras operações para garantir que o hardware esteja em um estado conhecido e funcional.
Preparação do Ambiente de Execução: O código de inicialização estabelece o ambiente de execução para o código do aplicativo principal. Isso pode incluir a configuração da pilha (stack) e do heap, inicialização de variáveis estáticas, definição de vetores de interrupção, configuração de modos de operação do processador e outras operações para garantir que o código do aplicativo possa ser executado de forma adequada.
Chamada do Ponto de Entrada do Aplicativo: Após a inicialização do hardware e a preparação do ambiente de execução, o código de inicialização geralmente chama o ponto de entrada do aplicativo principal. Isso pode ser a função main() em linguagens como C ou a rotina de inicialização principal em linguagens de baixo nível como assembly. A partir desse ponto, o controle é transferido para o código do aplicativo principal e a execução do programa continua normalmente.
O código de inicialização é responsável por preparar o ambiente de execução do sistema embarcado, configurando o hardware, estabelecendo configurações de sistema e inicializando a memória, para que o software principal possa ser executado corretamente.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
Um Makefile é um arquivo de texto especial usado em sistemas Linux para automatizar o processo de compilação e construção de software.Ele contém instruções e regras que especificam como os diferentes componentes de um projeto devem ser compilados e como devem ser construídos os artefatos finais, como executáveis, bibliotecas ou outros recursos.É especialmente útil em projetos grandes, onde muitos arquivos estão envolvidos e as dependências entre eles podem ser complicadas. Ele ajuda a evitar a necessidade de recompilar todos os arquivos sempre que algo é alterado, economizando tempo e garantindo que apenas os arquivos afetados sejam recompilados. Isso torna o processo de compilação mais eficiente e fácil de gerenciar.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
Leitura do Makefile: O make começa lendo o arquivo Makefile no diretório atual. Este arquivo contém as regras e instruções para compilar o programa.
Análise de dependências: O make identifica as dependências entre os diferentes arquivos do projeto, incluindo arquivos de código-fonte, cabeçalhos e outros recursos necessários.
Determinação das metas: Ele verifica qual meta (ou alvo) foi especificada pelo usuário na linha de comando. Se nenhum alvo for especificado, o make usa o primeiro alvo encontrado no Makefile como padrão.
Verificação de dependências: O make verifica se algum dos arquivos-fonte ou dependências foi alterado desde a última compilação. Ele compara as datas de modificação dos arquivos para determinar quais partes do programa precisam ser reconstruídas.
Execução de comandos de compilação: Com base nas dependências e regras definidas no Makefile, o make executa os comandos necessários para compilar os arquivos fonte modificados. Isso geralmente envolve invocar um compilador (como GCC para C/C++), gerando arquivos objeto correspondentes.
Vinculação dos arquivos objeto: Após compilar todos os arquivos fonte relevantes, o make os vincula juntos para formar o executável final, se aplicável. Ele também pode realizar outras etapas, como a criação de bibliotecas compartilhadas ou executáveis para o programa.
Conclusão e mensagens de status: O make exibe mensagens de status indicando se a compilação foi bem-sucedida ou se ocorreram erros durante o processo. Ele também pode fornecer informações sobre as etapas concluídas e os arquivos gerados.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
Precisamos especificar o nome do target seguido por um dois pontos (:), e em seguida, as instruções associadas a esse target. Tipo
target: dependências
    comandos

target: é o nome target que você está definindo.
dependências: são os arquivos ou outros targets de que o target atual depende. Se as dependências forem modificadas, o target será reconstruído.
comandos: são os comandos necessários para construir o target. Eles devem ser indentados usando uma tabulação (não espaços).

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
As dependências são fundamentais para o funcionamento eficiente do Makefile, pois permitem que o make determine automaticamente quais partes do projeto precisam ser reconstruídas com base nas modificações nos arquivos fonte ou em outros targets. 
Isso ajuda a evitar a reconstrução desnecessária de partes do projeto e a otimizar o processo de compilação.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
Regras Implícitas: As regras implícitas são regras padrão pré-definidas pelo Makefile para compilar certos tipos de arquivos fonte em arquivos objeto. Por exemplo, se você tem um arquivo C chamado programa.c, o Makefile pode incluir uma regra implícita que especifica como compilar programa.c em programa.o. Essas regras são implícitas porque o Makefile as utiliza automaticamente sem que você precise defini-las explicitamente.

Regras Explícitas: As regras explícitas são regras definidas explicitamente pelo usuário no Makefile para compilar arquivos fonte específicos em arquivos objeto ou executáveis. Elas oferecem mais controle sobre o processo de compilação, permitindo que você especifique as dependências, os comandos de compilação e quaisquer outras etapas necessárias para construir o software.
Em resumo, as regras no Makefile especificam como os arquivos fonte devem ser compilados e construídos. As regras implícitas são regras padrão pré-definidas pelo Makefile, enquanto as regras explícitas são regras definidas explicitamente pelo usuário para fornecer mais controle sobre o processo de compilação.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
Principais características do conjunto de instruções Thumb:
Instruções de 16 bits: No Thumb, as instruções são codificadas em 16 bits, em comparação com as instruções de 32 bits no conjunto de instruções ARM tradicional. Isso resulta em um código menor, o que é benéfico para sistemas com limitações de memória.
Maior densidade de código: Devido ao seu formato de instrução compacto, o Thumb permite que mais instruções sejam armazenadas na memória, o que resulta em um melhor aproveitamento do cache e menos buscas na memória principal.
Consumo de energia reduzido: Como o tamanho do código é menor, o processador consome menos energia para buscar e decodificar instruções, o que é vantajoso para dispositivos alimentados por bateria ou com restrições de energia.
Compatibilidade com instruções ARM: O conjunto de instruções Thumb opera em conjunto com o conjunto de instruções ARM. Isso significa que um processador ARM Cortex-M pode executar tanto instruções Thumb quanto instruções ARM. Os programadores podem escolher entre os dois conjuntos de instruções, dependendo dos requisitos de tamanho de código e desempenho de seus aplicativos.

O conjunto de instruções em conjunto:Os processadores ARM Cortex-M suportam tanto o conjunto de instruções Thumb quanto o conjunto de instruções ARM tradicional. Isso permite que os programadores escolham entre os dois conjuntos de instruções, dependendo das necessidades específicas de seus aplicativos.
Quando o processador está no modo Thumb, ele executa instruções Thumb de 16 bits. Quando está no modo ARM, ele executa instruções ARM de 32 bits. O processador pode alternar entre esses modos de acordo com as instruções encontradas no código do programa.
Essa capacidade de alternar entre os conjuntos de instruções oferece flexibilidade aos desenvolvedores para otimizar o tamanho do código e o consumo de energia de seus aplicativos, sem sacrificar o desempenho.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
Principais diferenças:
Acesso à memória: Na arquitetura Load/Store, todas as operações de acesso à memória são realizadas por instruções específicas de carga e armazenamento. Na arquitetura Register/Register, operações aritméticas e lógicas podem ser realizadas diretamente entre registradores, sem acessar a memória.
Instruções: Na arquitetura Load/Store, instruções específicas ("load" e "store") são usadas para transferir dados entre registradores e memória. Na arquitetura Register/Register, as instruções aritméticas e lógicas operam diretamente entre registradores.
Complexidade e desempenho: A arquitetura Load/Store tende a ser mais simples em termos de instruções, mas pode exigir mais instruções para realizar operações que envolvem acesso à memória. A arquitetura Register/Register pode ser mais eficiente em termos de desempenho em certos casos, pois pode evitar acessos à memória para operações comuns de aritmética e lógica.
Em resumo, as arquiteturas Load/Store e Register/Register representam abordagens diferentes para acessar a memória e operar com dados em instruções de processador, cada uma com suas próprias características e trade-offs em termos de complexidade, desempenho e eficiência.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
Níveis de Acesso de Execução de Código:
Os processadores ARM Cortex-M oferecem dois níveis de acesso para execução de código:
Privilegiado (Privileged):
No modo privilegiado, o processador tem acesso total ao sistema e pode executar todas as instruções.
O código em modo privilegiado tem acesso a todas as áreas de memória e pode executar instruções privilegiadas, como operações de acesso direto à memória (DMA), instruções de alteração de contexto, entre outras.
O código em modo privilegiado geralmente inclui o kernel do sistema operacional (RTOS) e os drivers de dispositivo, que precisam de acesso direto ao hardware e a recursos do sistema.
Não Privilegiado (Unprivileged):
No modo não privilegiado, o processador tem acesso restrito e só pode executar um subconjunto limitado de instruções.
O código em modo não privilegiado tem acesso restrito a certas áreas de memória e não pode executar instruções privilegiadas que afetam o funcionamento do sistema.
O código de aplicativo típico é executado em modo não privilegiado, garantindo que ele não possa comprometer a integridade do sistema.
Modos de Operação:
Os processadores ARM Cortex-M suportam diferentes modos de operação, que determinam o conjunto de instruções disponíveis e o comportamento do processador. Os principais modos de operação incluem:
Modo de Thread Principal (Main Thread Mode):
Este é o modo de operação principal do processador quando ele é ligado.
No modo de thread principal, o processador executa o código normal do usuário ou do kernel do sistema operacional.
Modo de Handler de Exceção (Exception Handler Mode):
Este modo é ativado quando ocorre uma exceção ou interrupção.
No modo de handler de exceção, o processador muda temporariamente para lidar com a exceção, interrompendo a execução normal do código.
Os handlers de exceção são responsáveis por tratar eventos como interrupções externas, falhas de memória e exceções de software.
Modo de Privilegiado (Privileged Mode):
Este modo é reservado para o código em modo privilegiado, como o kernel do sistema operacional (RTOS).
No modo privilegiado, o processador tem acesso total ao sistema e pode executar instruções privilegiadas.
Modo de Thread Específico (Handler Thread Mode):
Este modo é semelhante ao modo de thread principal, mas é usado para threads específicas que precisam de acesso privilegiado.
Ele é usado principalmente para lidar com tarefas críticas do sistema que exigem acesso direto ao hardware ou a recursos privilegiados.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
Tipos de Exceção:
Exceções Síncronas: São eventos que ocorrem como parte da execução normal do código, como instruções privilegiadas, erros de memória e divisão por zero.
Interrupções Externas: São sinais externos ao processador que solicitam atenção, como interrupções de hardware, temporizadores ou periféricos.
As exceções e interrupções no processador ARM Cortex-M são priorizadas em níveis diferentes, o que permite que o processador lide com eventos críticos primeiro. A priorização ocorre por meio de um sistema de prioridade configurável, que pode ser configurado para fornecer prioridades diferentes para diferentes tipos de exceções e interrupções.
Estratégia de Prioridade:
Group Priority (Prioridade de Grupo):
As exceções e interrupções são agrupadas em grupos de prioridade.
Cada grupo de prioridade tem sua própria prioridade de grupo, que é usada para determinar a prioridade relativa das exceções e interrupções dentro desse grupo.
Sub-Priority (Subprioridade):
Dentro de cada grupo de prioridade, as exceções e interrupções são priorizadas com base em sua subprioridade.
A subprioridade é usada para resolver conflitos de prioridade entre exceções e interrupções do mesmo grupo de prioridade.
Quando várias exceções ou interrupções ocorrem simultaneamente, o processador ARM Cortex-M usa o conceito de prioridade de grupo e subprioridade para determinar qual evento deve ser tratado primeiro. Isso garante que exceções e interrupções críticas sejam tratadas rapidamente e de forma confiável, mesmo em situações de alta carga de trabalho.


### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
CPSR (Current Program Status Register):
O CPSR é um registrador de estado que contém informações sobre o estado atual do programa em execução. Algumas das informações armazenadas no CPSR incluem:
Modo de Execução: Indica o modo de execução atual do processador (modo de usuário, modo privilegiado, etc.).
Flags de Status: Armazena flags de status que refletem o resultado de operações aritméticas e lógicas, como o flag de zero (Z), o flag de carry (C), o flag de overflow (V) e outros.
Prioridade de Interrupção: Em alguns modelos de processadores ARM, bits no CPSR podem ser utilizados para armazenar a prioridade atual das interrupções, especialmente em contextos de interrupções aninhadas.
O CPSR é um registrador de apenas leitura em alguns contextos, mas em outros, como em certos modos privilegiados, ele pode ser acessado tanto para leitura quanto para escrita.

SPSR (Saved Program Status Register):
O SPSR é um registrador usado para salvar temporariamente o estado do CPSR durante a ocorrência de exceções ou interrupções. Quando uma exceção ou interrupção ocorre e o processador precisa mudar para um novo contexto de execução, ele salva o conteúdo do CPSR no SPSR antes de alterar o CPSR para um novo estado relacionado à exceção.
A principal diferença entre o CPSR e o SPSR é que o CPSR contém o estado atual do programa em execução, enquanto o SPSR é usado para salvar temporariamente esse estado durante a ocorrência de exceções ou interrupções. O SPSR é usado para garantir que, quando a execução retornar ao contexto original após a exceção ou interrupção, o programa possa retomar exatamente de onde parou, mantendo seu estado original.

### (f) Qual a finalidade do **LR** (***Link Register***)?
O registrador LR (Link Register), também conhecido como registrador de link, é um registrador especial encontrado em processadores ARM, incluindo os da família Cortex-M. A finalidade principal do registrador LR é armazenar o endereço de retorno para chamadas de sub-rotina ou funções.
Quando uma função ou sub-rotina é chamada, o endereço de retorno, que é o endereço da próxima instrução a ser executada após a função ou sub-rotina, é armazenado no registrador LR. Isso permite que o programa retorne à sequência de instruções correta após a conclusão da função ou sub-rotina.
Quando a função ou sub-rotina termina sua execução e está pronta para retornar ao código que a chamou, ela utiliza o endereço armazenado no registrador LR para realizar a operação de retorno (return). Isso permite que o fluxo de controle do programa seja retomado de onde foi interrompido, garantindo que a execução continue de forma sequencial e correta.
Em resumo, o LR é essencial para implementar o conceito de chamadas e retornos de função em linguagens de programação de baixo nível, como C e assembly.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
O PSR é um registrador especial encontrado em processadores ARM que é responsável por armazenar informações sobre o estado atual da execução do programa. Seu propósito é fornecer um conjunto de flags e informações que refletem o estado atual do processador durante a execução de instruções.
Alguns dos propósitos do Program Status Register (PSR) nos processadores ARM incluem:
Flags de Status: O PSR armazena flags de status que indicam o resultado de operações aritméticas e lógicas, como o flag de zero (Z) que indica se o resultado de uma operação é zero, o flag de carry (C) que indica se houve uma operação de carry, o flag de overflow (V) que indica se houve um overflow em uma operação aritmética, entre outros.
Modo de Execução: O PSR contém informações sobre o modo de execução atual do processador, como modo de usuário, modo privilegiado (modo supervisor), modo de interrupção, entre outros. Esses modos determinam as permissões de acesso e o nível de privilégio do código em execução.
Estado de Interrupção: O PSR pode incluir informações sobre o estado de interrupção do processador, indicando se as interrupções estão habilitadas ou desabilitadas.
Controle de Execução de Instruções: O PSR pode conter informações sobre o controle de execução de instruções, como a habilitação ou desabilitação de execução de instruções privilegiadas.
Em resumo, o Program Status Register (PSR) nos processadores ARM é um registrador importante que armazena informações essenciais sobre o estado atual da execução do programa, incluindo flags de status, modo de execução, estado de interrupção e controle de execução de instruções. Ele desempenha um papel fundamental na execução correta e eficiente de programas em processadores ARM.

### (h) O que é a tabela de vetores de interrupção?
A tabela de vetores de interrupção é uma estrutura de dados usada em sistemas embarcados para gerenciar as interrupções e exceções que ocorrem no processador. É uma tabela na memória que contém endereços de entrada para as rotinas de tratamento de interrupção ou exceção correspondentes.
Quando uma interrupção ou exceção ocorre, o processador usa a tabela de vetores de interrupção para determinar qual rotina de tratamento deve ser executada em resposta ao evento. Cada entrada na tabela corresponde a um número de interrupção ou exceção específico e contém o endereço da rotina de tratamento associada.
Quando ocorre uma interrupção ou exceção, o processador consulta a tabela de vetores de interrupção para encontrar o endereço da rotina de tratamento correspondente. Em seguida, ele transfere o controle de execução para essa rotina, que é responsável por lidar com o evento de interrupção ou exceção.
A tabela de vetores de interrupção é uma parte fundamental do sistema de gerenciamento de interrupções em sistemas embarcados e é configurada durante a inicialização do sistema. Ela permite que o processador lide com eventos de interrupção e exceção de forma eficiente e previsível, garantindo um comportamento confiável do sistema.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
Funcionamento do NVIC:
Priorização de Interrupções: O NVIC permite que as interrupções sejam priorizadas com base em sua importância. Isso significa que interrupções mais críticas podem ser tratadas imediatamente, garantindo que o sistema responda adequadamente a eventos importantes.
Aninhamento de Interrupções: O NVIC suporta o aninhamento de interrupções, o que significa que uma interrupção pode ocorrer enquanto o processador está lidando com outra. Isso é essencial em sistemas de tempo real, onde eventos críticos podem ocorrer em momentos imprevisíveis.
Vetorização de Interrupções: O NVIC mantém uma tabela de vetores de interrupção, que contém endereços de memória das rotinas de tratamento de interrupção correspondentes. Isso permite que o processador saiba para onde direcionar o fluxo de execução quando uma interrupção ocorre.
Controle de Habilitação e Desabilitação: O NVIC permite que as interrupções sejam habilitadas ou desabilitadas conforme necessário. Isso é útil para evitar interrupções indesejadas ou para garantir que determinadas tarefas críticas sejam concluídas sem interrupção.
Utilidade em Aplicações de Tempo Real:
Resposta Rápida a Eventos: Em sistemas de tempo real, é crucial responder rapidamente a eventos externos ou internos. O NVIC garante que as interrupções sejam tratadas com eficiência e priorizadas adequadamente, garantindo uma resposta rápida a eventos críticos.
Gestão de Tarefas Críticas: Em muitas aplicações de tempo real, há tarefas críticas que devem ser concluídas dentro de prazos específicos. O NVIC permite que essas tarefas sejam tratadas como interrupções prioritárias, garantindo que sejam concluídas no momento certo, independentemente de outras atividades em andamento.
Previsibilidade do Sistema: O NVIC ajuda a garantir a previsibilidade do sistema, garantindo que interrupções importantes sejam tratadas no momento certo e que o sistema seja capaz de lidar com eventos imprevisíveis de forma eficiente e controlada.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 
O mecanismo de retorno de interrupção no Cortex-M é gerenciado pelo valor especial EXC_RETURN armazenado no registrador LR (Link Register) durante a ocorrência de uma interrupção. 
Armazenamento do EXC_RETURN:
Quando ocorre uma interrupção, o processador Cortex-M automaticamente salva o valor do registrador LR no momento da ocorrência da interrupção.
Esse valor do LR é substituído pelo valor especial EXC_RETURN, que é uma constante específica que indica ao processador que uma interrupção ocorreu e precisa retornar de forma apropriada após o tratamento da interrupção.
Recuperação do contexto após a interrupção:
Durante o tratamento da interrupção, o código de tratamento normalmente modifica o contexto do processador, como salvando e restaurando registradores e outros estados importantes.
Após o tratamento da interrupção, quando é hora de retornar à execução normal do programa, o processador usa o valor EXC_RETURN armazenado no LR para determinar como fazer o retorno.
O EXC_RETURN contém informações sobre o contexto antes da interrupção, incluindo o modo de operação (modo privilegiado ou não privilegiado), o estado de habilitação de interrupções e outras informações relevantes.
Com base no valor do EXC_RETURN, o processador restaura o contexto anterior ao estado da interrupção, incluindo a configuração do modo de operação e do estado de habilitação de interrupções.
Instrução de retorno específica:
Para realizar o retorno da interrupção de forma apropriada, o código de tratamento de interrupção normalmente usa a instrução BX LR, que instrui o processador a retornar ao endereço armazenado no registrador LR.
Quando o processador executa a instrução BX LR com o valor EXC_RETURN armazenado no LR, ele sabe que precisa restaurar o contexto anterior à interrupção com base nas informações contidas no EXC_RETURN.


### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 
Sobre o Cortex-M3:
Tempo de Resposta:
No Cortex-M3, o salvamento de contexto durante uma interrupção é realizado de maneira convencional e imediata.
Assim que uma interrupção ocorre, o processador interrompe a execução atual, salva o contexto atual do programa na pilha (incluindo registradores, status e endereço de retorno), e então começa a executar o código de tratamento de interrupção.
Uso da Pilha:
Durante o salvamento de contexto, o Cortex-M3 empilha os registros necessários e outras informações diretamente na pilha do programa.
Isso significa que a pilha precisa ser grande o suficiente para acomodar todo o contexto do programa durante as interrupções, o que pode aumentar o consumo de memória e tempo de execução.
No Cortex-M4F:
Tempo de Resposta:
No Cortex-M4F, que inclui uma unidade de ponto flutuante (FPU), o salvamento de contexto durante uma interrupção pode ser configurado para ocorrer de forma "lazy", o que pode melhorar o tempo de resposta.
Com o "lazy stacking", o salvamento de parte do contexto (especificamente os registradores do FPU) é adiado até que o código de tratamento de interrupção realmente precise acessar ou modificar esses registradores.
Uso da Pilha:
Durante a fase de "lazy stacking", apenas os registradores de propósito geral são empilhados imediatamente na pilha do programa, enquanto os registradores do FPU são salvos apenas quando necessário.
Isso reduz o uso da pilha e pode economizar memória, especialmente em casos em que o FPU não é utilizado durante todas as interrupções.
Lazy Stack:
O "lazy stack" é uma estratégia de otimização que adia o salvamento de parte do contexto durante a chegada de uma interrupção, empilhando apenas os registradores essenciais imediatamente e adiando o salvamento de outros registradores até que sejam necessários. No caso do Cortex-M4F, isso geralmente se refere aos registradores do FPU.
O "lazy stack" é configurado através do controle de configuração do NVIC (Nested Vectored Interrupt Controller) e pode ser habilitado ou desabilitado conforme necessário, dependendo dos requisitos de desempenho e consumo de memória da aplicação.
Em resumo, a principal diferença no salvamento de contexto durante a chegada de uma interrupção entre os processadores Cortex-M3 e Cortex-M4F está no uso do "lazy stack", que pode melhorar o tempo de resposta, reduzir o uso da pilha e economizar memória em aplicações que fazem uso do ponto flutuante.

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
