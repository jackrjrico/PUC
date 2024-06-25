# Objetivo de deste projeto é atender o trabalho final da disciplina de Banco de dados da Pós graduação da PUC

# Relatório de Projeto de Sistema de Gerenciamento de Estoque para Supermercados

# Introdução
Este relatório descreve o projeto de um sistema de gerenciamento de estoque para uma cadeia de supermercados com filiais em diferentes cidades. O sistema precisa ser escalável e eficiente, lidando com milhões de registros de produtos, permitindo consultas rápidas e atualizações de inventário. O foco principal é a estratégia de particionamento de dados para garantir desempenho e escalabilidade.
Estratégia de Particionamento

# Considerando os requisitos apresentados, a estratégia escolhida será a de particionamento horizontal (Sharding), seguem as justificativas para a escolha:

- Escalabilidade: Como cada shard pode ser colocado em um servidor diferente, adicionar novas filiais simplesmente envolve adicionar novos shards. Isso permite que o sistema escale horizontalmente com pouca reconfiguração.

- Desempenho: Distribuir os dados entre vários shards reduz a carga em cada servidor individual, melhorando o desempenho geral das consultas e atualizações.

- Localidade dos Dados: Filiais em diferentes cidades provavelmente operam de maneira independente. Particionar os dados por cidade (horizontalmente) significa que a maioria das consultas e atualizações será local a um shard específico, melhorando a eficiência.

- Isolamento de Falhas: Problemas em um shard não afetam outros shards. Isso significa que uma falha em uma filial (cidade) não comprometerá o sistema inteiro.
Implementação Detalhada

Muitos sistemas não precisam de sharding inicialmente, sendo melhor implementá-lo apenas quando a escalabilidade vertical não é mais suficiente.  
Portanto, para uma cadeia de supermercados que terá um volume grande de dados, a melhor estratégia é a de particionamento horizontal (sharding). 
Sem a estratégia de particionamento, o banco de dados pode rapidamente ficar sobrecarregado, tornando alguns nós ineficientes. 
O sharding facilita o gerenciamento das informações, garantindo eficiência de desempenho e escalabilidade contínua.

# Ferramentas utilizadas: 
Para realizar a tarefa, foram usadas as seguintes ferramentas: ChatGPT para criação de um script de uma base de exemplo, Python com IDE VSCode para 
execução do Script de criação do arquivo json, Docker contendo o ambiente dentro de um contêiner e MongoDB para leitura e gravação dos dados do 
database(trabalho_final_bd) e Collection (supermercado). A utilização dos mesmos, foi escolhida visando o desafio e facilidade e eficácia de uso.

# Criação do Cluster mongo replicante e particionado: Para essa tarefa foi usado o método abaixo:

# Criação de três tipos de serviços:

Roteadores: responsáveis por receberem as requisições de leitura e escrita e redirecionar para a partição correta.

Config Servers: armazenam os metadados das partições (shards). Os metadados incluem a lista de chunks de cada shard e os intervalos que definem os chunks.
  
Shards: são os nós responsáveis pelo armazenamento dos dados. Cada shard fica responsável por um subconjunto dos dados do banco.












