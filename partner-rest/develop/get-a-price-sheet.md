---
title: Obter uma folha de preços
description: Obtenha uma folha de preços para um determinado mercado e vista. Suporta filtros para obter história por mês.
ms.date: 01/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 5195ebed6559bd71a7832a667e63ee801be1c82f
ms.sourcegitcommit: bb3f5f7ee0489bded86fe52e55018c1f4f5032e2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/07/2020
ms.locfileid: "97770517"
---
# <a name="get-a-price-sheet"></a><span data-ttu-id="1584b-104">Obter uma folha de preços</span><span class="sxs-lookup"><span data-stu-id="1584b-104">Get a price sheet</span></span>

<span data-ttu-id="1584b-105">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="1584b-105">Applies to:</span></span>

- <span data-ttu-id="1584b-106">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="1584b-106">Partner API</span></span>

<span data-ttu-id="1584b-107">Este tópico explica como obter uma folha de preços para um determinado mercado e vista.</span><span class="sxs-lookup"><span data-stu-id="1584b-107">This topic explains how to get a price sheet for a given market and view.</span></span> <span data-ttu-id="1584b-108">Este método suporta filtros para obter história por mês.</span><span class="sxs-lookup"><span data-stu-id="1584b-108">This method supports filters to get history by month.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1584b-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="1584b-109">Prerequisites</span></span>

- <span data-ttu-id="1584b-110">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="1584b-110">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="1584b-111">Este cenário apenas suporta a autenticação do utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="1584b-111">This scenario only supports application user authentication.</span></span> <span data-ttu-id="1584b-112">A aplicação ainda não está suportada.</span><span class="sxs-lookup"><span data-stu-id="1584b-112">Application-ony is not yet supported.</span></span>
- <span data-ttu-id="1584b-113">Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.</span><span class="sxs-lookup"><span data-stu-id="1584b-113">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.</span></span>

## <a name="details"></a><span data-ttu-id="1584b-114">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1584b-114">Details</span></span>

- <span data-ttu-id="1584b-115">Os dados de retornos atuais apenas para o plano Azure de consumo e produtos de reserva.</span><span class="sxs-lookup"><span data-stu-id="1584b-115">Current returns data only for Azure plan consumption and reservation products.</span></span>
- <span data-ttu-id="1584b-116">O [preço](pricing.md) atual inclui todos os contadores e produtos disponíveis durante o mês em curso até à data em que a API é chamada.</span><span class="sxs-lookup"><span data-stu-id="1584b-116">Current [pricing](pricing.md) includes all meters and products available during the current month to the date the API is called.</span></span> <span data-ttu-id="1584b-117">Os meses anteriores incluem todos os contadores e produtos disponíveis para o mês em questão.</span><span class="sxs-lookup"><span data-stu-id="1584b-117">Previous months include all meters and products available for the given month.</span></span>
- <span data-ttu-id="1584b-118">Os preços dos contadores de consumo estão apenas em USD, os parceiros devem usar as taxas de câmbio API para calcular os custos da moeda local.</span><span class="sxs-lookup"><span data-stu-id="1584b-118">Consumption meter prices are only in USD, partners are to use the foreign exchange rates API to calculate local currency costs.</span></span>
- <span data-ttu-id="1584b-119">Os preços dos contadores de consumo são estimados nos preços de venda a retalho.</span><span class="sxs-lookup"><span data-stu-id="1584b-119">Consumption meter prices are estimated retail prices.</span></span> <span data-ttu-id="1584b-120">Os descontos para parceiros estão disponíveis através do [crédito adquirido pelo parceiro.](https://docs.microsoft.com/partner-center/partner-earned-credit-explanation)</span><span class="sxs-lookup"><span data-stu-id="1584b-120">Partner discounts are available via [partner earned credit](https://docs.microsoft.com/partner-center/partner-earned-credit-explanation).</span></span>
- <span data-ttu-id="1584b-121">Os preços dos contadores de reservas incluem os descontos para parceiros da CSP.</span><span class="sxs-lookup"><span data-stu-id="1584b-121">Reservations meter prices include the CSP partner discounts.</span></span> <span data-ttu-id="1584b-122">Os preços estimados de venda a retalho para reservas podem ser encontrados nas reservas de serviços partilhados que são descarregados a partir da página "Preços e ofertas" do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="1584b-122">Estimated retail prices for reservations can be found in the reservations shared services downloadable from the Partner Center "Pricing and offers" page.</span></span>
- <span data-ttu-id="1584b-123">Mais informações sobre os preços do plano Azure podem ser encontradas na documentação de preços do [plano Azure.](https://docs.microsoft.com/partner-center/azure-plan-price-list)</span><span class="sxs-lookup"><span data-stu-id="1584b-123">More information about Azure plan pricing can be found in the [Azure plan pricing documentation](https://docs.microsoft.com/partner-center/azure-plan-price-list).</span></span>
- <span data-ttu-id="1584b-124">Os preços dos parceiros e as APIs cambiais não fazem parte do [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span><span class="sxs-lookup"><span data-stu-id="1584b-124">Partner pricing and foreign exchange rate APIs are not part of the [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span></span>
- <span data-ttu-id="1584b-125">Este método devolve a lista de preços como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="1584b-125">This method returns the price list as a file stream.</span></span> <span data-ttu-id="1584b-126">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="1584b-126">File stream is either a .csv file or a zip compressed version of the .csv.</span></span> <span data-ttu-id="1584b-127">Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="1584b-127">Details about how to request compressed files are included below.</span></span>

## <a name="rest-request"></a><span data-ttu-id="1584b-128">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="1584b-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1584b-129">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="1584b-129">Request syntax</span></span>

| <span data-ttu-id="1584b-130">Método</span><span class="sxs-lookup"><span data-stu-id="1584b-130">Method</span></span>   | <span data-ttu-id="1584b-131">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="1584b-131">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1584b-132">**Obter**</span><span class="sxs-lookup"><span data-stu-id="1584b-132">**GET**</span></span> | <span data-ttu-id="1584b-133"> https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value</span><span class="sxs-lookup"><span data-stu-id="1584b-133">https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value</span></span>                                     |

### <a name="uri-required-parameters"></a><span data-ttu-id="1584b-134">URI exigia parâmetros</span><span class="sxs-lookup"><span data-stu-id="1584b-134">URI required parameters</span></span>

<span data-ttu-id="1584b-135">Utilize os seguintes parâmetros de percurso para solicitar qual o mercado e o tipo de folha de preços que pretende.</span><span class="sxs-lookup"><span data-stu-id="1584b-135">Use the following path parameters to request which market and type of price sheet you want.</span></span>

| <span data-ttu-id="1584b-136">Nome</span><span class="sxs-lookup"><span data-stu-id="1584b-136">Name</span></span>                   | <span data-ttu-id="1584b-137">Tipo</span><span class="sxs-lookup"><span data-stu-id="1584b-137">Type</span></span>     | <span data-ttu-id="1584b-138">Necessário</span><span class="sxs-lookup"><span data-stu-id="1584b-138">Required</span></span> | <span data-ttu-id="1584b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="1584b-139">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="1584b-140">Mercado</span><span class="sxs-lookup"><span data-stu-id="1584b-140">Market</span></span>                      | <span data-ttu-id="1584b-141">string</span><span class="sxs-lookup"><span data-stu-id="1584b-141">string</span></span>   | <span data-ttu-id="1584b-142">Sim</span><span class="sxs-lookup"><span data-stu-id="1584b-142">Yes</span></span>       | <span data-ttu-id="1584b-143">Código de país de duas letras para o mercado a ser solicitado</span><span class="sxs-lookup"><span data-stu-id="1584b-143">Two letter country code for the market being requested</span></span>       |
|<span data-ttu-id="1584b-144">Folha de preçosVereja</span><span class="sxs-lookup"><span data-stu-id="1584b-144">PricesheetView</span></span> | <span data-ttu-id="1584b-145">string</span><span class="sxs-lookup"><span data-stu-id="1584b-145">string</span></span>   | <span data-ttu-id="1584b-146">Sim</span><span class="sxs-lookup"><span data-stu-id="1584b-146">Yes</span></span>       | <span data-ttu-id="1584b-147">O tipo de folha de preços solicitada, isto pode ser azure_consumption ou azure_reservations</span><span class="sxs-lookup"><span data-stu-id="1584b-147">The type of price sheet being requested, this can be azure_consumption or azure_reservations</span></span>       |

### <a name="uri-filter-parameters"></a><span data-ttu-id="1584b-148">Parâmetros de filtro URI</span><span class="sxs-lookup"><span data-stu-id="1584b-148">URI filter parameters</span></span>

<span data-ttu-id="1584b-149">Utilize os seguintes parâmetros de filtro.</span><span class="sxs-lookup"><span data-stu-id="1584b-149">Use the following filter parameters.</span></span>

| <span data-ttu-id="1584b-150">Nome</span><span class="sxs-lookup"><span data-stu-id="1584b-150">Name</span></span>                   | <span data-ttu-id="1584b-151">Tipo</span><span class="sxs-lookup"><span data-stu-id="1584b-151">Type</span></span>     | <span data-ttu-id="1584b-152">Necessário</span><span class="sxs-lookup"><span data-stu-id="1584b-152">Required</span></span> | <span data-ttu-id="1584b-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="1584b-153">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="1584b-154">Linha cronológica</span><span class="sxs-lookup"><span data-stu-id="1584b-154">Timeline</span></span>| <span data-ttu-id="1584b-155">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="1584b-155">string</span></span>   | <span data-ttu-id="1584b-156">No</span><span class="sxs-lookup"><span data-stu-id="1584b-156">No</span></span>| <span data-ttu-id="1584b-157">Predefinições à corrente se não for aprovada.</span><span class="sxs-lookup"><span data-stu-id="1584b-157">Defaults to current if not passed.</span></span> <span data-ttu-id="1584b-158">Os valores possíveis são a história, a corrente e o futuro.</span><span class="sxs-lookup"><span data-stu-id="1584b-158">Possible values are history, current and future.</span></span>       |
|<span data-ttu-id="1584b-159">Mensal</span><span class="sxs-lookup"><span data-stu-id="1584b-159">Month</span></span>| <span data-ttu-id="1584b-160">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="1584b-160">string</span></span>   | <span data-ttu-id="1584b-161">No</span><span class="sxs-lookup"><span data-stu-id="1584b-161">No</span></span>| <span data-ttu-id="1584b-162">Só é necessário que o histórico seja solicitado, deve aderir à YYYYMM para a folha de preços solicitada.</span><span class="sxs-lookup"><span data-stu-id="1584b-162">Only required if history is requested, must adhere to YYYYMM for the price sheet being requested.</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="1584b-163">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="1584b-163">Request headers</span></span>

- <span data-ttu-id="1584b-164">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="1584b-164">See [Partner REST headers](headers.md) for more information.</span></span>

<span data-ttu-id="1584b-165">Além dos cabeçalhos acima, os ficheiros de preços podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="1584b-165">In addition to the above headers, pricing files can be retrieved as compressed reducing bandwidth and download times.</span></span> <span data-ttu-id="1584b-166">Por predefinição, os ficheiros não são comprimidos.</span><span class="sxs-lookup"><span data-stu-id="1584b-166">By default the files are not compressed.</span></span> <span data-ttu-id="1584b-167">Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo.</span><span class="sxs-lookup"><span data-stu-id="1584b-167">To get compressed versions of the files you can include the below header value.</span></span> <span data-ttu-id="1584b-168">Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todas as folhas antes de abril de 2020 só estão disponíveis como não comprimidos.</span><span class="sxs-lookup"><span data-stu-id="1584b-168">Realize that compressed sheets are only available from April 2020 onward, all sheets prior to April 2020 are only available as not compressed.</span></span>

| <span data-ttu-id="1584b-169">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="1584b-169">Header</span></span>                   | <span data-ttu-id="1584b-170">Tipo de Valor</span><span class="sxs-lookup"><span data-stu-id="1584b-170">Value Type</span></span>     | <span data-ttu-id="1584b-171">Valor</span><span class="sxs-lookup"><span data-stu-id="1584b-171">Value</span></span> | <span data-ttu-id="1584b-172">Descrição</span><span class="sxs-lookup"><span data-stu-id="1584b-172">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="1584b-173">Accept-Encoding</span><span class="sxs-lookup"><span data-stu-id="1584b-173">Accept-Encoding</span></span>| <span data-ttu-id="1584b-174">string</span><span class="sxs-lookup"><span data-stu-id="1584b-174">string</span></span>   | <span data-ttu-id="1584b-175">esvaziar</span><span class="sxs-lookup"><span data-stu-id="1584b-175">deflate</span></span>| <span data-ttu-id="1584b-176">Opcional.</span><span class="sxs-lookup"><span data-stu-id="1584b-176">Optional.</span></span> <span data-ttu-id="1584b-177">Se o fluxo de ficheiro omitido não for comprimido.</span><span class="sxs-lookup"><span data-stu-id="1584b-177">If omitted file stream is not compressed.</span></span>       |

### <a name="request-example"></a><span data-ttu-id="1584b-178">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="1584b-178">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='ad',PricesheetView='azure_consumption')/$value?timeline=history&month=201909 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a><span data-ttu-id="1584b-179">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="1584b-179">REST response</span></span>

<span data-ttu-id="1584b-180">Se for bem sucedido, este método devolve a lista de preços como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="1584b-180">If successful, this method returns the price list as a file stream.</span></span> <span data-ttu-id="1584b-181">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="1584b-181">File stream is either a .csv file or a zip compressed version of the .csv.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1584b-182">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="1584b-182">Response success and error codes</span></span>

<span data-ttu-id="1584b-183">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="1584b-183">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1584b-184">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="1584b-184">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1584b-185">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="1584b-185">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1584b-186">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="1584b-186">Response example</span></span>

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 42180180
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=pricesheet
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
Date: Wed, 02 Oct 2019 03:41:20 GMT

"ProductTitle","ProductId","SkuId","SkuTitle","Publisher","SkuDescription","UnitOfMeasure","TermDuration","Market","Currency","UnitPrice","PricingTierRangeMin","PricingTierRangeMax","EffectiveStartDate","EffectiveEndDate","MeterIds","MeterType","Tags“
"Advanced Data Security - SQL Database","DZH318Z0C16V","001J","Advanced Data Security - SQL Database - Standard - US East 2","Microsoft","Advanced Data Security - SQL Database - Standard - US East 2","1 Node/Month","payG-1","US","USD","15","","","3/1/2018 12:00:00 AM","11/30/9999 11:59:59 PM","cb0969aa-aaaa-4d6c-ab4b-7e182fa06aff","1 Node/Month","Azure“
======= Truncated ==============

```
