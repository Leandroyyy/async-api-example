# Documentação da Agenda de Petshop

## Informações Gerais

- **Título**: Agenda de Petshop
- **Versão**: 1.0.0
- **Descrição**:
  Esta agenda de petshop captura eventos relacionados a novos agendamentos. Ela permite que você acompanhe quando uma consulta foi agendada para um pet. Para mais detalhes, consulte os exemplos de ações e eventos listados abaixo.
- **Licença**: Apache 2.0
  - [Licença Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)

## Tipo de Conteúdo Padrão

- **Tipo de Conteúdo Padrão**: `application/json`
  - Todas as mensagens e dados trocados seguem o formato JSON.

## Servidores

Os servidores definidos representam os diferentes ambientes onde a agenda de petshop opera. Cada ambiente utiliza o protocolo SNS da AWS e tem uma URL específica.

- **Prod (Produção)**:

  - **Host**: `arn:aws:sns:us-east-1:123456789012:pet-shop-example`
  - **Protocolo**: `sns`
  - **Descrição**: Tópico para a agenda de petshop em ambiente de produção.

- **Hom (Homologação)**:

  - **Host**: `arn:aws:sns:us-east-1:123456789012:pet-shop-example`
  - **Protocolo**: `sns`
  - **Descrição**: Tópico para a agenda de petshop em ambiente de homologação.

- **Dev (Desenvolvimento)**:
  - **Host**: `arn:aws:sns:us-east-1:123456789012:pet-shop-example`
  - **Protocolo**: `sns`
  - **Descrição**: Tópico para a agenda de petshop em ambiente de desenvolvimento.

## Canais

Os canais representam os tópicos SNS para os quais os eventos são enviados ou recebidos.

- **appointment-scheduled**:
  - **Descrição**: Tópico para ouvir mensagens sobre agendamentos.
  - **Mensagens**:
    - **agendado**: Mensagens relacionadas ao evento de agendamento, definidas no componente `AppointmentScheduledMessage`.

## Operações

As operações descrevem as ações que o sistema realiza em relação aos canais definidos.

- **AppointmentScheduledMessage**:
  - **Título**: Agendamento realizado
  - **Resumo**: Evento de agendamento de um pet.
  - **Descrição**: Notificação quando um novo agendamento é feito para um pet.
  - **Canal**:
    - Referência: `#/channels/appointment-scheduled`
  - **Ação**: `receive`
    - Indica que o sistema está recebendo mensagens desse canal.

## Componentes

Os componentes incluem mensagens e esquemas que definem a estrutura dos dados trocados.

### Mensagens

- **AppointmentScheduledMessage**:
  - **Nome**: `AppointmentScheduledMessage`
  - **Título**: Appointment Scheduled Message
  - **Resumo**: Notificação que um novo agendamento foi feito!
  - **Tipo de Conteúdo**: `application/json`
  - **Payload**:
    - **Referência**: `#/components/schemas/AppointmentScheduledMessagePayload`
    - Descreve a estrutura dos dados enviados nas mensagens de agendamento.

### Esquemas

- **AppointmentScheduledMessagePayload**:
  - **Tipo**: `object`
  - **Propriedades**:
    - **appointmentId**:
      - **Tipo**: `string`
      - **Descrição**: Identificador único do agendamento.
    - **petName**:
      - **Tipo**: `string`
      - **Descrição**: Nome do pet.
    - **serviceType**:
      - **Tipo**: `string`
      - **Descrição**: Tipo de serviço agendado (ex.: banho, consulta).
    - **scheduledTime**:
      - **Tipo**: `string`
      - **Formato**: `date-time`
      - **Descrição**: Data e hora do agendamento.
    - **ownerContact**:
      - **Tipo**: `string`
      - **Descrição**: Informação de contato do dono do pet.
