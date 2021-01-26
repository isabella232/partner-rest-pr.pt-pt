---
title: Cabeçalhos API REST parceiro
description: Os seguintes cabeçalhos de pedido HTTP e resposta são suportados pela API de REST do Parceiro.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 955cab07da7f3a386690e18042165015906d864a
ms.sourcegitcommit: 0508b7302a3965fd5537b05c1f0397a1da014257
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2020
ms.locfileid: "97770480"
---
# <a name="partner-rest-api-headers"></a>Cabeçalhos API do Parceiro REST

A API rest do parceiro suporta os seguintes cabeçalhos de pedido e resposta HTTP.

> [!NOTE]
> Nem todas as chamadas da API aceitam todos os cabeçalhos.

## <a name="request-headers"></a>Cabeçalhos do pedido

Os seguintes cabeçalhos de pedido HTTP são suportados pela API de APOIO do Parceiro.

| Cabeçalho                       | Tipo de Valor | Descrição                                                                            |
|------------------------------|------------|----------------------------------------------------------------------------------------|
| Autorização           | string     | Obrigatório. O sinal de autorização na ficha do Bearer &lt; &gt; .                    |
| Aceitar                  | string     | Especifica o tipo de pedido e resposta, "aplicação/json".                           |
| cliente-pedido id         | GUID       | Obrigatório. Um identificador único para a chamada, útil em registos e traços de rede para erros de resolução de problemas. O valor deve ser reposto para cada chamada. Todas as operações devem incluir este cabeçalho. |
| Se-corresponder:                    | string     | Usado para o controlo da concordância. Algumas chamadas da API requerem passar o ETag através do cabeçalho If-Match. O ETag está geralmente no recurso e, portanto, requer que obtenha o mais recente. |

## <a name="response-headers"></a>Cabeçalhos de resposta

Os seguintes cabeçalhos de resposta HTTP podem ser devolvidos pela API do Partner REST.

| Cabeçalho                    | Tipo de valor | Descrição                                                                                                               |
|-------------------|------------|--------------------------------------------------------------------------------------------------|
| Aceitar                | string     | Especifica o tipo de pedido e resposta, "aplicação/json".                                     |
| pedido id        | GUID       | Um identificador único para a chamada, usado para garantir a potência de id. Em caso de intervalo, a chamada de novo deve incluir o mesmo valor. Ao receber uma resposta (sucesso ou falha de negócio), o valor deve ser reposto para a próxima chamada. |
| cliente-pedido id| GUID| Um identificador único para a chamada, útil os registos e os vestígios de rede para erros de resolução de problemas. O valor deve ser reposto para cada chamada. Todas as operações devem incluir este cabeçalho.                                                |
| x-ms-ags-diagnóstico   | string | Uma cadeia que contém informações de diagnóstico do serviço.
| carimbo de data/hora|string | Tempo de tempo do pedido quando atingiu a API.
|ETag |string | ETag do recurso.
