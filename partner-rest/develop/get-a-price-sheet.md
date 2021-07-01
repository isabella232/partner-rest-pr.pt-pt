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
# <a name="get-a-price-sheet"></a>Obter uma folha de preços

Aplica-se a:

- Parceiro API

Este tópico explica como obter uma folha de preços para um determinado mercado e vista. Este método suporta filtros para obter história por mês.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário apenas suporta a autenticação do utilizador da aplicação. Só a candidatura ainda não está apoiada. Os parceiros que **experimentem o erro http:400** devem consultar a [documentação de autenticação da API do Parceiro.](api-authentication.md)
- Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.

## <a name="details"></a>Detalhes

- Os dados de retornos atuais apenas para o plano Azure de consumo e produtos de reserva.
- O [preço](pricing.md) atual inclui todos os contadores e produtos disponíveis durante o mês em curso até à data em que a API é chamada. Os meses anteriores incluem todos os contadores e produtos disponíveis para o mês em questão.
- Os preços dos contadores de consumo estão apenas em USD, os parceiros devem usar as taxas de câmbio API para calcular os custos da moeda local.
- Os preços dos contadores de consumo são estimados nos preços de venda a retalho. Os descontos para parceiros estão disponíveis através do [crédito adquirido pelo parceiro.](https://docs.microsoft.com/partner-center/partner-earned-credit-explanation)
- Os preços dos contadores de reservas incluem os descontos para parceiros da CSP. Os preços estimados de venda a retalho para reservas podem ser encontrados nas reservas de serviços partilhados que são descarregados a partir da página "Preços e ofertas" do Partner Center.
- Mais informações sobre os preços do plano Azure podem ser encontradas na documentação de preços do [plano Azure.](https://docs.microsoft.com/partner-center/azure-plan-price-list)
- Os preços dos parceiros e as APIs cambiais não fazem parte do [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).
- Este método devolve a lista de preços como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv. Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Obter** | https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='{market}',PricesheetView='{view}')/$value                                     |

### <a name="uri-required-parameters"></a>URI exigia parâmetros

Utilize os seguintes parâmetros de percurso para solicitar qual o mercado e o tipo de folha de preços que pretende.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Mercado                      | string   | Yes       | Código de país de duas letras para o mercado a ser solicitado       |
|Folha de preçosVereja | string   | Yes       | O tipo de folha de preços solicitada, pode ser azure_consumption, azure_reservations ou atualizado.  |

> [!Note]
> Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

### <a name="uri-filter-parameters"></a>Parâmetros de filtro URI

Utilize os seguintes parâmetros de filtro.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Linha cronológica| cadeia (de carateres)   | No| Predefinições à corrente se não for aprovada. Os valores possíveis são a história, a corrente e o futuro.       |
|Mensal| cadeia (de carateres)   | No| Só é necessário que o histórico seja solicitado, deve aderir à YYYYMM para a folha de preços solicitada.       |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.

Além dos cabeçalhos acima, os ficheiros de preços podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento. Por predefinição, os ficheiros não são comprimidos. Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo. Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todas as folhas antes de abril de 2020 só estão disponíveis como não comprimidos.

| Cabeçalho                   | Tipo de Valor     | Valor | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Accept-Encoding| string   | esvaziar| Opcional. Se o fluxo de ficheiro omitido não for comprimido.       |

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='ad',PricesheetView='azure_consumption')/$value?timeline=history&month=201909 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```
### <a name="request-example-for-new-commerce"></a>Exemplo de pedido para novo comércio

> [!Note]
> Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

```http
GET https://api.partner.microsoft.com/v1.0/sales/pricesheets(Market='US',PricesheetView='updatedlicensebased')/$value?timeline=history&month=202101 HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve a lista de preços como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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

### <a name="response-example-for-new-commerce"></a>Exemplo de resposta para novo comércio

> [!Note]
> Atualizaçãobensebased PriceSheetView está atualmente disponível apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência de comércio M365/D365.

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
