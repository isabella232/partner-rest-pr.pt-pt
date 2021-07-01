---
title: Obtenha uma matriz de oferta
description: Obtenha uma matriz de oferta para uma data dada. Suporta filtros para obter história por mês.
ms.date: 02/11/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: e53276c1170febab002d35a42c88c1f96f7b7428
ms.sourcegitcommit: 9e64d6358ef4e1ac2d3e0d36cd63490a5f760b38
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113131304"
---
# <a name="get-an-offer-matrix"></a><span data-ttu-id="edb8d-104">Obtenha uma matriz de oferta</span><span class="sxs-lookup"><span data-stu-id="edb8d-104">Get an offer matrix</span></span>

<span data-ttu-id="edb8d-105">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="edb8d-105">Applies to:</span></span>

- <span data-ttu-id="edb8d-106">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="edb8d-106">Partner API</span></span>
- <span data-ttu-id="edb8d-107">O M365/D365 New Commerce experimenta pré-visualização técnica.</span><span class="sxs-lookup"><span data-stu-id="edb8d-107">The M365/D365 New Commerce experience technical preview.</span></span> <span data-ttu-id="edb8d-108">As mudanças abaixo do Novo Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência técnica M365/D365.</span><span class="sxs-lookup"><span data-stu-id="edb8d-108">The below New Commerce changes are currently available only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span>

<span data-ttu-id="edb8d-109">Este tópico explica como obter uma matriz de oferta por um dado mês.</span><span class="sxs-lookup"><span data-stu-id="edb8d-109">This topic explains how to get an offer matrix for a given month.</span></span> <span data-ttu-id="edb8d-110">A matriz de oferta inclui propriedades e regras de compra para os produtos e skus.</span><span class="sxs-lookup"><span data-stu-id="edb8d-110">The offer matrix includes properties and purchase rules for the products and skus.</span></span> <span data-ttu-id="edb8d-111">Este método suporta filtros para obter história por mês.</span><span class="sxs-lookup"><span data-stu-id="edb8d-111">This method supports filters to get history by month.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="edb8d-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="edb8d-112">Prerequisites</span></span>

- <span data-ttu-id="edb8d-113">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="edb8d-113">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="edb8d-114">Este cenário apenas suporta a autenticação do utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="edb8d-114">This scenario only supports application user authentication.</span></span> <span data-ttu-id="edb8d-115">Só a candidatura ainda não está apoiada.</span><span class="sxs-lookup"><span data-stu-id="edb8d-115">Application-only is not yet supported.</span></span> <span data-ttu-id="edb8d-116">Os parceiros que **experimentem o erro http:400** devem consultar a [documentação de autenticação da API do Parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="edb8d-116">Partners that experience **http error:400** should consult the [Partner API authentication](api-authentication.md) documentation.</span></span>
- <span data-ttu-id="edb8d-117">Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.</span><span class="sxs-lookup"><span data-stu-id="edb8d-117">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.</span></span>

## <a name="details"></a><span data-ttu-id="edb8d-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="edb8d-118">Details</span></span>

- <span data-ttu-id="edb8d-119">Os dados de devoluções atuais apenas para novos produtos baseados em licenças de comércio atualizados.</span><span class="sxs-lookup"><span data-stu-id="edb8d-119">Current returns data only for updated new commerce license-based products.</span></span>
- <span data-ttu-id="edb8d-120">Os preços atuais incluem produtos disponíveis durante o mês em curso até à data em que a API é chamada.</span><span class="sxs-lookup"><span data-stu-id="edb8d-120">Current pricing includes products available during the current month to the date the API is called.</span></span> <span data-ttu-id="edb8d-121">Os meses anteriores incluem a data a partir do último dia do mês selecionado.</span><span class="sxs-lookup"><span data-stu-id="edb8d-121">Previous months include date as of the last day of the selected month.</span></span>
- <span data-ttu-id="edb8d-122">Este método devolve os dados como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="edb8d-122">This method returns data as a file stream.</span></span> <span data-ttu-id="edb8d-123">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="edb8d-123">File stream is either a .csv file or a zip compressed version of the .csv.</span></span> <span data-ttu-id="edb8d-124">Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="edb8d-124">Details about how to request compressed files are included below.</span></span>

## <a name="rest-request"></a><span data-ttu-id="edb8d-125">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="edb8d-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="edb8d-126">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="edb8d-126">Request syntax</span></span>

| <span data-ttu-id="edb8d-127">Método</span><span class="sxs-lookup"><span data-stu-id="edb8d-127">Method</span></span>   | <span data-ttu-id="edb8d-128">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="edb8d-128">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="edb8d-129">**Obter**</span><span class="sxs-lookup"><span data-stu-id="edb8d-129">**GET**</span></span> | <span data-ttu-id="edb8d-130"> https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='{date}')/$value</span><span class="sxs-lookup"><span data-stu-id="edb8d-130">https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='{date}')/$value</span></span> |

### <a name="uri-filter-parameters"></a><span data-ttu-id="edb8d-131">Parâmetros de filtro URI</span><span class="sxs-lookup"><span data-stu-id="edb8d-131">URI filter parameters</span></span>

<span data-ttu-id="edb8d-132">Utilize os seguintes parâmetros de filtro.</span><span class="sxs-lookup"><span data-stu-id="edb8d-132">Use the following filter parameters.</span></span>

| <span data-ttu-id="edb8d-133">Nome</span><span class="sxs-lookup"><span data-stu-id="edb8d-133">Name</span></span>                   | <span data-ttu-id="edb8d-134">Tipo</span><span class="sxs-lookup"><span data-stu-id="edb8d-134">Type</span></span>     | <span data-ttu-id="edb8d-135">Necessário</span><span class="sxs-lookup"><span data-stu-id="edb8d-135">Required</span></span> | <span data-ttu-id="edb8d-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="edb8d-136">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="edb8d-137">Mensal</span><span class="sxs-lookup"><span data-stu-id="edb8d-137">Month</span></span>| <span data-ttu-id="edb8d-138">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="edb8d-138">string</span></span>   | <span data-ttu-id="edb8d-139">No</span><span class="sxs-lookup"><span data-stu-id="edb8d-139">No</span></span> | <span data-ttu-id="edb8d-140">Deve aderir à YYYYMM para a folha de preços solicitada.</span><span class="sxs-lookup"><span data-stu-id="edb8d-140">Must adhere to YYYYMM for the price sheet being requested.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="edb8d-141">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="edb8d-141">Request headers</span></span>

- <span data-ttu-id="edb8d-142">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="edb8d-142">See [Partner REST headers](headers.md) for more information.</span></span>

<span data-ttu-id="edb8d-143">Além dos cabeçalhos acima, os ficheiros de preços podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="edb8d-143">In addition to the above headers, pricing files can be retrieved as compressed reducing bandwidth and download times.</span></span> <span data-ttu-id="edb8d-144">Por predefinição, os ficheiros não são comprimidos.</span><span class="sxs-lookup"><span data-stu-id="edb8d-144">By default the files are not compressed.</span></span> <span data-ttu-id="edb8d-145">Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo.</span><span class="sxs-lookup"><span data-stu-id="edb8d-145">To get compressed versions of the files you can include the below header value.</span></span> <span data-ttu-id="edb8d-146">Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todas as folhas antes de abril de 2020 só estão disponíveis como não comprimidos.</span><span class="sxs-lookup"><span data-stu-id="edb8d-146">Realize that compressed sheets are only available from April 2020 onward, all sheets prior to April 2020 are only available as not compressed.</span></span>

| <span data-ttu-id="edb8d-147">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="edb8d-147">Header</span></span>                   | <span data-ttu-id="edb8d-148">Tipo de Valor</span><span class="sxs-lookup"><span data-stu-id="edb8d-148">Value Type</span></span>     | <span data-ttu-id="edb8d-149">Valor</span><span class="sxs-lookup"><span data-stu-id="edb8d-149">Value</span></span> | <span data-ttu-id="edb8d-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="edb8d-150">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="edb8d-151">Accept-Encoding</span><span class="sxs-lookup"><span data-stu-id="edb8d-151">Accept-Encoding</span></span>| <span data-ttu-id="edb8d-152">string</span><span class="sxs-lookup"><span data-stu-id="edb8d-152">string</span></span>   | <span data-ttu-id="edb8d-153">esvaziar</span><span class="sxs-lookup"><span data-stu-id="edb8d-153">deflate</span></span>| <span data-ttu-id="edb8d-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="edb8d-154">Optional.</span></span> <span data-ttu-id="edb8d-155">Se o fluxo de ficheiro omitido não for comprimido.</span><span class="sxs-lookup"><span data-stu-id="edb8d-155">If omitted file stream is not compressed.</span></span>       |

### <a name="request-example"></a><span data-ttu-id="edb8d-156">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="edb8d-156">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='202101')/$value HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a><span data-ttu-id="edb8d-157">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="edb8d-157">REST response</span></span>

<span data-ttu-id="edb8d-158">Se for bem sucedido, este método devolve uma matriz de oferta como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="edb8d-158">If successful, this method returns an offer matrix as a file stream.</span></span> <span data-ttu-id="edb8d-159">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="edb8d-159">File stream is either a .csv file or a zip compressed version of the .csv.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="edb8d-160">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="edb8d-160">Response success and error codes</span></span>

<span data-ttu-id="edb8d-161">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="edb8d-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="edb8d-162">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="edb8d-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="edb8d-163">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="edb8d-163">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="edb8d-164">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="edb8d-164">Response example</span></span>

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 42180180
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=updatedoffice.csv
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
Date: Wed, 02 Feb 2021 03:41:20 GMT

"ProductTitle","ProductId","SkuId","SkuTitle","ProvisioningId","ProvisioningString","MinLicenses","MaxLicenses","AssetOwnershipLimit","AssetOwnershipLimitType","ProductSkuPreRequisites","ProductSkuConversion","Description","AllowedCountries" 
"Microsoft 365 Business Basic","CFQ7TTC0LH18","0001","Microsoft 365 Business Basic","3b555118-da6a-4418-894f-7df1e2096870","O365_BUSINESS_ESSENTIALS","1","300","2","ConcurrentCount","","CFQ7TTC0LDPB/0001,CFQ7TTC0LF8Q/0001","Best for businesses that need professional...","AD;AE;AF;AG;AI;AL;AM;AO..."
======= Truncated ==============

```
