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
# <a name="get-the-list-of-leads-and-opportunities"></a><span data-ttu-id="5b6dd-103">Obter a lista de oportunidades potenciais e oportunidades</span><span class="sxs-lookup"><span data-stu-id="5b6dd-103">Get the list of leads and opportunities</span></span>

<span data-ttu-id="5b6dd-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="5b6dd-104">Applies to:</span></span>

- <span data-ttu-id="5b6dd-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="5b6dd-105">Partner API</span></span>

 <span data-ttu-id="5b6dd-106">Este tópico explica como obter a lista de leads recebidas da página do provedor de solução microsoft e co-vender oportunidades recebidas de vendedores da Microsoft ou de outros parceiros.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-106">This topic explains how to get the list of leads received from Microsoft solution provider page and co-sell opportunities received from Microsoft sellers or other partners.</span></span> <span data-ttu-id="5b6dd-107">Isto também irá obter a lista de oportunidades de co-venda ou negócios de pipeline criados pela sua organização.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-107">This will also fetch the list of co-sell opportunities or pipeline deals created by your organization.</span></span>

> [!Note]
> <span data-ttu-id="5b6dd-108">As leads recebidas do mercado comercial da Microsoft (Azure Marketplace e AppSource) não são suportadas.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-108">Leads received from the Microsoft commercial marketplace (Azure Marketplace and AppSource) are not supported.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b6dd-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5b6dd-109">Prerequisites</span></span>

- <span data-ttu-id="5b6dd-110">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="5b6dd-110">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="5b6dd-111">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-111">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="5b6dd-112">Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-112">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Referral Admin or Referral User.</span></span>

## <a name="rest-request"></a><span data-ttu-id="5b6dd-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="5b6dd-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5b6dd-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b6dd-114">Request syntax</span></span>

| <span data-ttu-id="5b6dd-115">Método</span><span class="sxs-lookup"><span data-stu-id="5b6dd-115">Method</span></span>  | <span data-ttu-id="5b6dd-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="5b6dd-116">Request URI</span></span>                                                    |
|:--------|:---------------------------------------------------------------|
| <span data-ttu-id="5b6dd-117">**Obter**</span><span class="sxs-lookup"><span data-stu-id="5b6dd-117">**GET**</span></span> | <https://api.partner.microsoft.com/v1.0/engagements/referrals> |

#### <a name="supported-odata-operations"></a><span data-ttu-id="5b6dd-118">Operações OData suportadas</span><span class="sxs-lookup"><span data-stu-id="5b6dd-118">Supported OData operations</span></span>

| <span data-ttu-id="5b6dd-119">Nome</span><span class="sxs-lookup"><span data-stu-id="5b6dd-119">Name</span></span>     | <span data-ttu-id="5b6dd-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b6dd-120">Description</span></span>     | <span data-ttu-id="5b6dd-121">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="5b6dd-121">Required</span></span>    | <span data-ttu-id="5b6dd-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5b6dd-122">Example</span></span>                                                                                                                                                                                                                                                     |
|:---------|:----------------|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5b6dd-123">$select</span><span class="sxs-lookup"><span data-stu-id="5b6dd-123">$select</span></span>  | <span data-ttu-id="5b6dd-124">Seleciona campos</span><span class="sxs-lookup"><span data-stu-id="5b6dd-124">Selects fields</span></span>  | <span data-ttu-id="5b6dd-125">Não</span><span class="sxs-lookup"><span data-stu-id="5b6dd-125">No</span></span>          | `/referrals?$select=id,status,customerProfile`                                                                                                                                                                                                              |
| <span data-ttu-id="5b6dd-126">$filter</span><span class="sxs-lookup"><span data-stu-id="5b6dd-126">$filter</span></span>  | <span data-ttu-id="5b6dd-127">Resultados dos filtros</span><span class="sxs-lookup"><span data-stu-id="5b6dd-127">Filters results</span></span> | <span data-ttu-id="5b6dd-128">Recomendado</span><span class="sxs-lookup"><span data-stu-id="5b6dd-128">Recommended</span></span> | `/referrals?$filter=engagementId eq '65edc0b5-3485-41b7-a17e-dfa9ef4706e2'` <br/> `/referrals?$filter=status eq 'New' and qualification eq 'SalesQualified'` <br/> `/referrals?$filter=customerProfile/address/country eq 'US' and direction eq 'Incoming'` |
| <span data-ttu-id="5b6dd-129">$orderby</span><span class="sxs-lookup"><span data-stu-id="5b6dd-129">$orderby</span></span> | <span data-ttu-id="5b6dd-130">Resultados das encomendas</span><span class="sxs-lookup"><span data-stu-id="5b6dd-130">Orders results</span></span>  | <span data-ttu-id="5b6dd-131">Recomendado</span><span class="sxs-lookup"><span data-stu-id="5b6dd-131">Recommended</span></span> | `/referrals?$orderby=createdDateTime desc`                                                                                                                                                                                                                  |

#### <a name="supported-orderby-parameters"></a><span data-ttu-id="5b6dd-132">Parâmetros de ordem suportados</span><span class="sxs-lookup"><span data-stu-id="5b6dd-132">Supported orderby parameters</span></span>

<span data-ttu-id="5b6dd-133">Use os seguintes parâmetros $orderby para classificar a lista de pistas e oportunidades</span><span class="sxs-lookup"><span data-stu-id="5b6dd-133">Use the following $orderby parameters to sort the list of leads and opportunities</span></span>

| <span data-ttu-id="5b6dd-134">Nome</span><span class="sxs-lookup"><span data-stu-id="5b6dd-134">Name</span></span>            | <span data-ttu-id="5b6dd-135">Tipo</span><span class="sxs-lookup"><span data-stu-id="5b6dd-135">Type</span></span>     | <span data-ttu-id="5b6dd-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b6dd-136">Description</span></span>                                       |
|:----------------|:---------|:--------------------------------------------------|
| <span data-ttu-id="5b6dd-137">createdDateTime</span><span class="sxs-lookup"><span data-stu-id="5b6dd-137">createdDateTime</span></span> | <span data-ttu-id="5b6dd-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b6dd-138">DateTime</span></span> | <span data-ttu-id="5b6dd-139">Data e hora da criação do chumbo ou oportunidade</span><span class="sxs-lookup"><span data-stu-id="5b6dd-139">Creation date and time of the lead or opportunity</span></span> |
| <span data-ttu-id="5b6dd-140">atualizadoDa hora do tempo</span><span class="sxs-lookup"><span data-stu-id="5b6dd-140">updatedDateTime</span></span> | <span data-ttu-id="5b6dd-141">DateTime</span><span class="sxs-lookup"><span data-stu-id="5b6dd-141">DateTime</span></span> | <span data-ttu-id="5b6dd-142">Atualizar data e hora do chumbo ou oportunidade</span><span class="sxs-lookup"><span data-stu-id="5b6dd-142">Update date and time of the lead or opportunity</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="5b6dd-143">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="5b6dd-143">Request headers</span></span>

<span data-ttu-id="5b6dd-144">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-144">See [Partner REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="5b6dd-145">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="5b6dd-145">Request body</span></span>

<span data-ttu-id="5b6dd-146">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5b6dd-147">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="5b6dd-147">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$orderby=createdDateTime desc HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="5b6dd-148">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="5b6dd-148">REST response</span></span>

<span data-ttu-id="5b6dd-149">Se for bem sucedido, o corpo de resposta contém uma coleção de [leads e/ou oportunidades](referral-resources.md).</span><span class="sxs-lookup"><span data-stu-id="5b6dd-149">If successful, the response body contains a collection of [leads and/or opportunities](referral-resources.md).</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5b6dd-150">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="5b6dd-150">Response success and error codes</span></span>

<span data-ttu-id="5b6dd-151">Cada resposta vem com um [código de estado HTTP](error-codes.md) que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-151">Each response comes with an [HTTP status code](error-codes.md) that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5b6dd-152">Utilize uma ferramenta de rastreio de rede para ler este código, o tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-152">Use a network trace tool to read this code, the error type, and additional parameters.</span></span>

### <a name="response-example"></a><span data-ttu-id="5b6dd-153">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="5b6dd-153">Response example</span></span>

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

<span data-ttu-id="5b6dd-154">Use o `@odata.nextLink` para obter a próxima página de resultados.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-154">Use the `@odata.nextLink` to get the next page of results.</span></span>

> [!Note]
> <span data-ttu-id="5b6dd-155">Os campos da ilustração de exemplo acima não são exaustivos.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-155">The fields in the example illustratration above are not exhaustive.</span></span> <span data-ttu-id="5b6dd-156">A resposta real da API contém mais campos como as equipas de clientes e parceiros.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-156">The actual API response contains more fields like the customer and partner teams.</span></span> <span data-ttu-id="5b6dd-157">Para obter a lista completa dos campos suportados, consulte [os recursos de encaminhamento.](referral-resources.md)</span><span class="sxs-lookup"><span data-stu-id="5b6dd-157">For the full list of supported fields, see [referral resources](referral-resources.md).</span></span>

## <a name="sample-requests"></a><span data-ttu-id="5b6dd-158">Pedidos de amostra</span><span class="sxs-lookup"><span data-stu-id="5b6dd-158">Sample requests</span></span>

1. <span data-ttu-id="5b6dd-159">Obtém o top 10 mais recente de oportunidades de co-venda.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-159">Gets the top 10 most recent inbound co-sell opportunities.</span></span> <span data-ttu-id="5b6dd-160">O pedido irá buscar oportunidades iniciadas por um representante de vendas da Microsoft ou outro parceiro, convidando a sua organização a participar numa atividade de co-venda.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-160">The request will fetch opportunities initiated by a Microsoft sales representative or another partner, inviting your organization to participate in a co-selling activity.</span></span>
    
    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$top=10&$filter=(type eq 'Shared' and direction eq 'Incoming')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```

2. <span data-ttu-id="5b6dd-161">Obtém as mais recentes pistas de entrada e oportunidades que não foram respondidas.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-161">Gets the most recent inbound leads and opportunities that have not been responded to.</span></span>  

    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$top=10&$filter=(direction eq 'Incoming' and substatus eq 'Pending')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```

    > [!Important]
    > <span data-ttu-id="5b6dd-162">Se não responder a uma vantagem ou oportunidade dentro do tempo atribuído (atualmente 14 dias), arquivá-la-emos como Expirado e notificaremos a Microsoft ou o parceiro que lhe enviou esta oportunidade.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-162">If you don't respond to a lead or opportunity within the allotted time (currently 14 days), we'll archive it as Expired and notify either Microsoft or the partner who sent you this opportunity.</span></span>

3. <span data-ttu-id="5b6dd-163">Obtém as mais recentes oportunidades de co-venda ativas iniciadas pela sua organização e sendo trabalhadas por um vendedor específico.</span><span class="sxs-lookup"><span data-stu-id="5b6dd-163">Gets the most recent active co-sell opportunities initiated by your organization and being worked on by a specific seller.</span></span>
    ```http
    GET https://api.partner.microsoft.com/v1.0/engagements/referrals?$filter=status eq 'Active' and direction eq 'Outgoing' and type eq 'Shared' and team/any(t:t/email eq 'r2d2@contoso.com')&$orderby=createdDateTime desc HTTP/1.1
    Authorization: Bearer <token>
    Content-Type: application/json
    ```