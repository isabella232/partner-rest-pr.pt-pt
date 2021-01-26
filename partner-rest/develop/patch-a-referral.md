---
title: Atualizar uma oportunidade potencial ou oportunidade
description: Permite-lhe atualizar os detalhes de chumbo ou oportunidade.
ms.date: 09/30/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: abfe7308f46cd65b9358b369f6fa05bcca4c1df2
ms.sourcegitcommit: 1e38faa376f317151aca15ae126015e290baa556
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97770541"
---
# <a name="update-a-lead-or-opportunity"></a>Atualizar uma oportunidade potencial ou oportunidade

Aplica-se a:

- Parceiro API

Este tópico explica como atualizar os detalhes de chumbo ou oportunidade como o valor do negócio, data estimada de fecho ou gerir as fases de vendas entre outros detalhes.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário suporta a autenticação com credenciais app+utilizador.
- Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método  | URI do pedido                                                       |
|---------|-------------------------------------------------------------------|
| **PATCH** | <https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}> |

### <a name="uri-parameter"></a>Parâmetro URI


| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Id                      | string   | Sim       | O identificador único para uma oportunidade de chumbo ou co-venda       |

### <a name="request-headers"></a>Cabeçalhos do pedido

Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.

### <a name="request-body"></a>Corpo do pedido

O corpo de pedido segue o formato [Json Patch.](https://tools.ietf.org/html/rfc6902) Um documento do JSON Patch tem uma série de operações. Cada operação identifica um tipo particular de mudança. Exemplos de tais alterações incluem adicionar um elemento de matriz ou substituir um valor de propriedade.

> [!Important]
> A API suporta atualmente apenas o `replace` e `add` opera.

### <a name="request-example"></a>Exemplo de pedido

```http
PATCH https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}
Authorization: Bearer <token>
Content-Type: application/json
Prefer: return=representation

[
    {
        "op": "replace",
        "path": "/details/dealValue",
        "value": "10000"
    },
    {
        "op": "add",
        "path": "/team/-",
        "value": {
            "email": "jane.doe@contoso.com",
            "firstName": "Jane",
            "lastName": "Doe",
            "phoneNumber": "0000000001"
        }
    }
]
```

> [!Note]
> Se o **cabeçalho Se-Match** for passado, será utilizado para o controlo da concordância.

## <a name="rest-response"></a>Resposta REST

Se for bem sucedido, o organismo de resposta contém o [chumbo ou oportunidade](referral-resources.md)atualizados .


### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um [código de estado HTTP](error-codes.md) que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.

### <a name="response-example"></a>Exemplo de resposta

``` http
HTTP/1.1 204 No Content
Content-Length: 0
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
```

> [!Tip]
> O corpo de resposta depende do **cabeçalho Prefer.** Se o valor do cabeçalho for omitido no pedido, o organismo de resposta está vazio com um código de estado HTTP 204. Adicione `Prefer: return=representation` ao cabeçalho para obter o chumbo ou oportunidade atualizados.

## <a name="sample-requests"></a>Pedidos de amostra

1. Atualiza o valor do negócio para a oportunidade de 10000 e atualiza as notas. Não há cheques de concordância por causa do absense do `If-Match` cabeceamento.
    
    ```http
    PATCH https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}
    Authorization: Bearer <token>
    Content-Type: application/json
    
    [
        {"op":"replace","path":"/details/dealValue","value":"10000"},
        {"op":"replace","path":"/details/notes","value":"Lorem ipsum dolor sit amet."}
    ]
    ```

2. Atualiza o estado de uma vantagem ou oportunidade para Won.
    
    ```http
    PATCH https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}
    Authorization: Bearer <token>
    Content-Type: application/json
    
    [
        {"op":"replace", "path":"/status", "value":"Closed"},
        {"op":"replace", "path":"/substatus", "value":"Won"}
    ]
    ```

    > [!Important]
    > Os `status` campos e campos devem estar em conformidade com o conjunto permitido de `substatus` valores de transição, tal como [descrito aqui.](referral-resources.md)

3. Adiciona um novo membro da sua organização à equipa de chumbo ou oportunidade. A resposta conterá o chumbo ou oportunidade atualizado devido à presença do `Prefer: return=representation` cabeçalho.

    ```http
    PATCH https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}
    Authorization: Bearer <token>
    Content-Type: application/json
    Prefer: return=representation
    
    [
        {
            "op": "add",
            "path": "/team/-",
            "value": {
                "email": "jane.doe@contoso.com",
                "firstName": "Jane",
                "lastName": "Doe",
                "phoneNumber": "0000000001"
            }
        }
    ]
    ```
