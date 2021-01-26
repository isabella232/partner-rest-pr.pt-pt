---
title: Códigos de erro API REST do Parceiro
description: As APIs de repouso do parceiro devolvem um objeto JSON com um código de estado sobre o sucesso ou falha do seu pedido.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 0829f48e5028b4a19e8a6f7b89fbb41d83a50cab
ms.sourcegitcommit: 0508b7302a3965fd5537b05c1f0397a1da014257
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2020
ms.locfileid: "97770499"
---
# <a name="partner-api-rest-error-codes"></a>Códigos de erro API REST do Parceiro

Aplica-se a:

- Parceiro API

Os erros nas APIs de REPOUSO do Parceiro são devolvidos utilizando códigos de estado HTTP padrão, bem como um objeto de resposta a erros JSON.

## <a name="http-status-codes"></a>Códigos de estado HTTP

As tabelas que se seguem e descreve os códigos de estado HTTP que podem ser devolvidos.

| Código de estado | Mensagem de estado                  | Descrição                                                                                                                            |
|:------------|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| 400         | Pedido Incorreto                     | Não é possível processar o pedido por estar mal formado ou incorreto.                                                                       |
| 401         | Não autorizado                    | As informações de autenticação necessárias estão em falta ou não são válidas para o recurso.                                                   |
| 403         | Proibido                       | O acesso é negado ao recurso solicitado. O utilizador pode não ter permissão suficiente. **Importante: se as políticas de acesso condicional forem aplicadas a um recurso, `HTTP 403; Forbidden error=insufficent_claims` podem ser devolvidas.** Para obter mais detalhes sobre o Microsoft Graph e acesso condicional, consulte [a Orientação do Programador para acesso condicional ao Azure Ative Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-conditional-access-developer)  |
| 404         | Não Encontrado                       | O recurso solicitado não existe.                                                                                                  |
| 405         | Método não permitido              | O método HTTP no pedido não é permitido no recurso.                                                                         |
| 406         | Não aceitável                  | Este serviço não suporta o formato solicitado no cabeçalho Aceitar.                                                                |
| 409         | Conflito                        | O estado atual entra em conflito com o que o pedido espera. Por exemplo, a pasta dos pais especificada pode não existir.                   |
| 410         | Foi-se                            | O recurso pedido já não está disponível no servidor.                                               |
| 411         | Comprimento necessário                 | É necessário um cabeçalho de comprimento de conteúdo no pedido.                                                                                    |
| 412         | Pré-condição falhou             | Uma condição prévia fornecida no pedido (como um cabeçalho se-match) não corresponde ao estado atual do recurso.                       |
| 413         | Entidade de pedido muito grande        | O tamanho do pedido excede o limite máximo.                                                                                            |
| 415         | Tipo de mídia não suportado          | O tipo de conteúdo do pedido é um formato que não é suportado pelo serviço.                                                      |
| 416         | Gama solicitada não satisfaizável | O intervalo de byte especificado é inválido ou indisponível.                                                                                    |
| 422         | Entidade não processável            | Não é possível processar o pedido porque é semântica incorreto.                                                                        |
| 423         | Bloqueado                          | O recurso que está a ser acedido está bloqueado.                                                                                          |
| 429         | Muitos pedidos               | A aplicação do cliente foi acelerada e não deve tentar repetir o pedido até que tenha decorrido um período de tempo.                |
| 500         | Erro interno do servidor           | Houve um erro do servidor interno durante o processamento do pedido.                                                                       |
| 501         | Não implementado                 | A funcionalidade solicitada não é implementada.                                                                                               |
| 503         | Serviço Indisponível             | O serviço está temporariamente indisponível para manutenção ou está sobrecarregado. Pode repetir o pedido após um atraso, o qual pode ser especificado num cabeçalho Retry-After.|
| 504         | Tempo de gateway                 | O servidor, apesar de agir como um representante, não recebeu uma resposta atempadamente do servidor a montante que precisava para aceder na tentativa de completar o pedido. Pode ocorrer juntamente com 503. |
| 507         | Armazenamento insuficiente            | A quota máxima de armazenamento foi atingida.                                                                                            |
| 509         | Limite de largura de banda ultrapassado        | A sua aplicação foi estrangulada por exceder a tampa máxima de largura de banda. A sua aplicação pode voltar a tentar o pedido depois de decorrido mais tempo. |

A resposta de erro é um único objeto JSON que contém um único erro denominado **propriedade**. Este objeto inclui todos os detalhes do erro. Pode utilizar as informações aqui devolvidas em vez de ou para além do código de estado HTTP. Segue-se um exemplo de um corpo completo de erro json.

## <a name="error-resource-type"></a>Tipo de recurso de erro

A resposta de erro é um único objeto JSON que contém um único erro denominado **propriedade**. Este objeto inclui todos os detalhes do erro. Pode utilizar as informações aqui devolvidas em vez de ou para além do código de estado HTTP. Segue-se um exemplo de um corpo completo de erro json.

A seguinte tabela e amostra de código descreve o esquema de uma resposta de erro.

| Nome        | Tipo   | Descrição                                                                                    |
|-------------|--------|------------------------------------------------------------------------------------------------|
| code        | string | Sempre voltava. Indica o tipo de erro que ocorreu. Sem ser nulo.                          |
| message | string | Sempre voltava. Descreve o erro em detalhe e fornece informações adicionais de depuragem. Não-nulo, não vazio. O comprimento máximo é de 1024 caracteres. |
| interiorError        | objeto  | Opcional. Objeto de erro adicional que pode ser mais específico do que o erro de nível superior.                                   |
| alvo      | string | O alvo de onde o erro se originou.                                                      |

### <a name="code-property"></a>Propriedade código

A `code` propriedade contém um dos seguintes valores possíveis. As suas aplicações devem estar preparadas para lidar com qualquer um destes erros.

| Código                      | Descrição
|:--------------------------|:--------------
| **acessodeniado**          | Quem ligou não tem permissão para realizar a ação.
| **generalExcepção**      | Ocorreu um erro não especificado.
| **invalidRequest**        | O pedido é mal formado ou incorreto.
| **itemNotFound**          | O recurso não foi encontrado.
|**pré-condiçãoFailed**     | Uma condição prévia fornecida no pedido (como um cabeçalho se-match) não corresponde ao estado atual do recurso.
| **recursosModificado**      | O recurso que está a ser atualizado mudou desde que o chamador o leu pela última vez, normalmente uma incompatibilidade do eTag.
| **serviço Não Disponível**   | O serviço não está disponível. Tente o pedido de novo depois de um atraso. Pode haver um cabeçalho Retry-After.
| **autenticado**       | O chamador não é autenticado.

### <a name="message-property"></a>Propriedade de mensagem

A `message` propriedade na raiz contém uma mensagem de erro destinada a que o desenvolvedor leia. As mensagens de erro não estão localizadas e não devem ser exibidas diretamente ao utilizador. Ao lidar com erros, o seu código não deve verificar `message` valores porque podem ser alterados a qualquer momento, e muitas vezes contêm informações dinâmicas específicas do pedido falhado. Só deve codificar códigos de erro devolvidos em `code` propriedades.

### <a name="innererror-object"></a>Objeto InnerError

O `innererror` objeto pode conter novamente mais `innererror` objetos com códigos de erro adicionais e mais específicos. Ao lidar com um erro, as aplicações devem circular por todos os códigos de erro disponíveis e utilizar o mais detalhado que entenderem.

Existem alguns erros adicionais que a sua aplicação pode encontrar dentro dos `innererror` objetos aninhados. As aplicações não são necessárias para lidar com estas, mas podem, se assim o desejarem. O serviço pode adicionar novos códigos de erro ou parar de devolver os antigos a qualquer momento, por isso é importante que todas as aplicações sejam capazes de lidar com os [códigos básicos de erro]

```json
{
  "error": {
    "code": "unAuthorized",
    "message": "Caller is not authorized to access the resource.",
    "target": "referral",
    "innerError": {
      "code": "innerErrorCode",
      "message": "Unauthorized referral access"
    }
  }
}
```
