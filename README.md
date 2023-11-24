# lb_status.sh: Documentação de Uso

## Descrição

O script `lb_status.sh` é uma ferramenta de linha de comando projetada para verificar o estado de saúde de Load Balancers na Oracle Cloud Infrastructure (OCI). Ele oferece duas funcionalidades principais:

1. **Verificar o Estado do Load Balancer (check_lb_status)**: Esta função verifica o estado geral do Load Balancer, informando se está ativo e funcionando corretamente.
2. **Verificar a Saúde dos Backends (check_backend_health)**: Esta função fornece um relatório detalhado sobre a saúde de cada Backend Set e seus backends associados no Load Balancer.

Este script é útil para administradores de sistema e equipes de operações que precisam monitorar a saúde e o status dos Load Balancers na OCI.

## Pré-requisitos

- Oracle Cloud Infrastructure Command Line Interface (OCI CLI) deve estar instalada e configurada no seu sistema.
- Você deve ter o `jq` instalado, uma ferramenta de linha de comando para processar dados JSON.
- Acesso apropriado à OCI para consultar informações sobre Load Balancers.

## Como Usar

### Execução do Script

O script `lb_status.sh` pode ser executado a partir da linha de comando. Para usá-lo, você precisa fornecer dois parâmetros:

1. **OCID do Load Balancer**: O Oracle Cloud Identifier (OCID) do Load Balancer que você deseja verificar.
2. **Nome da Função**: Indica qual função você deseja executar - `check_lb_status` para verificar o estado do Load Balancer, `check_backend_health` para verificar a saúde dos Backends.

### Formato do Comando

```bash
./lb_status.sh <OCID_Load_Balancer> <Nome_da_Função>
```

Substitua `<OCID_Load_Balancer>` pelo OCID do seu Load Balancer e `<Nome_da_Função>` por `check_lb_status` ou `check_backend_health`, dependendo da verificação desejada.

### Exemplos

- Para verificar o estado do Load Balancer:
  ```bash
  ./lb_status.sh ocid1.loadbalancer.oc1... check_lb_status
  ```
- Para verificar a saúde dos Backends:
  ```bash
  ./lb_status.sh ocid1.loadbalancer.oc1... check_backend_health
  ```

### Interpretação dos Resultados

- **Verificação do Estado do Load Balancer (check_lb_status)**:

  - Se o Load Balancer estiver ativo, você receberá uma mensagem indicando que está "ACTIVE".
  - Se o Load Balancer não estiver ativo, você receberá o estado atual e um código de saída `2`, indicando uma condição de falha.

- **Verificação da Saúde dos Backends (check_backend_health)**:
  - O script fornecerá um relatório detalhado para cada Backend Set e seus backends. Cada linha indica o estado de saúde de um backend.
  - Se todos os backends estiverem saudáveis, você receberá mensagens indicando que estão "Saudáveis".
  - Se algum backend apresentar problemas, você receberá detalhes do problema e um código de saída `2`.

## Conclusão

O script `lb_status.sh` é uma ferramenta eficaz para o monitoramento rápido e fácil do estado e saúde dos Load Balancers na Oracle Cloud Infrastructure. Com este script, equipes técnicas podem manter uma visão clara sobre o desempenho e a estabilidade de seus recursos de Load Balancer.
