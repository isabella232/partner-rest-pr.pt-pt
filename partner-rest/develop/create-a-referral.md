---
title: Criar uma referência
description: Criar referências independentes ou partilhadas na API do Parceiro.
ms.date: 05/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 6aab4b5f45030c3c16294b2929b1a6d3086fb951
ms.sourcegitcommit: 3c165938f544ff226cbe11ca21ed5aa00448d9b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2020
ms.locfileid: "97770493"
---
# <a name="create-a-referral"></a><span data-ttu-id="47224-103">Criar uma referência</span><span class="sxs-lookup"><span data-stu-id="47224-103">Create a referral</span></span>

<span data-ttu-id="47224-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="47224-104">Applies to:</span></span>

- <span data-ttu-id="47224-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="47224-105">Partner API</span></span>

<span data-ttu-id="47224-106">Este tópico explica como criar uma referência.</span><span class="sxs-lookup"><span data-stu-id="47224-106">This topic explains how to create a referral.</span></span> <span data-ttu-id="47224-107">Existem dois tipos de [ReferralType:](referral-resources.md#referraltype)</span><span class="sxs-lookup"><span data-stu-id="47224-107">There are two types of [ReferralType](referral-resources.md#referraltype):</span></span>

1. <span data-ttu-id="47224-108">Independente: Quando uma referência é visível a um parceiro.</span><span class="sxs-lookup"><span data-stu-id="47224-108">Independent: Where a referral is visible to one partner.</span></span>
2. <span data-ttu-id="47224-109">Partilhado: Onde uma referência é visível para dois partidos que estão a trabalhar em conjunto.</span><span class="sxs-lookup"><span data-stu-id="47224-109">Shared: Where a referral is visible to two parties that are working together.</span></span> <span data-ttu-id="47224-110">Por exemplo, se a Microsoft e um parceiro estiverem a trabalhar juntos num negócio de co-venda, uma referência pode ser partilhada entre ambas as partes.</span><span class="sxs-lookup"><span data-stu-id="47224-110">For example, if Microsoft and a partner are working together in a co-selling deal, a referral can be shared between both parties.</span></span> <span data-ttu-id="47224-111">Para mais informações, consulte a secção [Criar uma referência partilhada.](#create-a-shared-referral)</span><span class="sxs-lookup"><span data-stu-id="47224-111">For more information, see the section [Creating a shared referral](#create-a-shared-referral).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47224-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="47224-112">Prerequisites</span></span>

- <span data-ttu-id="47224-113">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="47224-113">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="47224-114">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="47224-114">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="47224-115">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="47224-115">REST Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="47224-116">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="47224-116">Request syntax</span></span>

| <span data-ttu-id="47224-117">Método</span><span class="sxs-lookup"><span data-stu-id="47224-117">Method</span></span>  | <span data-ttu-id="47224-118">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="47224-118">Request URI</span></span>                                                  |
|---------|--------------------------------------------------------------|
| <span data-ttu-id="47224-119">**Publicar**</span><span class="sxs-lookup"><span data-stu-id="47224-119">**POST**</span></span> | <https://api.partner.microsoft.com/v1.0/engagements/referrals> |

### <a name="request-headers"></a><span data-ttu-id="47224-120">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="47224-120">Request headers</span></span>

- <span data-ttu-id="47224-121">Consulte [os cabeçalhos API REST do Parceiro](headers.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="47224-121">See [Partner API REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="47224-122">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="47224-122">Request body</span></span>

<span data-ttu-id="47224-123">Esta tabela descreve as propriedades [de referência](referral-resources.md) no organismo de pedido para uma nova referência.</span><span class="sxs-lookup"><span data-stu-id="47224-123">This table describes the [Referral](referral-resources.md) properties in the request body for a brand new referral.</span></span>

| <span data-ttu-id="47224-124">Propriedade</span><span class="sxs-lookup"><span data-stu-id="47224-124">Property</span></span>            | <span data-ttu-id="47224-125">Tipo</span><span class="sxs-lookup"><span data-stu-id="47224-125">Type</span></span>                                                                 | <span data-ttu-id="47224-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="47224-126">Description</span></span>                                                                                                          |
|---------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="47224-127">Nome</span><span class="sxs-lookup"><span data-stu-id="47224-127">Name</span></span>                | <span data-ttu-id="47224-128">string</span><span class="sxs-lookup"><span data-stu-id="47224-128">string</span></span>                                                               | <span data-ttu-id="47224-129">O nome da Referência.</span><span class="sxs-lookup"><span data-stu-id="47224-129">The name of the Referral.</span></span>                                                                                            |
| <span data-ttu-id="47224-130">ExternoReferênciaId</span><span class="sxs-lookup"><span data-stu-id="47224-130">ExternalReferenceId</span></span> | <span data-ttu-id="47224-131">string</span><span class="sxs-lookup"><span data-stu-id="47224-131">string</span></span>                                                               | <span data-ttu-id="47224-132">Um identificador externo para a referência.</span><span class="sxs-lookup"><span data-stu-id="47224-132">An external identifier for the referral.</span></span> <span data-ttu-id="47224-133">Por exemplo, o seu próprio ID de chumbo ou oportunidade dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="47224-133">For example, your own Dynamics 365 lead or opportunity ID.</span></span>                   |
| <span data-ttu-id="47224-134">Estado</span><span class="sxs-lookup"><span data-stu-id="47224-134">Status</span></span>              | [<span data-ttu-id="47224-135">ReferênciaStatus</span><span class="sxs-lookup"><span data-stu-id="47224-135">ReferralStatus</span></span>](referral-resources.md#referralstatus)               | <span data-ttu-id="47224-136">Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="47224-136">An [Enum](https://docs.microsoft.com/dotnet/api/system.enum) with values that indicate the referral status.</span></span>          |
| <span data-ttu-id="47224-137">Subtátuo</span><span class="sxs-lookup"><span data-stu-id="47224-137">Substatus</span></span>           | [<span data-ttu-id="47224-138">ReferênciaSubstato</span><span class="sxs-lookup"><span data-stu-id="47224-138">ReferralSubstatus</span></span>](referral-resources.md#referralsubstatus)         | <span data-ttu-id="47224-139">Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o substatus de referência.</span><span class="sxs-lookup"><span data-stu-id="47224-139">An [Enum](https://docs.microsoft.com/dotnet/api/system.enum) with values that indicate the referral substatus.</span></span>       |
| <span data-ttu-id="47224-140">StatusReason</span><span class="sxs-lookup"><span data-stu-id="47224-140">StatusReason</span></span>        | <span data-ttu-id="47224-141">string</span><span class="sxs-lookup"><span data-stu-id="47224-141">string</span></span>                                                               | <span data-ttu-id="47224-142">Uma mensagem descritiva sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="47224-142">A descriptive message about the status.</span></span> <span data-ttu-id="47224-143">Por exemplo, explique por que a referência foi perdida.</span><span class="sxs-lookup"><span data-stu-id="47224-143">For example, explain why the referral was lost.</span></span>                            |
| <span data-ttu-id="47224-144">Tipo de Referência</span><span class="sxs-lookup"><span data-stu-id="47224-144">ReferralType</span></span>        | [<span data-ttu-id="47224-145">Tipo de Referência</span><span class="sxs-lookup"><span data-stu-id="47224-145">ReferralType</span></span>](referral-resources.md#referraltype)                   | <span data-ttu-id="47224-146">Representa o tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="47224-146">Represents the referral type.</span></span> <span data-ttu-id="47224-147">**Necessário.**</span><span class="sxs-lookup"><span data-stu-id="47224-147">**Required.**</span></span>                                                                                        |
| <span data-ttu-id="47224-148">Qualificação</span><span class="sxs-lookup"><span data-stu-id="47224-148">Qualification</span></span>       | [<span data-ttu-id="47224-149">Qualificação de ReferênciaS</span><span class="sxs-lookup"><span data-stu-id="47224-149">ReferralQualification</span></span>](referral-resources.md#referralqualification) | <span data-ttu-id="47224-150">Representa a qualidade da referência.</span><span class="sxs-lookup"><span data-stu-id="47224-150">Represents the quality of the referral.</span></span>                                                                              |
| <span data-ttu-id="47224-151">CustomerProfile</span><span class="sxs-lookup"><span data-stu-id="47224-151">CustomerProfile</span></span>     | [<span data-ttu-id="47224-152">CustomerProfile</span><span class="sxs-lookup"><span data-stu-id="47224-152">CustomerProfile</span></span>](referral-resources.md#customerprofile)             | <span data-ttu-id="47224-153">Informações de contacto com o cliente.</span><span class="sxs-lookup"><span data-stu-id="47224-153">Customer contact information.</span></span>  <span data-ttu-id="47224-154">**Necessário.**</span><span class="sxs-lookup"><span data-stu-id="47224-154">**Required.**</span></span>                                                                                      |
| <span data-ttu-id="47224-155">Consent (Consentimento)</span><span class="sxs-lookup"><span data-stu-id="47224-155">Consent</span></span>             | [<span data-ttu-id="47224-156">Consent (Consentimento)</span><span class="sxs-lookup"><span data-stu-id="47224-156">Consent</span></span>](referral-resources.md#consent)                             | <span data-ttu-id="47224-157">O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores. **É necessário.**</span><span class="sxs-lookup"><span data-stu-id="47224-157">Consent flags around sharing information with other organizations and allowing them to contact users.**Required.**</span></span>               |
| <span data-ttu-id="47224-158">Detalhes</span><span class="sxs-lookup"><span data-stu-id="47224-158">Details</span></span>             | [<span data-ttu-id="47224-159">ReferênciaDetails</span><span class="sxs-lookup"><span data-stu-id="47224-159">ReferralDetails</span></span>](referral-resources.md#referraldetails)             | <span data-ttu-id="47224-160">Detalhes do cliente, notas, valor da oferta, data de fecho de moeda.</span><span class="sxs-lookup"><span data-stu-id="47224-160">Customer details, notes, deal value, currency closing date.</span></span> <span data-ttu-id="47224-161">**Necessário.**</span><span class="sxs-lookup"><span data-stu-id="47224-161">**Required.**</span></span>                                                           |
| <span data-ttu-id="47224-162">Equipa</span><span class="sxs-lookup"><span data-stu-id="47224-162">Team</span></span>                | [<span data-ttu-id="47224-163">Membro</span><span class="sxs-lookup"><span data-stu-id="47224-163">Member</span></span>](referral-resources.md#member)                               | <span data-ttu-id="47224-164">Representa os utilizadores nas organizações envolvidas no envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="47224-164">Represents users in the organizations that are involved in the partner engagement.</span></span>                                   |
| <span data-ttu-id="47224-165">ConvidarContexto</span><span class="sxs-lookup"><span data-stu-id="47224-165">InviteContext</span></span>       | [<span data-ttu-id="47224-166">ConvidarContexto</span><span class="sxs-lookup"><span data-stu-id="47224-166">InviteContext</span></span>](referral-resources.md#invitecontext)                 | <span data-ttu-id="47224-167">Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="47224-167">Represents additional information a user can provide when inviting another organization into the partner engagement.</span></span> |
| <span data-ttu-id="47224-168">Destino</span><span class="sxs-lookup"><span data-stu-id="47224-168">Target</span></span>         | [<span data-ttu-id="47224-169">ReferênciaTarget</span><span class="sxs-lookup"><span data-stu-id="47224-169">ReferralTarget</span></span>](referral-resources.md#target)        | <span data-ttu-id="47224-170">Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="47224-170">Represents additional information a user can provide when inviting another organization into the partner engagement.</span></span>  |

#### <a name="status--substatus-transition-states"></a><span data-ttu-id="47224-171">Estado & Estados de transição substatus</span><span class="sxs-lookup"><span data-stu-id="47224-171">Status & Substatus transition states</span></span>

| <span data-ttu-id="47224-172">Estado</span><span class="sxs-lookup"><span data-stu-id="47224-172">Status</span></span> | <span data-ttu-id="47224-173">Transição de estado permitida</span><span class="sxs-lookup"><span data-stu-id="47224-173">Allowed status transition</span></span> | <span data-ttu-id="47224-174">Substato permitido</span><span class="sxs-lookup"><span data-stu-id="47224-174">Allowed substatus</span></span>            |
|--------|---------------------------|------------------------------|
| <span data-ttu-id="47224-175">Novo</span><span class="sxs-lookup"><span data-stu-id="47224-175">New</span></span>    | <span data-ttu-id="47224-176">Novo, Ativo, Fechado</span><span class="sxs-lookup"><span data-stu-id="47224-176">New, Active, Closed</span></span>       | <span data-ttu-id="47224-177">Pendente, Recebido</span><span class="sxs-lookup"><span data-stu-id="47224-177">Pending, Received</span></span>            |
| <span data-ttu-id="47224-178">Ativo</span><span class="sxs-lookup"><span data-stu-id="47224-178">Active</span></span> | <span data-ttu-id="47224-179">Ativo, Fechado</span><span class="sxs-lookup"><span data-stu-id="47224-179">Active, Closed</span></span>            | <span data-ttu-id="47224-180">Aceite</span><span class="sxs-lookup"><span data-stu-id="47224-180">Accepted</span></span>                     |
| <span data-ttu-id="47224-181">Fechado</span><span class="sxs-lookup"><span data-stu-id="47224-181">Closed</span></span> | <span data-ttu-id="47224-182">Fechado</span><span class="sxs-lookup"><span data-stu-id="47224-182">Closed</span></span>                    | <span data-ttu-id="47224-183">Won, Lost, Declined, expirou</span><span class="sxs-lookup"><span data-stu-id="47224-183">Won, Lost, Declined, Expired</span></span> |

### <a name="request-example"></a><span data-ttu-id="47224-184">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="47224-184">Request example</span></span>

```http
POST https://api.partner.microsoft.com/v1.0/engagements/referrals HTTP/1.1
Authorization: Bearer <token>
Host: api.partner.microsoft.com
Content-Type: application/json

 {
    "name": "Test Cosell Invite_20",
    "status": "New",
    "substatus": "Pending",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Shared",
    "target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-34104-EBB"
        }
    ],
    "customerProfile": {
        "name": "Contoso Customer Inc",
        "address": {
            "addressLine1": "One Microsoft Way",
            "addressLine2": "34",
            "city": "Redmond",
            "state": "WA",
            "postalCode": "98052",
            "country": "US"
        },
        "size": "10to50employees",
        "team": [
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Sue",
                "lastName": "Smith",
                "phoneNumber": "1234567890",
                "email": "sue.smith@contoso.com"
            },
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Joe",
                "lastName": "Hansen",
                "phoneNumber": "4035698759",
                "email": "joe.hansen@contoso.com"
            }
        ],
        "ids": []
    },
    "consent": {
        "consentToToShareInfoWithOthers": true,
        "consentToContact": true
    },
    "details": {
        "notes": "Customer is looking to leverage Dynamics 365 to manage their supply chain. There is also a need to leverage a set of custom apps to enable their business processes.",
        "dealValue": 50000,
        "currency": "USD",
        "closingDateTime": "2018-11-14T00:00:00Z",
        "requirements": {
            "industries": [
                {
                    "id": "Manufacturing"
                }
            ],
            "products": [
                {
                    "id": "Dynamics365Enterprise"
                }
            ],
            "services": [
                {
                    "id": "DeploymentOrMigration"
                }
            ],
            "solutions": [
                {
                    "name": "Dynamics 365 for Field Service",
                    "type": "Category",
                    "id": "Dynamics365forFieldService"
                }
            ]
        }
    },
    "team": [
        {
            "contactPreference": {
                "locale": "en-us",
                "disableNotifications": false
            },
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "1231231234",
            "email": "john.doe@microsoft.com"
        }
    ],
    "inviteContext": {
        "notes": "Hi ABC Partner, hoping you can help this customer. Thanks, John @ Microsoft",
        "invitedBy": {
            "organizationId": "msft"
        }
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="47224-185">Resposta REST</span><span class="sxs-lookup"><span data-stu-id="47224-185">REST Response</span></span>

<span data-ttu-id="47224-186">Se for bem sucedido, este método devolve o recurso [de referência](referral-resources.md) povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="47224-186">If successful, this method returns the populated [Referral](referral-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="47224-187">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="47224-187">Response success and error codes</span></span>

<span data-ttu-id="47224-188">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="47224-188">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="47224-189">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="47224-189">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="47224-190">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="47224-190">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="47224-191">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="47224-191">Response example</span></span>

``` http
{
    "id": "4111fffc-f9ee-4d53-bba6-569135228642",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "organizationId": "7d23e5ca-19dc-4eaa-aac8-5e6b559f0d1d",
    "organizationName": "Contoso Company",
    "name": "Test Cosell Invite_20",
    "externalReferenceId": null,
    "createdDateTime": "2019-02-23T02:05:23.2931817Z",
    "updatedDateTime": "2019-02-23T02:05:23.2931817Z",
    "expirationDateTime": null,
    "status": "Active",
    "substatus": "Accepted",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Shared",
    "eTag": "\"00006d10-0000-0000-0000-5c70aa630000\"",
    "target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-34104-EBB"
        }
    ],
    "customerProfile": {
        "name": "Contoso Customer Inc",
        "address": {
            "addressLine1": "One Microsoft Way",
            "addressLine2": "34",
            "city": "Redmond",
            "state": "WA",
            "postalCode": "98052",
            "country": "US"
        },
        "size": "10to50employees",
        "team": [
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Sue",
                "lastName": "Smith",
                "phoneNumber": "1234567890",
                "email": "sue.smith@contoso.com"
            },
            {
                "contactPreference": {
                    "locale": "en-us",
                    "disableNotifications": false
                },
                "firstName": "Joe",
                "lastName": "Hansen",
                "phoneNumber": "4035698759",
                "email": "joe.hansen@contoso.com"
            }
        ],
        "ids": []
    },
    "consent": {
        "consentToToShareInfoWithOthers": true,
        "consentToContact": true
    },
    "details": {
        "notes": "Customer is looking to leverage Dynamics 365 to manage their supply chain. There is also a need to leverage a set of custom apps to enable their business processes.",
        "dealValue": 50000,
        "currency": "USD",
        "requirements": {
            "industries": [
                {
                    "id": "Manufacturing"
                }
            ],
            "products": [
                {
                    "id": "Dynamics365Enterprise"
                }
            ],
            "services": [
                {
                    "id": "DeploymentOrMigration"
                }
            ],
            "solutions": [
                {
                    "name": "Dynamics 365 for Field Service",
                    "type": "Category",
                    "id": "Dynamics365forFieldService"
                }
            ]
        }
    },
    "team": [
        {
            "contactPreference": {
                "locale": "en-us",
                "disableNotifications": false
            },
            "firstName": "John",
            "lastName": "Doe",
            "phoneNumber": "1231231234",
            "email": "john.doe@microsoft.com"
        }
    ],
    "inviteContext": {
        "notes": "Hi ABC Partner, hoping you can help this customer. Thanks, John @ Microsoft",
        "invitedBy": {
            "organizationId": "msft"
        }
    },
    "links": {
        "relatedReferrals": {
            "uri": "https://api.partner.microsoft.com/v1.0/engagments/referrals?$filter=engagementId eq '37ef26aa-1d15-4533-9f93-a69bd33ab1e5'",
            "method": "GET"
        },
        "self": {
            "uri": "https://api.partner.microsoft.com/v1.0/engagments/referrals/4111fffc-f9ee-4d53-bba6-569135228642",
            "method": "GET"
        }
    }
}
```

## <a name="create-a-shared-referral"></a><span data-ttu-id="47224-192">Criar uma referência partilhada</span><span class="sxs-lookup"><span data-stu-id="47224-192">Create a shared referral</span></span>

<span data-ttu-id="47224-193">Existem duas etapas para criar uma referência do tipo de [referência](referral-resources.md#referraltype) **partilhada.**</span><span class="sxs-lookup"><span data-stu-id="47224-193">There are two steps to create a referral of the **Shared** [referral type](referral-resources.md#referraltype).</span></span>

1. [<span data-ttu-id="47224-194">Crie a sua referência partilhada</span><span class="sxs-lookup"><span data-stu-id="47224-194">Create your shared referral</span></span>](#create-your-referral)
2. [<span data-ttu-id="47224-195">Criar uma referência conectada para o segundo partido</span><span class="sxs-lookup"><span data-stu-id="47224-195">Create a connected referral for the second party</span></span>](#create-a-connected-referral)

<span data-ttu-id="47224-196">O gráfico de fluxo que se segue ilustra estes dois passos na criação de uma referência partilhada.</span><span class="sxs-lookup"><span data-stu-id="47224-196">The following flow chart illustrates these two steps in creating a shared referral.</span></span>

![Gráfico de fluxo mostrando uma referência partilhada com 2 referências ligadas através da API do Parceiro Microsoft](../images/SharedReferral.png)

### <a name="create-your-referral"></a><span data-ttu-id="47224-198">Crie a sua referência</span><span class="sxs-lookup"><span data-stu-id="47224-198">Create your referral</span></span>

1. <span data-ttu-id="47224-199">Crie uma referência com [o set de Referência](referral-resources.md#referraltype) para compartilhado.</span><span class="sxs-lookup"><span data-stu-id="47224-199">Create a referral with [ReferralType](referral-resources.md#referraltype) set to shared.</span></span>
2. <span data-ttu-id="47224-200">Copie o **noivadoId** da resposta de retorno.</span><span class="sxs-lookup"><span data-stu-id="47224-200">Copy the **engagementId** from the return response.</span></span>

<span data-ttu-id="47224-201">[Amostra de referênciaStarget](referral-resources.md#target) para encaminhamento</span><span class="sxs-lookup"><span data-stu-id="47224-201">[ReferralTarget](referral-resources.md#target) sample for referral</span></span>

```json
"target": [
        {
            "type": "SolutionProfile",
            "id": "SOL-ABC-DEF"
        }
    ]
```

### <a name="create-a-connected-referral"></a><span data-ttu-id="47224-202">Criar uma referência conectada</span><span class="sxs-lookup"><span data-stu-id="47224-202">Create a connected referral</span></span>

1. <span data-ttu-id="47224-203">Crie outra referência para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="47224-203">Create another referral for Microsoft.</span></span>
2. <span data-ttu-id="47224-204">Inclua o **enagementId** da sua referência para que estejam ligados.</span><span class="sxs-lookup"><span data-stu-id="47224-204">Include the **enagementId** from your referral so they are tied together.</span></span>

<span data-ttu-id="47224-205">[Amostra de ReferênciaTarget](referral-resources.md#target) para encaminhamento da Microsoft</span><span class="sxs-lookup"><span data-stu-id="47224-205">[ReferralTarget](referral-resources.md#target) sample for Microsoft referral</span></span>

```json
"target": [
        {
            "type": "BusinessProfileLocation",
            "id": "msft"
        }
    ]
```