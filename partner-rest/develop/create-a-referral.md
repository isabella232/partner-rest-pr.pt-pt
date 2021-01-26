---
title: Criar uma referência
description: Criar referências independentes ou partilhadas na API do Parceiro.
ms.date: 05/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 6aab4b5f45030c3c16294b2929b1a6d3086fb951
ms.sourcegitcommit: 3c165938f544ff226cbe11ca21ed5aa00448d9b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2020
ms.locfileid: "97770493"
---
# <a name="create-a-referral"></a>Criar uma referência

Aplica-se a:

- Parceiro API

Este tópico explica como criar uma referência. Existem dois tipos de [ReferralType:](referral-resources.md#referraltype)

1. Independente: Quando uma referência é visível a um parceiro.
2. Partilhado: Onde uma referência é visível para dois partidos que estão a trabalhar em conjunto. Por exemplo, se a Microsoft e um parceiro estiverem a trabalhar juntos num negócio de co-venda, uma referência pode ser partilhada entre ambas as partes. Para mais informações, consulte a secção [Criar uma referência partilhada.](#create-a-shared-referral)

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                  |
|---------|--------------------------------------------------------------|
| **Publicar** | <https://api.partner.microsoft.com/v1.0/engagements/referrals> |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Consulte [os cabeçalhos API REST do Parceiro](headers.md) para obter mais informações.

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades [de referência](referral-resources.md) no organismo de pedido para uma nova referência.

| Propriedade            | Tipo                                                                 | Descrição                                                                                                          |
|---------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Nome                | string                                                               | O nome da Referência.                                                                                            |
| ExternoReferênciaId | string                                                               | Um identificador externo para a referência. Por exemplo, o seu próprio ID de chumbo ou oportunidade dynamics 365.                   |
| Estado              | [ReferênciaStatus](referral-resources.md#referralstatus)               | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.          |
| Subtátuo           | [ReferênciaSubstato](referral-resources.md#referralsubstatus)         | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o substatus de referência.       |
| StatusReason        | string                                                               | Uma mensagem descritiva sobre o estado. Por exemplo, explique por que a referência foi perdida.                            |
| Tipo de Referência        | [Tipo de Referência](referral-resources.md#referraltype)                   | Representa o tipo de referência. **Necessário.**                                                                                        |
| Qualificação       | [Qualificação de ReferênciaS](referral-resources.md#referralqualification) | Representa a qualidade da referência.                                                                              |
| CustomerProfile     | [CustomerProfile](referral-resources.md#customerprofile)             | Informações de contacto com o cliente.  **Necessário.**                                                                                      |
| Consent (Consentimento)             | [Consent (Consentimento)](referral-resources.md#consent)                             | O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores. **É necessário.**               |
| Detalhes             | [ReferênciaDetails](referral-resources.md#referraldetails)             | Detalhes do cliente, notas, valor da oferta, data de fecho de moeda. **Necessário.**                                                           |
| Equipa                | [Membro](referral-resources.md#member)                               | Representa os utilizadores nas organizações envolvidas no envolvimento do parceiro.                                   |
| ConvidarContexto       | [ConvidarContexto](referral-resources.md#invitecontext)                 | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro. |
| Destino         | [ReferênciaTarget](referral-resources.md#target)        | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.  |

#### <a name="status--substatus-transition-states"></a>Estado & Estados de transição substatus

| Estado | Transição de estado permitida | Substato permitido            |
|--------|---------------------------|------------------------------|
| Novo    | Novo, Ativo, Fechado       | Pendente, Recebido            |
| Ativo | Ativo, Fechado            | Aceite                     |
| Fechado | Fechado                    | Won, Lost, Declined, expirou |

### <a name="request-example"></a>Exemplo de pedido

```http
POST https://api.partner.microsoft.com/v1.0/engagements/referrals HTTP/1.1
Authorization: Bearer <token>
Host: api.partner.microsoft.com
Content-Type: application/json

 {
    "name": "Test Cosell Invite_20",
    "status": "New",
    "substatus": "Pending",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Shared",
    "target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-34104-EBB"
        }
    ],
    "customerProfile": {
        "name": "Contoso Customer Inc",
        "address": {
            "addressLine1": "One Microsoft Way",
            "addressLine2": "34",
            "city": "Redmond",
            "state": "WA",
            "postalCode": "98052",
            "country": "US"
        },
        "size": "10to50employees",
        "team": [
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Sue",
                "lastName": "Smith",
                "phoneNumber": "1234567890",
                "email": "sue.smith@contoso.com"
            },
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Joe",
                "lastName": "Hansen",
                "phoneNumber": "4035698759",
                "email": "joe.hansen@contoso.com"
            }
        ],
        "ids": []
    },
    "consent": {
        "consentToToShareInfoWithOthers": true,
        "consentToContact": true
    },
    "details": {
        "notes": "Customer is looking to leverage Dynamics 365 to manage their supply chain. There is also a need to leverage a set of custom apps to enable their business processes.",
        "dealValue": 50000,
        "currency": "USD",
        "closingDateTime": "2018-11-14T00:00:00Z",
        "requirements": {
            "industries": [
                {
                    "id": "Manufacturing"
                }
            ],
            "products": [
                {
                    "id": "Dynamics365Enterprise"
                }
            ],
            "services": [
                {
                    "id": "DeploymentOrMigration"
                }
            ],
            "solutions": [
                {
                    "name": "Dynamics 365 for Field Service",
                    "type": "Category",
                    "id": "Dynamics365forFieldService"
                }
            ]
        }
    },
    "team": [
        {
            "contactPreference": {
                "locale": "en-us",
                "disableNotifications": false
            },
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "1231231234",
            "email": "john.doe@microsoft.com"
        }
    ],
    "inviteContext": {
        "notes": "Hi ABC Partner, hoping you can help this customer. Thanks, John @ Microsoft",
        "invitedBy": {
            "organizationId": "msft"
        }
    }
}
```

## <a name="rest-response"></a>Resposta REST

Se for bem sucedido, este método devolve o recurso [de referência](referral-resources.md) povoado no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

``` http
{
    "id": "4111fffc-f9ee-4d53-bba6-569135228642",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "organizationId": "7d23e5ca-19dc-4eaa-aac8-5e6b559f0d1d",
    "organizationName": "Contoso Company",
    "name": "Test Cosell Invite_20",
    "externalReferenceId": null,
    "createdDateTime": "2019-02-23T02:05:23.2931817Z",
    "updatedDateTime": "2019-02-23T02:05:23.2931817Z",
    "expirationDateTime": null,
    "status": "Active",
    "substatus": "Accepted",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Shared",
    "eTag": "\"00006d10-0000-0000-0000-5c70aa630000\"",
    "target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-34104-EBB"
        }
    ],
    "customerProfile": {
        "name": "Contoso Customer Inc",
        "address": {
            "addressLine1": "One Microsoft Way",
            "addressLine2": "34",
            "city": "Redmond",
            "state": "WA",
            "postalCode": "98052",
            "country": "US"
        },
        "size": "10to50employees",
        "team": [
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Sue",
                "lastName": "Smith",
                "phoneNumber": "1234567890",
                "email": "sue.smith@contoso.com"
            },
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Joe",
                "lastName": "Hansen",
                "phoneNumber": "4035698759",
                "email": "joe.hansen@contoso.com"
            }
        ],
        "ids": []
    },
    "consent": {
        "consentToToShareInfoWithOthers": true,
        "consentToContact": true
    },
    "details": {
        "notes": "Customer is looking to leverage Dynamics 365 to manage their supply chain. There is also a need to leverage a set of custom apps to enable their business processes.",
        "dealValue": 50000,
        "currency": "USD",
        "requirements": {
            "industries": [
                {
                    "id": "Manufacturing"
                }
            ],
            "products": [
                {
                    "id": "Dynamics365Enterprise"
                }
            ],
            "services": [
                {
                    "id": "DeploymentOrMigration"
                }
            ],
            "solutions": [
                {
                    "name": "Dynamics 365 for Field Service",
                    "type": "Category",
                    "id": "Dynamics365forFieldService"
                }
            ]
        }
    },
    "team": [
        {
            "contactPreference": {
                "locale": "en-us",
                "disableNotifications": false
            },
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "1231231234",
            "email": "john.doe@microsoft.com"
        }
    ],
    "inviteContext": {
        "notes": "Hi ABC Partner, hoping you can help this customer. Thanks, John @ Microsoft",
        "invitedBy": {
            "organizationId": "msft"
        }
    },
    "links": {
        "relatedReferrals": {
            "uri": "https://api.partner.microsoft.com/v1.0/engagments/referrals?$filter=engagementId eq '37ef26aa-1d15-4533-9f93-a69bd33ab1e5'",
            "method": "GET"
        },
        "self": {
            "uri": "https://api.partner.microsoft.com/v1.0/engagments/referrals/4111fffc-f9ee-4d53-bba6-569135228642",
            "method": "GET"
        }
    }
}
```

## <a name="create-a-shared-referral"></a>Criar uma referência partilhada

Existem duas etapas para criar uma referência do tipo de [referência](referral-resources.md#referraltype) **partilhada.**

1. [Crie a sua referência partilhada](#create-your-referral)
2. [Criar uma referência conectada para o segundo partido](#create-a-connected-referral)

O gráfico de fluxo que se segue ilustra estes dois passos na criação de uma referência partilhada.

![Gráfico de fluxo mostrando uma referência partilhada com 2 referências ligadas através da API do Parceiro Microsoft](../images/SharedReferral.png)

### <a name="create-your-referral"></a>Crie a sua referência

1. Crie uma referência com [o set de Referência](referral-resources.md#referraltype) para compartilhado.
2. Copie o **noivadoId** da resposta de retorno.

[Amostra de referênciaStarget](referral-resources.md#target) para encaminhamento

```json
"target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-ABC-DEF"
        }
    ]
```

### <a name="create-a-connected-referral"></a>Criar uma referência conectada

1. Crie outra referência para a Microsoft.
2. Inclua o **enagementId** da sua referência para que estejam ligados.

[Amostra de ReferênciaTarget](referral-resources.md#target) para encaminhamento da Microsoft

```json
"target": [
        {
            "type": "BusinessProfileLocation",
            "id": "msft"
        }
    ]
```