---
title: Obter uma folha de preços
description: Obtenha uma folha de preços para um determinado mercado e vista. Suporta filtros para obter história por mês.
ms.date: 01/24/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 7571e8fce861dbfe463000a1ac4094115af08ffa
ms.sourcegitcommit: 9e64d6358ef4e1ac2d3e0d36cd63490a5f760b38
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2021
ms.locfileid: "113125521"
---
# <a name="get-a-price-sheet"></a><span data-ttu-id="dbe57-104">Obter uma folha de preços</span><span class="sxs-lookup"><span data-stu-id="dbe57-104">Get a price sheet</span></span>

<span data-ttu-id="dbe57-105">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="dbe57-105">Applies to:</span></span>

- <span data-ttu-id="dbe57-106">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="dbe57-106">Partner API</span></span>

<span data-ttu-id="dbe57-107">Este tópico explica como obter uma folha de preços para um determinado mercado e vista.</span><span class="sxs-lookup"><span data-stu-id="dbe57-107">This topic explains how to get a price sheet for a given market and view.</span></span> <span data-ttu-id="dbe57-108">Este método suporta filtros para obter história por mês.</span><span class="sxs-lookup"><span data-stu-id="dbe57-108">This method supports filters to get history by month.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbe57-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dbe57-109">Prerequisites</span></span>

- <span data-ttu-id="dbe57-110">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="dbe57-110">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="dbe57-111">Este cenário apenas suporta a autenticação do utilizador da aplicação.</span><span class="sxs-lookup"><span data-stu-id="dbe57-111">This scenario only supports application user authentication.</span></span> <span data-ttu-id="dbe57-112">Só a candidatura ainda não está apoiada.</span><span class="sxs-lookup"><span data-stu-id="dbe57-112">Application-only is not yet supported.</span></span> <span data-ttu-id="dbe57-113">Os parceiros que **experimentem o erro http:400** devem consultar a [documentação de autenticação da API do Parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="dbe57-113">Partners that experience **http error:400** should consult the [Partner API authentication](api-authentication.md) documentation.</span></span>
- <span data-ttu-id="dbe57-114">Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.</span><span class="sxs-lookup"><span data-stu-id="dbe57-114">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Admin Agent or Sales Agent.</span></span>

## <a name="details"></a><span data-ttu-id="dbe57-115">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dbe57-115">Details</span></span>

- <span data-ttu-id="dbe57-116">Os dados de retornos atuais apenas para o plano Azure de consumo e produtos de reserva.</span><span class="sxs-lookup"><span data-stu-id="dbe57-116">Current returns data only for Azure plan consumption and reservation products.</span></span>
- <span data-ttu-id="dbe57-117">O [preço](pricing.md) atual inclui todos os contadores e produtos disponíveis durante o mês em curso até à data em que a API é chamada.</span><span class="sxs-lookup"><span data-stu-id="dbe57-117">Current [pricing](pricing.md) includes all meters and products available during the current month to the date the API is called.</span></span> <span data-ttu-id="dbe57-118">Os meses anteriores incluem todos os contadores e produtos disponíveis para o mês em questão.</span><span class="sxs-lookup"><span data-stu-id="dbe57-118">Previous months include all meters and products available for the given month.</span></span>
- <span data-ttu-id="dbe57-119">Os preços dos contadores de consumo estão apenas em USD, os parceiros devem usar as taxas de câmbio API para calcular os custos da moeda local.</span><span class="sxs-lookup"><span data-stu-id="dbe57-119">Consumption meter prices are only in USD, partners are to use the foreign exchange rates API to calculate local currency costs.</span></span>
- <span data-ttu-id="dbe57-120">Os preços dos contadores de consumo são estimados nos preços de venda a retalho.</span><span class="sxs-lookup"><span data-stu-id="dbe57-120">Consumption meter prices are estimated retail prices.</span></span> <span data-ttu-id="dbe57-121">Os descontos para parceiros estão disponíveis através do [crédito adquirido pelo parceiro.](https://docs.microsoft.com/partner-center/partner-earned-credit-explanation)</span><span class="sxs-lookup"><span data-stu-id="dbe57-121">Partner discounts are available via [partner earned credit](https://docs.microsoft.com/partner-center/partner-earned-credit-explanation).</span></span>
- <span data-ttu-id="dbe57-122">Os preços dos contadores de reservas incluem os descontos para parceiros da CSP.</span><span class="sxs-lookup"><span data-stu-id="dbe57-122">Reservations meter prices include the CSP partner discounts.</span></span> <span data-ttu-id="dbe57-123">Os preços estimados de venda a retalho para reservas podem ser encontrados nas reservas de serviços partilhados que são descarregados a partir da página "Preços e ofertas" do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="dbe57-123">Estimated retail prices for reservations can be found in the reservations shared services downloadable from the Partner Center "Pricing and offers" page.</span></span>
- <span data-ttu-id="dbe57-124">Mais informações sobre os preços do plano Azure podem ser encontradas na documentação de preços do [plano Azure.](https://docs.microsoft.com/partner-center/azure-plan-price-list)</span><span class="sxs-lookup"><span data-stu-id="dbe57-124">More information about Azure plan pricing can be found in the [Azure plan pricing documentation](https://docs.microsoft.com/partner-center/azure-plan-price-list).</span></span>
- <span data-ttu-id="dbe57-125">Os preços dos parceiros e as APIs cambiais não fazem parte do [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span><span class="sxs-lookup"><span data-stu-id="dbe57-125">Partner pricing and foreign exchange rate APIs are not part of the [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).</span></span>
- <span data-ttu-id="dbe57-126">Este método devolve a lista de preços como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="dbe57-126">This method returns the price list as a file stream.</span></span> <span data-ttu-id="dbe57-127">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="dbe57-127">File stream is either a .csv file or a zip compressed version of the .csv.</span></span> <span data-ttu-id="dbe57-128">Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbe57-128">Details about how to request compressed files are included below.</span></span>

## <a name="rest-request"></a><span data-ttu-id="dbe57-129">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="dbe57-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="dbe57-130">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="dbe57-130">Request syntax</span></span>

| <span data-ttu-id="dbe57-131">Método</span><span class="sxs-lookup"><span data-stu-id="dbe57-131">Method</span></span>   | <span data-ttu-id="dbe57-132">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="dbe57-132">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="dbe57-133">**Obter**</span><span class="sxs-lookup"><span data-stu-id="dbe57-133">**GET**</span></span> | <span data-ttu-id="dbe57-134"> https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value</span><span class="sxs-lookup"><span data-stu-id="dbe57-134">https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value</span></span>                                     |

### <a name="uri-required-parameters"></a><span data-ttu-id="dbe57-135">URI exigia parâmetros</span><span class="sxs-lookup"><span data-stu-id="dbe57-135">URI required parameters</span></span>

<span data-ttu-id="dbe57-136">Utilize os seguintes parâmetros de percurso para solicitar qual o mercado e o tipo de folha de preços que pretende.</span><span class="sxs-lookup"><span data-stu-id="dbe57-136">Use the following path parameters to request which market and type of price sheet you want.</span></span>

| <span data-ttu-id="dbe57-137">Nome</span><span class="sxs-lookup"><span data-stu-id="dbe57-137">Name</span></span>                   | <span data-ttu-id="dbe57-138">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbe57-138">Type</span></span>     | <span data-ttu-id="dbe57-139">Necessário</span><span class="sxs-lookup"><span data-stu-id="dbe57-139">Required</span></span> | <span data-ttu-id="dbe57-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbe57-140">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="dbe57-141">Mercado</span><span class="sxs-lookup"><span data-stu-id="dbe57-141">Market</span></span>                      | <span data-ttu-id="dbe57-142">string</span><span class="sxs-lookup"><span data-stu-id="dbe57-142">string</span></span>   | <span data-ttu-id="dbe57-143">Yes</span><span class="sxs-lookup"><span data-stu-id="dbe57-143">Yes</span></span>       | <span data-ttu-id="dbe57-144">Código de país de duas letras para o mercado a ser solicitado</span><span class="sxs-lookup"><span data-stu-id="dbe57-144">Two letter country code for the market being requested</span></span>       |
|<span data-ttu-id="dbe57-145">Folha de preçosVereja</span><span class="sxs-lookup"><span data-stu-id="dbe57-145">PricesheetView</span></span> | <span data-ttu-id="dbe57-146">string</span><span class="sxs-lookup"><span data-stu-id="dbe57-146">string</span></span>   | <span data-ttu-id="dbe57-147">Yes</span><span class="sxs-lookup"><span data-stu-id="dbe57-147">Yes</span></span>       | <span data-ttu-id="dbe57-148">O tipo de folha de preços solicitada, pode ser azure_consumption, azure_reservations ou atualizado.</span><span class="sxs-lookup"><span data-stu-id="dbe57-148">The type of price sheet being requested, this can be azure_consumption, azure_reservations or updatedlicensebased.</span></span>  |

> [!Note]
> <span data-ttu-id="dbe57-149">Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.</span><span class="sxs-lookup"><span data-stu-id="dbe57-149">updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span>

### <a name="uri-filter-parameters"></a><span data-ttu-id="dbe57-150">Parâmetros de filtro URI</span><span class="sxs-lookup"><span data-stu-id="dbe57-150">URI filter parameters</span></span>

<span data-ttu-id="dbe57-151">Utilize os seguintes parâmetros de filtro.</span><span class="sxs-lookup"><span data-stu-id="dbe57-151">Use the following filter parameters.</span></span>

| <span data-ttu-id="dbe57-152">Nome</span><span class="sxs-lookup"><span data-stu-id="dbe57-152">Name</span></span>                   | <span data-ttu-id="dbe57-153">Tipo</span><span class="sxs-lookup"><span data-stu-id="dbe57-153">Type</span></span>     | <span data-ttu-id="dbe57-154">Necessário</span><span class="sxs-lookup"><span data-stu-id="dbe57-154">Required</span></span> | <span data-ttu-id="dbe57-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbe57-155">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="dbe57-156">Linha cronológica</span><span class="sxs-lookup"><span data-stu-id="dbe57-156">Timeline</span></span>| <span data-ttu-id="dbe57-157">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="dbe57-157">string</span></span>   | <span data-ttu-id="dbe57-158">No</span><span class="sxs-lookup"><span data-stu-id="dbe57-158">No</span></span>| <span data-ttu-id="dbe57-159">Predefinições à corrente se não for aprovada.</span><span class="sxs-lookup"><span data-stu-id="dbe57-159">Defaults to current if not passed.</span></span> <span data-ttu-id="dbe57-160">Os valores possíveis são a história, a corrente e o futuro.</span><span class="sxs-lookup"><span data-stu-id="dbe57-160">Possible values are history, current and future.</span></span>       |
|<span data-ttu-id="dbe57-161">Mensal</span><span class="sxs-lookup"><span data-stu-id="dbe57-161">Month</span></span>| <span data-ttu-id="dbe57-162">cadeia (de carateres)</span><span class="sxs-lookup"><span data-stu-id="dbe57-162">string</span></span>   | <span data-ttu-id="dbe57-163">No</span><span class="sxs-lookup"><span data-stu-id="dbe57-163">No</span></span>| <span data-ttu-id="dbe57-164">Só é necessário que o histórico seja solicitado, deve aderir à YYYYMM para a folha de preços solicitada.</span><span class="sxs-lookup"><span data-stu-id="dbe57-164">Only required if history is requested, must adhere to YYYYMM for the price sheet being requested.</span></span>       |

### <a name="request-headers"></a><span data-ttu-id="dbe57-165">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="dbe57-165">Request headers</span></span>

- <span data-ttu-id="dbe57-166">Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="dbe57-166">See [Partner REST headers](headers.md) for more information.</span></span>

<span data-ttu-id="dbe57-167">Além dos cabeçalhos acima, os ficheiros de preços podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento.</span><span class="sxs-lookup"><span data-stu-id="dbe57-167">In addition to the above headers, pricing files can be retrieved as compressed reducing bandwidth and download times.</span></span> <span data-ttu-id="dbe57-168">Por predefinição, os ficheiros não são comprimidos.</span><span class="sxs-lookup"><span data-stu-id="dbe57-168">By default the files are not compressed.</span></span> <span data-ttu-id="dbe57-169">Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbe57-169">To get compressed versions of the files you can include the below header value.</span></span> <span data-ttu-id="dbe57-170">Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todas as folhas antes de abril de 2020 só estão disponíveis como não comprimidos.</span><span class="sxs-lookup"><span data-stu-id="dbe57-170">Realize that compressed sheets are only available from April 2020 onward, all sheets prior to April 2020 are only available as not compressed.</span></span>

| <span data-ttu-id="dbe57-171">Cabeçalho</span><span class="sxs-lookup"><span data-stu-id="dbe57-171">Header</span></span>                   | <span data-ttu-id="dbe57-172">Tipo de Valor</span><span class="sxs-lookup"><span data-stu-id="dbe57-172">Value Type</span></span>     | <span data-ttu-id="dbe57-173">Valor</span><span class="sxs-lookup"><span data-stu-id="dbe57-173">Value</span></span> | <span data-ttu-id="dbe57-174">Descrição</span><span class="sxs-lookup"><span data-stu-id="dbe57-174">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|<span data-ttu-id="dbe57-175">Accept-Encoding</span><span class="sxs-lookup"><span data-stu-id="dbe57-175">Accept-Encoding</span></span>| <span data-ttu-id="dbe57-176">string</span><span class="sxs-lookup"><span data-stu-id="dbe57-176">string</span></span>   | <span data-ttu-id="dbe57-177">esvaziar</span><span class="sxs-lookup"><span data-stu-id="dbe57-177">deflate</span></span>| <span data-ttu-id="dbe57-178">Opcional.</span><span class="sxs-lookup"><span data-stu-id="dbe57-178">Optional.</span></span> <span data-ttu-id="dbe57-179">Se o fluxo de ficheiro omitido não for comprimido.</span><span class="sxs-lookup"><span data-stu-id="dbe57-179">If omitted file stream is not compressed.</span></span>       |

### <a name="request-example"></a><span data-ttu-id="dbe57-180">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="dbe57-180">Request example</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='ad',PricesheetView='azure_consumption')/$value?timeline=history&month=201909 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```
### <a name="request-example-for-new-commerce"></a><span data-ttu-id="dbe57-181">Exemplo de pedido para novo comércio</span><span class="sxs-lookup"><span data-stu-id="dbe57-181">Request example for new commerce</span></span>

> [!Note]
> <span data-ttu-id="dbe57-182">Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.</span><span class="sxs-lookup"><span data-stu-id="dbe57-182">updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span>

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='US',PricesheetView='updatedlicensebased')/$value?timeline=history&month=202101 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a><span data-ttu-id="dbe57-183">Resposta do REST</span><span class="sxs-lookup"><span data-stu-id="dbe57-183">REST response</span></span>

<span data-ttu-id="dbe57-184">Se for bem sucedido, este método devolve a lista de preços como um fluxo de ficheiros.</span><span class="sxs-lookup"><span data-stu-id="dbe57-184">If successful, this method returns the price list as a file stream.</span></span> <span data-ttu-id="dbe57-185">O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.</span><span class="sxs-lookup"><span data-stu-id="dbe57-185">File stream is either a .csv file or a zip compressed version of the .csv.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="dbe57-186">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="dbe57-186">Response success and error codes</span></span>

<span data-ttu-id="dbe57-187">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="dbe57-187">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="dbe57-188">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="dbe57-188">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="dbe57-189">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="dbe57-189">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="dbe57-190">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="dbe57-190">Response example</span></span>

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

### <a name="response-example-for-new-commerce"></a><span data-ttu-id="dbe57-191">Exemplo de resposta para novo comércio</span><span class="sxs-lookup"><span data-stu-id="dbe57-191">Response example for new commerce</span></span>

> [!Note]
> <span data-ttu-id="dbe57-192">Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.</span><span class="sxs-lookup"><span data-stu-id="dbe57-192">updatedlicensebased PriceSheetView is currently available only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span>

``` http
HTTP/1.1 200 OK
Cache-Control: private
Content-Length: 42180180
Content-Type: application/octet-stream
Content-Disposition: attachment; filename=sheets.csv
Request-ID: 9f8bed52-e4df-4d0c-9ca6-929a187b0731
Date: Wed, 02 Feb 2021 03:41:20 GMT

"ProductTitle","ProductId","SkuId","SkuTitle","Publisher","SkuDescription","UnitOfMeasure","TermDuration","BillingPlan","Market","Currency","UnitPrice","PricingTierRangeMin","PricingTierRangeMax","EffectiveStartDate","EffectiveEndDate","Tags","ERP Price“
"Advanced Communications","CFQ7TTC0HDK0","0001","Advanced Communications","Microsoft Corporation","Advanced meetings, calling, workflow integration, and management tools for IT.","","P1Y","Annual","US","USD","115.2","","","2/1/2019 12:00:00 AM","2/4/2021 8:35:31 PM","License","144"
======= Truncated ==============

```
