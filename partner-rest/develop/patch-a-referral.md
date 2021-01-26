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
# <a name="update-a-lead-or-opportunity"></a><span data-ttu-id="485c7-103">Atualizar uma oportunidade potencial ou oportunidade</span><span class="sxs-lookup"><span data-stu-id="485c7-103">Update a lead or opportunity</span></span>

<span data-ttu-id="485c7-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="485c7-104">Applies to:</span></span>

- <span data-ttu-id="485c7-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="485c7-105">Partner API</span></span>

<span data-ttu-id="485c7-106">Este tópico explica como atualizar os detalhes de chumbo ou oportunidade como o valor do negócio, data estimada de fecho ou gerir as fases de vendas entre outros detalhes.</span><span class="sxs-lookup"><span data-stu-id="485c7-106">This topic explains how to update the lead or opportunity details like the deal value, estimated close date or manage the sales stages amongst other details.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="485c7-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="485c7-107">Prerequisites</span></span>

- <span data-ttu-id="485c7-108">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="485c7-108">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="485c7-109">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="485c7-109">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="485c7-110">Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.</span><span class="sxs-lookup"><span data-stu-id="485c7-110">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Referral Admin or Referral User.</span></span>

## <a name="rest-request"></a><span data-ttu-id="485c7-111">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="485c7-111">REST Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="485c7-112">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="485c7-112">Request syntax</span></span>

| <span data-ttu-id="485c7-113">Método</span><span class="sxs-lookup"><span data-stu-id="485c7-113">Method</span></span>  | <span data-ttu-id="485c7-114">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="485c7-114">Request URI</span></span>                                                       |
|---------|-------------------------------------------------------------------|
| <span data-ttu-id="485c7-115">**PATCH**</span><span class="sxs-lookup"><span data-stu-id="485c7-115">**PATCH**</span></span> | <https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}> |

### <a name="uri-parameter"></a><span data-ttu-id="485c7-116">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="485c7-116">URI parameter</span></span>


| <span data-ttu-id="485c7-117">Nome</span><span class="sxs-lookup"><span data-stu-id="485c7-117">Name</span></span>                   | <span data-ttu-id="485c7-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="485c7-118">Type</span></span>     | <span data-ttu-id="485c7-119">Necessário</span><span class="sxs-lookup"><span data-stu-id="485c7-119">Required</span></span> | <span data-ttu-id="485c7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="485c7-120">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="485c7-121">Id</span><span class="sxs-lookup"><span data-stu-id="485c7-121">Id</span></span>                      | <span data-ttu-id="485c7-122">string</span><span class="sxs-lookup"><span data-stu-id="485c7-122">string</span></span>   | <span data-ttu-id="485c7-123">Sim</span><span class="sxs-lookup"><span data-stu-id="485c7-123">Yes</span></span>       | <span data-ttu-id="485c7-124">O identificador único para uma oportunidade de chumbo ou co-venda</span><span class="sxs-lookup"><span data-stu-id="485c7-124">The unique identifier for a lead or co-sell opportunity</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="485c7-125">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="485c7-125">Request headers</span></span>

<span data-ttu-id="485c7-126">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="485c7-126">See [Partner REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="485c7-127">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="485c7-127">Request body</span></span>

<span data-ttu-id="485c7-128">O corpo de pedido segue o formato [Json Patch.](https://tools.ietf.org/html/rfc6902)</span><span class="sxs-lookup"><span data-stu-id="485c7-128">The request body follows the [Json Patch](https://tools.ietf.org/html/rfc6902) format.</span></span> <span data-ttu-id="485c7-129">Um documento do JSON Patch tem uma série de operações.</span><span class="sxs-lookup"><span data-stu-id="485c7-129">A JSON Patch document has an array of operations.</span></span> <span data-ttu-id="485c7-130">Cada operação identifica um tipo particular de mudança.</span><span class="sxs-lookup"><span data-stu-id="485c7-130">Each operation identifies a particular type of change.</span></span> <span data-ttu-id="485c7-131">Exemplos de tais alterações incluem adicionar um elemento de matriz ou substituir um valor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="485c7-131">Examples of such changes include adding an array element or replacing a property value.</span></span>

> [!Important]
> <span data-ttu-id="485c7-132">A API suporta atualmente apenas o `replace` e `add` opera.</span><span class="sxs-lookup"><span data-stu-id="485c7-132">The API currently only supports the `replace` and `add` operations.</span></span>

### <a name="request-example"></a><span data-ttu-id="485c7-133">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="485c7-133">Request example</span></span>

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
> <span data-ttu-id="485c7-134">Se o **cabeçalho Se-Match** for passado, será utilizado para o controlo da concordância.</span><span class="sxs-lookup"><span data-stu-id="485c7-134">If the **If-Match** header is passed, it will be used for concurrency control.</span></span>

## <a name="rest-response"></a><span data-ttu-id="485c7-135">Resposta REST</span><span class="sxs-lookup"><span data-stu-id="485c7-135">REST Response</span></span>

<span data-ttu-id="485c7-136">Se for bem sucedido, o organismo de resposta contém o [chumbo ou oportunidade](referral-resources.md)atualizados .</span><span class="sxs-lookup"><span data-stu-id="485c7-136">If successful, the response body contains the updated [lead or opportunity](referral-resources.md).</span></span>


### <a name="response-success-and-error-codes"></a><span data-ttu-id="485c7-137">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="485c7-137">Response success and error codes</span></span>

<span data-ttu-id="485c7-138">Cada resposta vem com um [código de estado HTTP](error-codes.md) que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="485c7-138">Each response comes with an [HTTP status code](error-codes.md) that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="485c7-139">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="485c7-139">Use a network trace tool to read this code, the error type, and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="485c7-140">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="485c7-140">Response example</span></span>

``` http
HTTP/1.1 204 No Content
Content-Length: 0
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
```

> [!Tip]
> <span data-ttu-id="485c7-141">O corpo de resposta depende do **cabeçalho Prefer.**</span><span class="sxs-lookup"><span data-stu-id="485c7-141">The response body depends on the **Prefer** header.</span></span> <span data-ttu-id="485c7-142">Se o valor do cabeçalho for omitido no pedido, o organismo de resposta está vazio com um código de estado HTTP 204.</span><span class="sxs-lookup"><span data-stu-id="485c7-142">If the header value is omitted in the request, the response body is empty with a HTTP Status code 204.</span></span> <span data-ttu-id="485c7-143">Adicione `Prefer: return=representation` ao cabeçalho para obter o chumbo ou oportunidade atualizados.</span><span class="sxs-lookup"><span data-stu-id="485c7-143">Add `Prefer: return=representation` to the header to get the updated lead or opportunity.</span></span>

## <a name="sample-requests"></a><span data-ttu-id="485c7-144">Pedidos de amostra</span><span class="sxs-lookup"><span data-stu-id="485c7-144">Sample requests</span></span>

1. <span data-ttu-id="485c7-145">Atualiza o valor do negócio para a oportunidade de 10000 e atualiza as notas.</span><span class="sxs-lookup"><span data-stu-id="485c7-145">Updates the deal value for the opportunity to 10000 and updates the notes.</span></span> <span data-ttu-id="485c7-146">Não há cheques de concordância por causa do absense do `If-Match` cabeceamento.</span><span class="sxs-lookup"><span data-stu-id="485c7-146">There are no concurrency checks because of the absense of the `If-Match` header.</span></span>
    
    ```http
    PATCH https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}
    Authorization: Bearer <token>
    Content-Type: application/json
    
    [
        {"op":"replace","path":"/details/dealValue","value":"10000"},
        {"op":"replace","path":"/details/notes","value":"Lorem ipsum dolor sit amet."}
    ]
    ```

2. <span data-ttu-id="485c7-147">Atualiza o estado de uma vantagem ou oportunidade para Won.</span><span class="sxs-lookup"><span data-stu-id="485c7-147">Updates the status of a lead or opportunity to Won.</span></span>
    
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
    > <span data-ttu-id="485c7-148">Os `status` campos e campos devem estar em conformidade com o conjunto permitido de `substatus` valores de transição, tal como [descrito aqui.](referral-resources.md)</span><span class="sxs-lookup"><span data-stu-id="485c7-148">The `status` and `substatus` fields should conform to the allowed set of transition values as described [here](referral-resources.md).</span></span>

3. <span data-ttu-id="485c7-149">Adiciona um novo membro da sua organização à equipa de chumbo ou oportunidade.</span><span class="sxs-lookup"><span data-stu-id="485c7-149">Adds a new member from your organization to the lead or opportunity team.</span></span> <span data-ttu-id="485c7-150">A resposta conterá o chumbo ou oportunidade atualizado devido à presença do `Prefer: return=representation` cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="485c7-150">The response will contain the updated lead or opportunity because of the presence of the `Prefer: return=representation` header.</span></span>

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
