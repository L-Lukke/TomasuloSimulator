# TomasuloSimulator

## Structs:

### Gerais:

#### struct Register: Define uma estrutura para um registro com um nome e um valor. O operador de igualdade (==) é sobrecarregado para verificar se dois registros são iguais com base no nome. vector<Register> regs; e vector<Register> memory;: São vetores que armazenam registros e memória, respectivamente.

#### struct InstructionStatus: Mantém o status de uma instrução, como quando foi emitida (issue), quando começou a execução (executionStart), quando terminou a execução (executionComplete), quando escreveu de volta (writeBack) e quantos ciclos de execução restam (executionCyclesRemaining).

#### struct InstructionType: Define constantes para tipos de instrução, como multiplicação, subtração, adição, divisão, carga, desvio condicional e armazenamento.

#### struct ReservationStationType e struct LoadStoreBufferType: Definem tipos de unidades funcionais para estações de reserva e buffers de carga/armazenamento.

#### struct Instruction: Representa uma instrução com seu tipo, registradores envolvidos, deslocamento imediato (usado apenas para instruções do tipo I) e status de execução.

#### struct RegisterStatus: Mantém o status de um registro, indicando qual unidade está escrevendo nele.

#### struct ReservationStation: Representa uma estação de reserva, que pode ser ocupada (isBusy), contém informações sobre o tipo de instrução, valores dos operandos (Vj, Vk), dependências entre instruções (Qj, Qk) e um ponteiro para a instrução sendo executada.

#### struct LoadStoreBuffer: Modela um buffer de carga ou armazenamento, indicando seu estado (isBusy), endereço, unidade funcional (fu) e uma instrução associada.

### Struct Tomasulo:

#### Método execute: A função execute() simula como as instruções são processadas em um chip de computador usando o método de Tomasulo. Ela verifica se as instruções podem ser executadas e avança seu progresso em diferentes áreas do chip, como buffers de carga, armazenamento e unidades de cálculo. Ela também lida com problemas como dependência de dados e atualiza o estado das instruções à medida que são executadas ou completadas. Essencialmente, é como um "motor" que move as instruções pelo chip, controlando sua execução e garantindo que tudo ocorra corretamente.

#### Método issueInstruction: A função issueInstruction() emite diferentes tipos de instruções (LOAD, STORE, ADD, SUB, MULT, DIV) em um simulador Tomasulo. Ela verifica a disponibilidade de buffers e estações de reserva para cada tipo de instrução, configura os buffers com as instruções emitidas, seus endereços e informações de execução, além de lidar com possíveis dependências de dados (RAW hazards). Se não houver recursos disponíveis, registra um aviso de hazard estrutural e retorna -1, caso contrário, retorna 0 indicando sucesso na emissão da instrução.

#### Método writeBack: A função writeBack() é responsável por escrever de volta os resultados das instruções executadas. Ela percorre os buffers de carga, armazenamento, soma, subtração, multiplicação e divisão, verificando se as instruções estão prontas para serem escritas de volta na memória ou nos registradores. Assim que uma instrução é completada, ela atualiza os valores correspondentes e libera os recursos utilizados, preparando-se para a próxima etapa do ciclo de execução.

#### Método print: A função print() exibe detalhes sobre as instruções, buffers de carga/armazenamento, estações de reserva e o status dos registradores. Ela mostra informações como tipo de instrução, registradores envolvidos, estado de execução e escrita de volta. Também fornece uma representação visual do estado atual do sistema de simulação de processamento.

#### Método Simulate: A função Simulate() executa o ciclo de simulação do processador. Ela itera continuamente através dos estágios de execução de instruções: emissão, execução e escrita de volta. Durante cada ciclo, exibe o número do ciclo atual, atualiza e mostra o estado do sistema após cada etapa (emissão, execução e escrita de volta) usando a função print().

## Main: 

Na main() o programa realiza configurações iniciais para formatação da tela e executa a simulação do algoritmo de Tomasulo. Ele define o tamanho da fonte, o estilo da fonte, a posição do cursor na tela e inicia a simulação da execução do algoritmo de Tomasulo, carregando os dados de um arquivo (source.txt, mas outro pode ser passado por parâmetro) e exibe os resultados no console. Ao final, aguarda um pressionamento de tecla antes de encerrar o programa.
