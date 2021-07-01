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
# <a name="get-an-offer-matrix"></a>Obtenha uma matriz de oferta

Aplica-se a:

- Parceiro API
- O M365/D365 New Commerce experimenta pré-visualização técnica. As mudanças abaixo do Novo Comércio estão atualmente disponíveis apenas para parceiros que fazem parte da nova pré-visualização técnica da experiência técnica M365/D365.

Este tópico explica como obter uma matriz de oferta por um dado mês. A matriz de oferta inclui propriedades e regras de compra para os produtos e skus. Este método suporta filtros para obter história por mês.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário apenas suporta a autenticação do utilizador da aplicação. Só a candidatura ainda não está apoiada. Os parceiros que **experimentem o erro http:400** devem consultar a [documentação de autenticação da API do Parceiro.](api-authentication.md)
- Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.

## <a name="details"></a>Detalhes

- Os dados de devoluções atuais apenas para novos produtos baseados em licenças de comércio atualizados.
- Os preços atuais incluem produtos disponíveis durante o mês em curso até à data em que a API é chamada. Os meses anteriores incluem a data a partir do último dia do mês selecionado.
- Este método devolve os dados como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv. Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Obter** | https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='{date}')/$value |

### <a name="uri-filter-parameters"></a>Parâmetros de filtro URI

Utilize os seguintes parâmetros de filtro.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Mensal| cadeia (de carateres)   | No | Deve aderir à YYYYMM para a folha de preços solicitada. |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.

Além dos cabeçalhos acima, os ficheiros de preços podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento. Por predefinição, os ficheiros não são comprimidos. Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo. Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todas as folhas antes de abril de 2020 só estão disponíveis como não comprimidos.

| Cabeçalho                   | Tipo de Valor     | Valor | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Accept-Encoding| string   | esvaziar| Opcional. Se o fluxo de ficheiro omitido não for comprimido.       |

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partner.microsoft.com/v1.0/sales/offermatrix(Month='202101')/$value HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve uma matriz de oferta como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
