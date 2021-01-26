---
title: Obtenha uma lista de pistas e oportunidades
description: Como obter uma lista de pistas e oportunidades usando a API do Parceiro.
ms.date: 09/30/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 46243f8484a8068827e24e1d03f39ffddade1dbf
ms.sourcegitcommit: 1e38faa376f317151aca15ae126015e290baa556
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97770529"
---
# <a name="get-the-list-of-leads-and-opportunities"></a>Obter a lista de oportunidades potenciais e oportunidades

Aplica-se a:

- Parceiro API

 Este tópico explica como obter a lista de leads recebidas da página do provedor de solução microsoft e co-vender oportunidades recebidas de vendedores da Microsoft ou de outros parceiros. Isto também irá obter a lista de oportunidades de co-venda ou negócios de pipeline criados pela sua organização.

> [!Note]
> As leads recebidas do mercado comercial da Microsoft (Azure Marketplace e AppSource) não são suportadas.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.
- Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                    |
|:--------|:---------------------------------------------------------------|
| **Obter** | <https://api.partner.microsoft.com/v1.0/engagements/referrals> |

#### <a name="supported-odata-operations"></a>Operações OData suportadas

| Nome     | Descrição     | Obrigatório    | Exemplo                                                                                                                                                                                                                                                     |
|:---------|:----------------|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| $select  | Seleciona campos  | Não          | `/referrals?$select=id,status,customerProfile`                                                                                                                                                                                                              |
| $filter  | Resultados dos filtros | Recomendado | `/referrals?$filter=engagementId eq '65edc0b5-3485-41b7-a17e-dfa9ef4706e2'` <br/> `/referrals?$filter=status eq 'New' and qualification eq 'SalesQualified'` <br/> `/referrals?$filter=customerProfile/address/country eq 'US' and direction eq 'Incoming'` |
| $orderby | Resultados das encomendas  | Recomendado | `/referrals?$orderby=createdDateTime desc`                                                                                                                                                                                                                  |

#### <a name="supported-orderby-parameters"></a>Parâmetros de ordem suportados

Use os seguintes parâmetros $orderby para classificar a lista de pistas e oportunidades

| Nome            | Tipo     | Descrição                                       |
|:----------------|:---------|:--------------------------------------------------|
| createdDateTime | DateTime | Data e hora da criação do chumbo ou oportunidade |
| atualizadoDa hora do tempo | DateTime | Atualizar data e hora do chumbo ou oportunidade   |

### <a name="request-headers"></a>Cabeçalhos do pedido

Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.

### <a name="request-body"></a>Corpo do pedido

Nenhum.

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$orderby=createdDateTime desc HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, o corpo de resposta contém uma coleção de [leads e/ou oportunidades](referral-resources.md).

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um [código de estado HTTP](error-codes.md) que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.

### <a name="response-example"></a>Exemplo de resposta

``` http
HTTP/1.1 200 OK
Content-Type: application/json
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731

{
  "@odata.context": "http://api.partner.microsoft.com/v1.0/$metadata#Referrals",
  "@odata.count": 1,
  "value": [
    {
      "id": "c5fbb3b6-be74-4795-9fb5-4324c73fed37",
      "engagementId": "65edc0b5-3485-41b7-a17e-dfa9ef4706e2",
      "organizationId": "7d23e5ca-19dc-4eaa-aac8-5e6b559f0d1d",
      "organizationName": "Contoso Company",
      "createdDateTime": "2020-10-30T21:03:00.0000000Z",
      "updatedDateTime": "2020-10-30T21:03:00.0000000Z",
      "status": "New",
      "substatus": "Pending",
      "qualification": "Direct",
      "type": "Independent",
      "direction": "Incoming",
      "customerProfile": {
        "name": "Fabrikam Customer Inc",
        "address": {
          "addressLine1": "One Microsoft Way",
          "addressLine2": "",
          "city": "Redmond",
          "state": "WA",
          "postalCode": "98052",
          "country": "US"
        }
      },
      "details": {
        "notes": "We are interested in deploying Microsoft 365 and are looking for support in training our employees. Can you help?",
        "dealValue": 10000,
        "currency": "USD",
        "closingDateTime": "2020-12-01T00:00:00Z",
        "requirements": {
            "industries": [ { "id": "Education" } ],
            "products": [ { "id": "Microsoft365" } ],
            "services": [ { "id": "LearningAndCertification" } ],
            "solutions": [ { "id": "SOL-Microsoft365", "name": "Microsoft365" }
          ]
        }
      },
      "links": {
        "relatedReferrals": {
          "uri": "https://api.partner.microsoft.com/v1.0/engagements/referrals?$filter=engagementId eq '65edc0b5-3485-41b7-a17e-dfa9ef4706e2'",
          "method": "GET"
        },
        "self": {
          "uri": "https://api.partner.microsoft.com/v1.0/engagements/referrals/c5fbb3b6-be74-4795-9fb5-4324c73fed37",
          "method": "GET"
        }
      }
    }
  ],
  "@odata.nextLink": "http://api.partner.microsoft.com/v1.0/referrals?$skiptoken=k181pEdP0ykypkieJfcxX"
}
```

Use o `@odata.nextLink` para obter a próxima página de resultados.

> [!Note]
> Os campos da ilustração de exemplo acima não são exaustivos. A resposta real da API contém mais campos como as equipas de clientes e parceiros. Para obter a lista completa dos campos suportados, consulte [os recursos de encaminhamento.](referral-resources.md)

## <a name="sample-requests"></a>Pedidos de amostra

1. Obtém o top 10 mais recente de oportunidades de co-venda. O pedido irá buscar oportunidades iniciadas por um representante de vendas da Microsoft ou outro parceiro, convidando a sua organização a participar numa atividade de co-venda.
    
    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$top=10&$filter=(type eq 'Shared' and direction eq 'Incoming')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```

2. Obtém as mais recentes pistas de entrada e oportunidades que não foram respondidas.  

    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$top=10&$filter=(direction eq 'Incoming' and substatus eq 'Pending')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```

    > [!Important]
    > Se não responder a uma vantagem ou oportunidade dentro do tempo atribuído (atualmente 14 dias), arquivá-la-emos como Expirado e notificaremos a Microsoft ou o parceiro que lhe enviou esta oportunidade.

3. Obtém as mais recentes oportunidades de co-venda ativas iniciadas pela sua organização e sendo trabalhadas por um vendedor específico.
    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$filter=status eq 'Active' and direction eq 'Outgoing' and type eq 'Shared' and team/any(t:t/email eq 'r2d2@contoso.com')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```