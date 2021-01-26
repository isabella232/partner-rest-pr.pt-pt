---
title: Obter taxas de câmbio estrangeiras
description: Obtenha taxas de câmbio por um determinado mês.
ms.date: 01/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 1e718624db54dcc2ed2b5d2d93dfd1cef0e6f96f
ms.sourcegitcommit: bb3f5f7ee0489bded86fe52e55018c1f4f5032e2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2020
ms.locfileid: "97770520"
---
# <a name="get-foreign-exchange-rates"></a><span data-ttu-id="6fda2-103">Obter taxas de câmbio estrangeiras</span><span class="sxs-lookup"><span data-stu-id="6fda2-103">Get foreign exchange rates</span></span>

<span data-ttu-id="6fda2-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="6fda2-104">Applies to:</span></span>

- <span data-ttu-id="6fda2-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="6fda2-105">Partner API</span></span>

<span data-ttu-id="6fda2-106">Este tópico explica como obter taxas de câmbio por um determinado mês.</span><span class="sxs-lookup"><span data-stu-id="6fda2-106">This topic explains how to get foreign exchange rates for a given month.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fda2-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6fda2-107">Prerequisites</span></span>

- <span data-ttu-id="6fda2-108">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="6fda2-108">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="6fda2-109">Este cenário apenas suporta a autenticação do utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="6fda2-109">This scenario only supports application user authentication.</span></span> <span data-ttu-id="6fda2-110">Só a candidatura ainda não está apoiada.</span><span class="sxs-lookup"><span data-stu-id="6fda2-110">Application-only is not yet supported.</span></span>
- <span data-ttu-id="6fda2-111">Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.</span><span class="sxs-lookup"><span data-stu-id="6fda2-111">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.</span></span>


## <a name="details"></a><span data-ttu-id="6fda2-112">Detalhes</span><span class="sxs-lookup"><span data-stu-id="6fda2-112">Details</span></span>

- <span data-ttu-id="6fda2-113">Atualmente utilizado com [a API de folha de preços](get-a-price-sheet.md) para calcular os encargos esperados para as moedas locais do plano Azure CSP.</span><span class="sxs-lookup"><span data-stu-id="6fda2-113">Currently used with [get price sheet API](get-a-price-sheet.md) to calculate expected charges for Azure plan CSP local currencies.</span></span>
- <span data-ttu-id="6fda2-114">As taxas de câmbio mantêm-se verdadeiras durante todo o mês em que são publicadas.</span><span class="sxs-lookup"><span data-stu-id="6fda2-114">Foreign exchange rates hold true for the entire month they are posted.</span></span>
- <span data-ttu-id="6fda2-115">Mais informações sobre [os preços do](pricing.md) plano Azure podem ser encontradas na documentação de preços do [plano Azure.](https://docs.microsoft.com/partner-center/azure-plan-price-list)</span><span class="sxs-lookup"><span data-stu-id="6fda2-115">More information about Azure plan [pricing](pricing.md) can be found in the [Azure plan pricing documentation](https://docs.microsoft.com/partner-center/azure-plan-price-list).</span></span>
- <span data-ttu-id="6fda2-116">Os preços dos parceiros e as APIs cambiais não fazem parte do [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span><span class="sxs-lookup"><span data-stu-id="6fda2-116">Partner pricing and foreign exchange rate APIs are not part of the [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span></span>
- <span data-ttu-id="6fda2-117">Este método devolve os resultados como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="6fda2-117">This method returns results as a file stream.</span></span> <span data-ttu-id="6fda2-118">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="6fda2-118">File stream is either a .csv file or a zip compressed version of the .csv.</span></span> <span data-ttu-id="6fda2-119">Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="6fda2-119">Details about how to request compressed files are included below.</span></span>

## <a name="rest-request"></a><span data-ttu-id="6fda2-120">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="6fda2-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6fda2-121">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fda2-121">Request syntax</span></span>

| <span data-ttu-id="6fda2-122">Método</span><span class="sxs-lookup"><span data-stu-id="6fda2-122">Method</span></span>   | <span data-ttu-id="6fda2-123">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="6fda2-123">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6fda2-124">**Obter**</span><span class="sxs-lookup"><span data-stu-id="6fda2-124">**GET**</span></span> | <span data-ttu-id="6fda2-125"> https://api.partner.microsoft.com/v1.0/sales/fxrates(Month='{month}')/$value</span><span class="sxs-lookup"><span data-stu-id="6fda2-125">https://api.partner.microsoft.com/v1.0/sales/fxrates(Month='{month}')/$value</span></span>                                  |

### <a name="uri-required-parameters"></a><span data-ttu-id="6fda2-126">URI exigia parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fda2-126">URI required parameters</span></span>

<span data-ttu-id="6fda2-127">Use os seguintes parâmetros de caminho para solicitar o mês de taxas de câmbio que deseja.</span><span class="sxs-lookup"><span data-stu-id="6fda2-127">Use the following path parameters to request the month of foreign exchange rates you want.</span></span>

| <span data-ttu-id="6fda2-128">Nome</span><span class="sxs-lookup"><span data-stu-id="6fda2-128">Name</span></span>                   | <span data-ttu-id="6fda2-129">Tipo</span><span class="sxs-lookup"><span data-stu-id="6fda2-129">Type</span></span>     | <span data-ttu-id="6fda2-130">Necessário</span><span class="sxs-lookup"><span data-stu-id="6fda2-130">Required</span></span> | <span data-ttu-id="6fda2-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fda2-131">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="6fda2-132">Mensal</span><span class="sxs-lookup"><span data-stu-id="6fda2-132">Month</span></span>                      | <span data-ttu-id="6fda2-133">string</span><span class="sxs-lookup"><span data-stu-id="6fda2-133">string</span></span>   | <span data-ttu-id="6fda2-134">Sim</span><span class="sxs-lookup"><span data-stu-id="6fda2-134">Yes</span></span>       | <span data-ttu-id="6fda2-135">Deve estar no formato YYYMM.</span><span class="sxs-lookup"><span data-stu-id="6fda2-135">Must be in YYYMM format.</span></span> <span data-ttu-id="6fda2-136">Se omitiu incumprimentos ao mês em curso.</span><span class="sxs-lookup"><span data-stu-id="6fda2-136">If omitted defaults to current month.</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="6fda2-137">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="6fda2-137">Request headers</span></span>

- <span data-ttu-id="6fda2-138">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="6fda2-138">See [Partner REST headers](headers.md) for more information.</span></span>

<span data-ttu-id="6fda2-139">Além dos cabeçalhos acima, os ficheiros podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="6fda2-139">In addition to the above headers, files can be retrieved as compressed reducing bandwidth and download times.</span></span> <span data-ttu-id="6fda2-140">Por predefinição, os ficheiros não são comprimidos.</span><span class="sxs-lookup"><span data-stu-id="6fda2-140">By default the files are not compressed.</span></span> <span data-ttu-id="6fda2-141">Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo.</span><span class="sxs-lookup"><span data-stu-id="6fda2-141">To get compressed versions of the files you can include the below header value.</span></span> <span data-ttu-id="6fda2-142">Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todos os pedidos antes de abril de 2020 só estão disponíveis como não comprimidos.</span><span class="sxs-lookup"><span data-stu-id="6fda2-142">Realize that compressed sheets are only available from April 2020 onward, all requests prior to April 2020 are only available as not compressed.</span></span>

| <span data-ttu-id="6fda2-143">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="6fda2-143">Header</span></span>                   | <span data-ttu-id="6fda2-144">Tipo de Valor</span><span class="sxs-lookup"><span data-stu-id="6fda2-144">Value Type</span></span>     | <span data-ttu-id="6fda2-145">Valor</span><span class="sxs-lookup"><span data-stu-id="6fda2-145">Value</span></span> | <span data-ttu-id="6fda2-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fda2-146">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="6fda2-147">Accept-Encoding</span><span class="sxs-lookup"><span data-stu-id="6fda2-147">Accept-Encoding</span></span>| <span data-ttu-id="6fda2-148">string</span><span class="sxs-lookup"><span data-stu-id="6fda2-148">string</span></span>   | <span data-ttu-id="6fda2-149">esvaziar</span><span class="sxs-lookup"><span data-stu-id="6fda2-149">deflate</span></span>| <span data-ttu-id="6fda2-150">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6fda2-150">Optional.</span></span> <span data-ttu-id="6fda2-151">Se o fluxo de ficheiro omitido não for comprimido.</span><span class="sxs-lookup"><span data-stu-id="6fda2-151">If omitted file stream is not compressed.</span></span>       |

### <a name="request-example"></a><span data-ttu-id="6fda2-152">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="6fda2-152">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/sales/fxrates(Month='201909')/$value HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a><span data-ttu-id="6fda2-153">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="6fda2-153">REST response</span></span>

<span data-ttu-id="6fda2-154">Se for bem sucedido, este método devolve as taxas de câmbio como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="6fda2-154">If successful, this method returns foreign exchange rates as a file stream.</span></span> <span data-ttu-id="6fda2-155">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="6fda2-155">File stream is either a .csv file or a zip compressed version of the .csv.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6fda2-156">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="6fda2-156">Response success and error codes</span></span>

<span data-ttu-id="6fda2-157">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="6fda2-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6fda2-158">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="6fda2-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6fda2-159">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6fda2-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6fda2-160">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="6fda2-160">Response example</span></span>

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 18548
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=fxrates
Request-ID: 65fb6e59-051b-42f7-8771-c8c139b3c901
Date: Wed, 02 Oct 2019 03:42:54 GMT

"CurrencyCode","USDPerUnit","Month"
"AED","0.27224589249009701","2019”
======= Truncated ==============

```
