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
# <a name="get-foreign-exchange-rates"></a>Obter taxas de câmbio estrangeiras

Aplica-se a:

- Parceiro API

Este tópico explica como obter taxas de câmbio por um determinado mês.

## <a name="prerequisites"></a>Pré-requisitos

- Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md) Este cenário apenas suporta a autenticação do utilizador da aplicação. Só a candidatura ainda não está apoiada.
- Atualmente, esta API suporta apenas o acesso do utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Admin Agent ou Sales Agent.


## <a name="details"></a>Detalhes

- Atualmente utilizado com [a API de folha de preços](get-a-price-sheet.md) para calcular os encargos esperados para as moedas locais do plano Azure CSP.
- As taxas de câmbio mantêm-se verdadeiras durante todo o mês em que são publicadas.
- Mais informações sobre [os preços do](pricing.md) plano Azure podem ser encontradas na documentação de preços do [plano Azure.](https://docs.microsoft.com/partner-center/azure-plan-price-list)
- Os preços dos parceiros e as APIs cambiais não fazem parte do [Partner Center SDK](https://docs.microsoft.com/partner-center/develop/get-started).
- Este método devolve os resultados como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv. Os detalhes sobre como solicitar ficheiros comprimidos estão incluídos abaixo.

## <a name="rest-request"></a>Pedido de DESCANSO

### <a name="request-syntax"></a>Solicitar sintaxe

| Método   | URI do pedido                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Obter** | https://api.partner.microsoft.com/v1.0/sales/fxrates(Month='{month}')/$value                                  |

### <a name="uri-required-parameters"></a>URI exigia parâmetros

Use os seguintes parâmetros de caminho para solicitar o mês de taxas de câmbio que deseja.

| Nome                   | Tipo     | Necessário | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Mensal                      | string   | Sim       | Deve estar no formato YYYMM. Se omitiu incumprimentos ao mês em curso.       |

### <a name="request-headers"></a>Cabeçalhos do pedido

- Consulte [os cabeçalhos Partner REST](headers.md) para obter mais informações.

Além dos cabeçalhos acima, os ficheiros podem ser recuperados como redução comprimida reduzindo a largura de banda e os tempos de descarregamento. Por predefinição, os ficheiros não são comprimidos. Para obter versões comprimidos dos ficheiros pode incluir o valor do cabeçalho abaixo. Percebam que as folhas comprimidos só estão disponíveis a partir de abril de 2020, todos os pedidos antes de abril de 2020 só estão disponíveis como não comprimidos.

| Cabeçalho                   | Tipo de Valor     | Valor | Descrição                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
|Accept-Encoding| string   | esvaziar| Opcional. Se o fluxo de ficheiro omitido não for comprimido.       |

### <a name="request-example"></a>Exemplo de pedido

```http
GET https://api.partner.microsoft.com/v1.0/sales/fxrates(Month='201909')/$value HTTP/1.1
Authorization: Bearer
Accept-Encoding: deflate
Host: api.partner.microsoft.com

```

## <a name="rest-response"></a>Resposta do REST

Se for bem sucedido, este método devolve as taxas de câmbio como um fluxo de ficheiros. O fluxo de ficheiros é um ficheiro .csv ou uma versão comprimida zip do .csv.

### <a name="response-success-and-error-codes"></a>Códigos de sucesso e erro de resposta

Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem. Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais. Para obter a lista completa, consulte [códigos de erro](error-codes.md).

### <a name="response-example"></a>Exemplo de resposta

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
