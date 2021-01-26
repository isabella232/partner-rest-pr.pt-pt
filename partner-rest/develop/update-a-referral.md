---
title: Atualizar uma vantagem ou oportunidade (Obsoleta)
description: Permite-lhe atualizar os detalhes de chumbo ou oportunidade. Este método de atualização de uma vantagem ou oportunidade é obsoleto e recomeciamos usando a chamada PATCH.
ms.date: 09/30/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 9705db1c21dbec7099cfefebdc7bb23ec65e428c
ms.sourcegitcommit: 1e38faa376f317151aca15ae126015e290baa556
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97770544"
---
# <a name="update-a-lead-or-opportunity-obsolete"></a>Atualizar uma vantagem ou oportunidade (Obsoleta)

Aplica-se a:

- Parceiro API

Este tópico explica como atualizar os detalhes de chumbo ou oportunidade como o valor do negócio, data estimada de fecho ou gerir as fases de vendas entre outros detalhes. 


> [!IMPORTANT]
Este método de atualização de uma vantagem ou oportunidade é obsoleto e recomeciamos usando a chamada [PATCH.](patch-a-referral.md)

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.
- Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                       |
|---------|-------------------------------------------------------------------|
| **PUT** | <https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}> |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Para obter mais informações, consulte [os cabeçalhos Partner API REST](headers.md).

> [!IMPORTANT]
> Certifique-se de definir o **cabeçalho If-Match.**

### <a name="request-body"></a>Corpo do pedido

Esta tabela descreve as propriedades [de referência](referral-resources.md) no corpo de pedido.

| Propriedade            | Tipo                                                                 | Descrição                                                                                                          |
|---------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| Id                  | string                                                               | A identificação desta referência.                                                                                            |
| EngagementId        | string                                                               | O EngagementID para esta referência. Várias referências podem ser associadas a um único EngagementID                    |
| Nome                | string                                                               | O nome da Referência.                                                                                            |
| ExternoReferênciaId | string                                                               | Um identificador externo para a referência. Exemplo: Guarde o seu próprio ID de chumbo/oportunidade Dynamics 365                    |
| CreatedDateTime     | cadeia no formato de hora de data UTC                                       | A data em que a referência foi criada.                                                                                   |
| Hora do Natal Atualizado     | cadeia no formato de hora de data UTC                                       | A data em que a referência foi atualizada pela última vez.                                                                              |
| Expiração Hora do Fim  | cadeia no formato de hora de data UTC                                       | A data da referência expirará.                                                                                   |
| Estado              | [ReferênciaStatus](referral-resources.md#referralstatus)               | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.          |
| Subtátuo           | [ReferênciaSubstato](referral-resources.md#referralsubstatus)         | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o sub estatuto de encaminhamento.      |
| StatusReason        | string                                                               | Uma mensagem descritiva sobre o estado. Por exemplo, explique por que a referência foi perdida.                              |
| Tipo de Referência        | [Tipo de Referência](referral-resources.md#referraltype)                   | Representa o tipo de referência.                                                                                        |
| Qualificação       | [Qualificação de ReferênciaS](referral-resources.md#referralqualification) | Representa a qualidade da referência.                                                                              |
| CustomerProfile     | [CustomerProfile](referral-resources.md#customerprofile)             | Informações de contacto com o cliente.                                                                                        |
| Consent (Consentimento)             | [Consent (Consentimento)](referral-resources.md#consent)                             | O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores.                |
| Detalhes             | [ReferênciaDetails](referral-resources.md#referraldetails)             | Detalhes do cliente, notas, valor da oferta, data de fecho de moeda.                                                          |
| Equipa                | [Membro](referral-resources.md#member)                               | Representa os utilizadores nas organizações envolvidas no envolvimento do parceiro.                                   |
| ConvidarContexto       | [ConvidarContexto](referral-resources.md#invitecontext)                 | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro. |
| Destino         | [ReferênciaTarget](referral-resources.md#target)        | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.  |

### <a name="status-and-substatus-transition-states"></a>Estado e estados de transição sub-estatuetas

| Estado | Transição de Estado Permitida | Substatus permitido            |
|--------|---------------------------|------------------------------|
| Novo    | Novo, Ativo, Fechado       | Pendente, Recebido            |
| Ativo | Ativo, Fechado            | Aceite                     |
| Fechado | Fechado                    | Won, Lost, Declined, expirou |

### <a name="request-example"></a>Exemplo de pedido

```http
PUT https://api.partner.microsoft.com/v1.0/engagements/referrals/49d90c72-3326-4f61-aacc-2cb57970448c HTTP/1.1
Authorization: Bearer <token>
Host: api.partner.microsoft.com
Content-Type: application/json

 {
    "id": "49d90c72-3326-4f61-aacc-2cb57970448c",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "createdDateTime": "2018-11-06T18:40:42.6178337Z",
    "updatedDateTime": "2018-11-06T18:40:42.6178337Z",
    "expirationDateTime": "2018-11-14T00:00:00Z",
    "status": "Closed",
    "substatus": "Won",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Independent",
    "target": [
        {
            "type": "BusinessProfileLocation",
            "id": "01e2abcd-52b0-4af3-a3ae-1fd1530b3563"
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
    },
    "eTag": "\"2500ec5a-0000-0000-0000-5bf4967d0000\"",

}
```

> [!IMPORTANT]
> Retire o `"links": { }` objeto do recurso PUT.

## <a name="rest-response"></a>Resposta REST

Se for bem sucedido, este método devolve o recurso [de referência](referral-resources.md) povoado no organismo de resposta.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

``` http
{
    "id": "4111fffc-f9ee-4d53-bba6-569135228642",
    "organizationId": "7d23e5ca-19dc-4eaa-aac8-5e6b559f0d1d",
    "organizationName": "Contoso Company",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "createdDateTime": "2018-11-06T18:40:42.6178337Z",
    "updatedDateTime": "2018-11-06T18:43:38.9948636Z",
    "expirationDateTime": "2018-11-14T00:00:00Z",
    "status": "Closed",
    "substatus": "Won",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Independent",
    "target": [
        {
            "type": "BusinessProfileLocation",
            "id": "01e2abcd-52b0-4af3-a3ae-1fd1530b3563"
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
    "eTag": "\"2500ec5a-0000-0000-0000-5bf4967d0000\"",
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