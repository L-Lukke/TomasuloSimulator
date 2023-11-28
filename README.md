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

### Tomasulo:

####
