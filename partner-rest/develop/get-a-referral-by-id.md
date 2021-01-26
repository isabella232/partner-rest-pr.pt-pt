---
title: Obter uma oportunidade potencial ou oportunidade por ID
description: Obter uma pista ou oportunidade por ID.
ms.date: 09/30/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: dcfaea393afc6a9d09946b4c31b7168ba26aa255
ms.sourcegitcommit: 1e38faa376f317151aca15ae126015e290baa556
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97770532"
---
# <a name="get-a-lead-or-opportunity-by-id"></a><span data-ttu-id="fff81-103">Obter uma oportunidade potencial ou oportunidade por ID</span><span class="sxs-lookup"><span data-stu-id="fff81-103">Get a lead or opportunity by Id</span></span>

<span data-ttu-id="fff81-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="fff81-104">Applies to:</span></span>

- <span data-ttu-id="fff81-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="fff81-105">Partner API</span></span>

<span data-ttu-id="fff81-106">Este tópico explica como obter uma oportunidade de liderança ou co-venda por Id.</span><span class="sxs-lookup"><span data-stu-id="fff81-106">This topic explains how to get a lead or co-sell opportunity by Id.</span></span>

> [!Note]
> <span data-ttu-id="fff81-107">As leads recebidas do mercado comercial da Microsoft (Azure Marketplace e AppSource) não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="fff81-107">Leads received from the Microsoft commercial marketplace (Azure Marketplace and AppSource) are not supported.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="fff81-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fff81-108">Prerequisites</span></span>

- <span data-ttu-id="fff81-109">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="fff81-109">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="fff81-110">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="fff81-110">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="fff81-111">Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.</span><span class="sxs-lookup"><span data-stu-id="fff81-111">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Referral Admin or Referral User.</span></span>

## <a name="rest-request"></a><span data-ttu-id="fff81-112">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="fff81-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fff81-113">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="fff81-113">Request syntax</span></span>

| <span data-ttu-id="fff81-114">Método</span><span class="sxs-lookup"><span data-stu-id="fff81-114">Method</span></span>   | <span data-ttu-id="fff81-115">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="fff81-115">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fff81-116">**Obter**</span><span class="sxs-lookup"><span data-stu-id="fff81-116">**GET**</span></span> | <https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}>                                     |

### <a name="uri-parameter"></a><span data-ttu-id="fff81-117">Parâmetro URI</span><span class="sxs-lookup"><span data-stu-id="fff81-117">URI parameter</span></span>


| <span data-ttu-id="fff81-118">Nome</span><span class="sxs-lookup"><span data-stu-id="fff81-118">Name</span></span>                   | <span data-ttu-id="fff81-119">Tipo</span><span class="sxs-lookup"><span data-stu-id="fff81-119">Type</span></span>     | <span data-ttu-id="fff81-120">Necessário</span><span class="sxs-lookup"><span data-stu-id="fff81-120">Required</span></span> | <span data-ttu-id="fff81-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="fff81-121">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="fff81-122">Id</span><span class="sxs-lookup"><span data-stu-id="fff81-122">Id</span></span>                      | <span data-ttu-id="fff81-123">string</span><span class="sxs-lookup"><span data-stu-id="fff81-123">string</span></span>   | <span data-ttu-id="fff81-124">Sim</span><span class="sxs-lookup"><span data-stu-id="fff81-124">Yes</span></span>       | <span data-ttu-id="fff81-125">O identificador único para uma oportunidade de chumbo ou co-venda</span><span class="sxs-lookup"><span data-stu-id="fff81-125">The unique identifier for a lead or co-sell opportunity</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="fff81-126">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="fff81-126">Request headers</span></span>

<span data-ttu-id="fff81-127">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fff81-127">See [Partner REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="fff81-128">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="fff81-128">Request body</span></span>

<span data-ttu-id="fff81-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fff81-129">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fff81-130">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="fff81-130">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id} HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="fff81-131">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="fff81-131">REST response</span></span>

<span data-ttu-id="fff81-132">Se for bem sucedido, o corpo de resposta contém o [chumbo ou oportunidade](referral-resources.md) correspondente ao ID.</span><span class="sxs-lookup"><span data-stu-id="fff81-132">If successful, the response body contains the [lead or opportunity](referral-resources.md) matching the Id.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fff81-133">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="fff81-133">Response success and error codes</span></span>

<span data-ttu-id="fff81-134">Cada resposta vem com um [código de estado HTTP](error-codes.md) que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="fff81-134">Each response comes with an [HTTP status code](error-codes.md) that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fff81-135">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="fff81-135">Use a network trace tool to read this code, the error type, and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="fff81-136">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="fff81-136">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Type: application/json
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731

{
    "@odata.context": "https://api.partner.microsoft.com/v1.0/engagments/referrals/$metadata#Referrals/$entity",
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
      "notes": "We are interested in deploying Microsoft 365 and are looking forsupport in training our employees. Can you help?",
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
        "uri": "https://api.partner.microsoft.com/v1.0/engagements/referrals$filter=engagementId eq '65edc0b5-3485-41b7-a17e-dfa9ef4706e2'",
        "method": "GET"
      },
      "self": {
        "uri": "https://api.partner.microsoft.com/v1.0/engagements/referralsc5fbb3b6-be74-4795-9fb5-4324c73fed37",
        "method": "GET"
      }
    },
    "eTag": "\"2500ec5a-0000-0000-0000-5bf4967d0000\""
}
```

> [!Note]
> <span data-ttu-id="fff81-137">Os campos da ilustração de exemplo acima não são exaustivos.</span><span class="sxs-lookup"><span data-stu-id="fff81-137">The fields in the example illustratration above are not exhaustive.</span></span> <span data-ttu-id="fff81-138">A resposta real da API contém mais campos como as equipas de clientes e parceiros.</span><span class="sxs-lookup"><span data-stu-id="fff81-138">The actual API response contains more fields like the customer and partner teams.</span></span> <span data-ttu-id="fff81-139">Para obter a lista completa dos campos suportados, consulte [os recursos de encaminhamento.](referral-resources.md)</span><span class="sxs-lookup"><span data-stu-id="fff81-139">For the full list of supported fields, see [referral resources](referral-resources.md).</span></span>