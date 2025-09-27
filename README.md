Terceiro/Quarto desafio do curso Code Girl da Dio.

 ## Introdução
  AWS CloudFormation é um serviço da Amazon que oferece uma maneira fácil e eficaz de criar e gerenciar uma infraestrutura de nuvem. Ele permite que você utilize arquivos de modelo (templates) escritos em YAML ou JSON para   descrever e provisionar todos os recursos da AWS que você precisa, como instâncias do EC2, buckets do S3, funções do Lambda, e muitos outros serviços. 

## Como Funciona o CloudFormation
• Modelagem de Infraestrutura: Você define sua infraestrutura em um arquivo de modelo. Este arquivo contém a descrição de todos os recursos que você deseja criar, suas configurações, as dependências entre eles e como devem ser integrados.

• Stacks: Quando você cria uma pilha (stack) a partir de um modelo, o CloudFormation gera automaticamente os recursos definidos. Todos os recursos podem ser gerenciados como uma única unidade (stack), facilitando a manutenção e atualização.

• Gerenciamento de Mudanças: O CloudFormation também permite que você faça atualizações na sua infraestrutura de maneira controlada, sem causar tempo de inatividade. Quando você altera o template e atualização, ele garante que as mudanças sejam aplicadas corretamente.

• Rollback Automático: Se algo der errado durante a criação ou atualização da stack, o CloudFormation pode reverter automaticamente as alterações para o estado anterior.

## Onde Aplicar o CloudFormation
• Provisionamento de Infraestrutura: Implantar um conjunto de recursos AWS de forma consistente e reproduzível. Por exemplo, criar um ambiente de desenvolvimento com múltiplas instâncias EC2 e bancos de dados RDS.

• Desdobramentos em Múltiplas Regiões: Gerenciar a infraestrutura em várias regiões AWS de maneira centralizada, simplificando a replicação de sistemas em várias localizações geográficas.

• Infraestrutura como Código (IaC): Aplicar princípios de IaC ao criar, modificar e excluir recursos AWS com segurança, rastreando mudanças na infraestrutura ao longo do tempo.
 _____________________________________________________________________________________________________________________
  ### Requisitos
  1. Faça login no seu Conta da AWS.
  2. Escolha o modelo AWS CloudFormation e a região mais próxima de você. (Poderá visualizar os modelos aqui: https://docs.aws.amazon.com/pt_br/forecast/latest/dg/tutorial-cloudformation.html)
  _____________________________________________________________________________________________________________________
  ### Workflow Design
  Um exemplo de criação de três instâncias ec2 t3-micro em 3 regiões diferentes e utilize o code deploy para realizar o deployment de uma api em ambas as três.
  _____________________________________________________________________________________________________________________ 
  ### Anexos
  code.md contendo o código do template para a criação do workflow.
