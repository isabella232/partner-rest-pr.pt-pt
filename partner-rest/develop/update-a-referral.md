---
title: Atualizar uma vantagem ou oportunidade (Obsoleta)
description: Permite-lhe atualizar os detalhes de chumbo ou oportunidade. Este método de atualização de uma vantagem ou oportunidade é obsoleto e recomeciamos usando a chamada PATCH.
ms.date: 09/30/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 9705db1c21dbec7099cfefebdc7bb23ec65e428c
ms.sourcegitcommit: 1e38faa376f317151aca15ae126015e290baa556
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/29/2020
ms.locfileid: "97770544"
---
# <a name="update-a-lead-or-opportunity-obsolete"></a><span data-ttu-id="7636e-104">Atualizar uma vantagem ou oportunidade (Obsoleta)</span><span class="sxs-lookup"><span data-stu-id="7636e-104">Update a lead or opportunity (Obsolete)</span></span>

<span data-ttu-id="7636e-105">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="7636e-105">Applies to:</span></span>

- <span data-ttu-id="7636e-106">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="7636e-106">Partner API</span></span>

<span data-ttu-id="7636e-107">Este tópico explica como atualizar os detalhes de chumbo ou oportunidade como o valor do negócio, data estimada de fecho ou gerir as fases de vendas entre outros detalhes.</span><span class="sxs-lookup"><span data-stu-id="7636e-107">This topic explains how to update the lead or opportunity details like the deal value, estimated close date or manage the sales stages amongst other details.</span></span> 


> [!IMPORTANT]
<span data-ttu-id="7636e-108">Este método de atualização de uma vantagem ou oportunidade é obsoleto e recomeciamos usando a chamada [PATCH.](patch-a-referral.md)</span><span class="sxs-lookup"><span data-stu-id="7636e-108">This method of updating a lead or opportunity is obsolete and we recommmend using the [PATCH](patch-a-referral.md) call instead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7636e-109">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7636e-109">Prerequisites</span></span>

- <span data-ttu-id="7636e-110">Credenciais descritas na [autenticação da API do parceiro.](api-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="7636e-110">Credentials as described in [Partner API authentication](api-authentication.md).</span></span> <span data-ttu-id="7636e-111">Este cenário suporta a autenticação com credenciais app+utilizador.</span><span class="sxs-lookup"><span data-stu-id="7636e-111">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="7636e-112">Atualmente, esta API suporta apenas o acesso ao utilizador quando os parceiros devem estar numa das seguintes funções: Global Admin, Referral Admin ou Referral User.</span><span class="sxs-lookup"><span data-stu-id="7636e-112">This API currently supports only user access where partners must be in one of the following roles: Global Admin, Referral Admin or Referral User.</span></span>

## <a name="rest-request"></a><span data-ttu-id="7636e-113">Pedido de DESCANSO</span><span class="sxs-lookup"><span data-stu-id="7636e-113">REST Request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7636e-114">Solicitar sintaxe</span><span class="sxs-lookup"><span data-stu-id="7636e-114">Request syntax</span></span>

| <span data-ttu-id="7636e-115">Método</span><span class="sxs-lookup"><span data-stu-id="7636e-115">Method</span></span>  | <span data-ttu-id="7636e-116">URI do pedido</span><span class="sxs-lookup"><span data-stu-id="7636e-116">Request URI</span></span>                                                       |
|---------|-------------------------------------------------------------------|
| <span data-ttu-id="7636e-117">**PUT**</span><span class="sxs-lookup"><span data-stu-id="7636e-117">**PUT**</span></span> | <https://api.partner.microsoft.com/v1.0/engagements/referrals/{Id}> |

### <a name="request-headers"></a><span data-ttu-id="7636e-118">Cabeçalhos do pedido</span><span class="sxs-lookup"><span data-stu-id="7636e-118">Request headers</span></span>

- <span data-ttu-id="7636e-119">Para obter mais informações, consulte [os cabeçalhos Partner API REST](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7636e-119">For more information, see [Partner API REST headers](headers.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7636e-120">Certifique-se de definir o **cabeçalho If-Match.**</span><span class="sxs-lookup"><span data-stu-id="7636e-120">Be sure to set the **If-Match** header.</span></span>

### <a name="request-body"></a><span data-ttu-id="7636e-121">Corpo do pedido</span><span class="sxs-lookup"><span data-stu-id="7636e-121">Request body</span></span>

<span data-ttu-id="7636e-122">Esta tabela descreve as propriedades [de referência](referral-resources.md) no corpo de pedido.</span><span class="sxs-lookup"><span data-stu-id="7636e-122">This table describes the [Referral](referral-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="7636e-123">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7636e-123">Property</span></span>            | <span data-ttu-id="7636e-124">Tipo</span><span class="sxs-lookup"><span data-stu-id="7636e-124">Type</span></span>                                                                 | <span data-ttu-id="7636e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="7636e-125">Description</span></span>                                                                                                          |
|---------------------|----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7636e-126">Id</span><span class="sxs-lookup"><span data-stu-id="7636e-126">Id</span></span>                  | <span data-ttu-id="7636e-127">string</span><span class="sxs-lookup"><span data-stu-id="7636e-127">string</span></span>                                                               | <span data-ttu-id="7636e-128">A identificação desta referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-128">The ID for this Referral.</span></span>                                                                                            |
| <span data-ttu-id="7636e-129">EngagementId</span><span class="sxs-lookup"><span data-stu-id="7636e-129">EngagementId</span></span>        | <span data-ttu-id="7636e-130">string</span><span class="sxs-lookup"><span data-stu-id="7636e-130">string</span></span>                                                               | <span data-ttu-id="7636e-131">O EngagementID para esta referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-131">The EngagementID for this Referral.</span></span> <span data-ttu-id="7636e-132">Várias referências podem ser associadas a um único EngagementID</span><span class="sxs-lookup"><span data-stu-id="7636e-132">Multiple referrals can be associated to a single EngagementID</span></span>                    |
| <span data-ttu-id="7636e-133">Nome</span><span class="sxs-lookup"><span data-stu-id="7636e-133">Name</span></span>                | <span data-ttu-id="7636e-134">string</span><span class="sxs-lookup"><span data-stu-id="7636e-134">string</span></span>                                                               | <span data-ttu-id="7636e-135">O nome da Referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-135">The name of the Referral.</span></span>                                                                                            |
| <span data-ttu-id="7636e-136">ExternoReferênciaId</span><span class="sxs-lookup"><span data-stu-id="7636e-136">ExternalReferenceId</span></span> | <span data-ttu-id="7636e-137">string</span><span class="sxs-lookup"><span data-stu-id="7636e-137">string</span></span>                                                               | <span data-ttu-id="7636e-138">Um identificador externo para a referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-138">An external identifier for the referral.</span></span> <span data-ttu-id="7636e-139">Exemplo: Guarde o seu próprio ID de chumbo/oportunidade Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="7636e-139">Example: Store your own Dynamics 365 lead/opportunity ID</span></span>                    |
| <span data-ttu-id="7636e-140">CreatedDateTime</span><span class="sxs-lookup"><span data-stu-id="7636e-140">CreatedDateTime</span></span>     | <span data-ttu-id="7636e-141">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="7636e-141">string in UTC date time format</span></span>                                       | <span data-ttu-id="7636e-142">A data em que a referência foi criada.</span><span class="sxs-lookup"><span data-stu-id="7636e-142">The date the referral was created.</span></span>                                                                                   |
| <span data-ttu-id="7636e-143">Hora do Natal Atualizado</span><span class="sxs-lookup"><span data-stu-id="7636e-143">UpdatedDateTime</span></span>     | <span data-ttu-id="7636e-144">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="7636e-144">string in UTC date time format</span></span>                                       | <span data-ttu-id="7636e-145">A data em que a referência foi atualizada pela última vez.</span><span class="sxs-lookup"><span data-stu-id="7636e-145">The date the referral was last updated.</span></span>                                                                              |
| <span data-ttu-id="7636e-146">Expiração Hora do Fim</span><span class="sxs-lookup"><span data-stu-id="7636e-146">ExpirationDateTime</span></span>  | <span data-ttu-id="7636e-147">cadeia no formato de hora de data UTC</span><span class="sxs-lookup"><span data-stu-id="7636e-147">string in UTC date time format</span></span>                                       | <span data-ttu-id="7636e-148">A data da referência expirará.</span><span class="sxs-lookup"><span data-stu-id="7636e-148">The date the referral will expire.</span></span>                                                                                   |
| <span data-ttu-id="7636e-149">Estado</span><span class="sxs-lookup"><span data-stu-id="7636e-149">Status</span></span>              | [<span data-ttu-id="7636e-150">ReferênciaStatus</span><span class="sxs-lookup"><span data-stu-id="7636e-150">ReferralStatus</span></span>](referral-resources.md#referralstatus)               | <span data-ttu-id="7636e-151">Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="7636e-151">An [Enum](https://docs.microsoft.com/dotnet/api/system.enum) with values that indicate the referral status.</span></span>          |
| <span data-ttu-id="7636e-152">Subtátuo</span><span class="sxs-lookup"><span data-stu-id="7636e-152">Substatus</span></span>           | [<span data-ttu-id="7636e-153">ReferênciaSubstato</span><span class="sxs-lookup"><span data-stu-id="7636e-153">ReferralSubstatus</span></span>](referral-resources.md#referralsubstatus)         | <span data-ttu-id="7636e-154">Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o sub estatuto de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="7636e-154">An [Enum](https://docs.microsoft.com/dotnet/api/system.enum) with values that indicate the referral sub status.</span></span>      |
| <span data-ttu-id="7636e-155">StatusReason</span><span class="sxs-lookup"><span data-stu-id="7636e-155">StatusReason</span></span>        | <span data-ttu-id="7636e-156">string</span><span class="sxs-lookup"><span data-stu-id="7636e-156">string</span></span>                                                               | <span data-ttu-id="7636e-157">Uma mensagem descritiva sobre o estado.</span><span class="sxs-lookup"><span data-stu-id="7636e-157">A descriptive message about the status.</span></span> <span data-ttu-id="7636e-158">Por exemplo, explique por que a referência foi perdida.</span><span class="sxs-lookup"><span data-stu-id="7636e-158">For example, explain why the referral was lost.</span></span>                              |
| <span data-ttu-id="7636e-159">Tipo de Referência</span><span class="sxs-lookup"><span data-stu-id="7636e-159">ReferralType</span></span>        | [<span data-ttu-id="7636e-160">Tipo de Referência</span><span class="sxs-lookup"><span data-stu-id="7636e-160">ReferralType</span></span>](referral-resources.md#referraltype)                   | <span data-ttu-id="7636e-161">Representa o tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-161">Represents the referral type.</span></span>                                                                                        |
| <span data-ttu-id="7636e-162">Qualificação</span><span class="sxs-lookup"><span data-stu-id="7636e-162">Qualification</span></span>       | [<span data-ttu-id="7636e-163">Qualificação de ReferênciaS</span><span class="sxs-lookup"><span data-stu-id="7636e-163">ReferralQualification</span></span>](referral-resources.md#referralqualification) | <span data-ttu-id="7636e-164">Representa a qualidade da referência.</span><span class="sxs-lookup"><span data-stu-id="7636e-164">Represents the quality of the referral.</span></span>                                                                              |
| <span data-ttu-id="7636e-165">CustomerProfile</span><span class="sxs-lookup"><span data-stu-id="7636e-165">CustomerProfile</span></span>     | [<span data-ttu-id="7636e-166">CustomerProfile</span><span class="sxs-lookup"><span data-stu-id="7636e-166">CustomerProfile</span></span>](referral-resources.md#customerprofile)             | <span data-ttu-id="7636e-167">Informações de contacto com o cliente.</span><span class="sxs-lookup"><span data-stu-id="7636e-167">Customer contact information.</span></span>                                                                                        |
| <span data-ttu-id="7636e-168">Consent (Consentimento)</span><span class="sxs-lookup"><span data-stu-id="7636e-168">Consent</span></span>             | [<span data-ttu-id="7636e-169">Consent (Consentimento)</span><span class="sxs-lookup"><span data-stu-id="7636e-169">Consent</span></span>](referral-resources.md#consent)                             | <span data-ttu-id="7636e-170">O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores.</span><span class="sxs-lookup"><span data-stu-id="7636e-170">Consent flags around sharing information with other organizations and allowing them to contact users.</span></span>                |
| <span data-ttu-id="7636e-171">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7636e-171">Details</span></span>             | [<span data-ttu-id="7636e-172">ReferênciaDetails</span><span class="sxs-lookup"><span data-stu-id="7636e-172">ReferralDetails</span></span>](referral-resources.md#referraldetails)             | <span data-ttu-id="7636e-173">Detalhes do cliente, notas, valor da oferta, data de fecho de moeda.</span><span class="sxs-lookup"><span data-stu-id="7636e-173">Customer details, notes, deal value, currency closing date.</span></span>                                                          |
| <span data-ttu-id="7636e-174">Equipa</span><span class="sxs-lookup"><span data-stu-id="7636e-174">Team</span></span>                | [<span data-ttu-id="7636e-175">Membro</span><span class="sxs-lookup"><span data-stu-id="7636e-175">Member</span></span>](referral-resources.md#member)                               | <span data-ttu-id="7636e-176">Representa os utilizadores nas organizações envolvidas no envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="7636e-176">Represents users in the organizations that are involved in the partner engagement.</span></span>                                   |
| <span data-ttu-id="7636e-177">ConvidarContexto</span><span class="sxs-lookup"><span data-stu-id="7636e-177">InviteContext</span></span>       | [<span data-ttu-id="7636e-178">ConvidarContexto</span><span class="sxs-lookup"><span data-stu-id="7636e-178">InviteContext</span></span>](referral-resources.md#invitecontext)                 | <span data-ttu-id="7636e-179">Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="7636e-179">Represents additional information a user can provide when inviting another organization into the partner engagement.</span></span> |
| <span data-ttu-id="7636e-180">Destino</span><span class="sxs-lookup"><span data-stu-id="7636e-180">Target</span></span>         | [<span data-ttu-id="7636e-181">ReferênciaTarget</span><span class="sxs-lookup"><span data-stu-id="7636e-181">ReferralTarget</span></span>](referral-resources.md#target)        | <span data-ttu-id="7636e-182">Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.</span><span class="sxs-lookup"><span data-stu-id="7636e-182">Represents additional information a user can provide when inviting another organization into the partner engagement.</span></span>  |

### <a name="status-and-substatus-transition-states"></a><span data-ttu-id="7636e-183">Estado e estados de transição sub-estatuetas</span><span class="sxs-lookup"><span data-stu-id="7636e-183">Status and substatus transition states</span></span>

| <span data-ttu-id="7636e-184">Estado</span><span class="sxs-lookup"><span data-stu-id="7636e-184">Status</span></span> | <span data-ttu-id="7636e-185">Transição de Estado Permitida</span><span class="sxs-lookup"><span data-stu-id="7636e-185">Allowed Status Transition</span></span> | <span data-ttu-id="7636e-186">Substatus permitido</span><span class="sxs-lookup"><span data-stu-id="7636e-186">Allowed Substatus</span></span>            |
|--------|---------------------------|------------------------------|
| <span data-ttu-id="7636e-187">Novo</span><span class="sxs-lookup"><span data-stu-id="7636e-187">New</span></span>    | <span data-ttu-id="7636e-188">Novo, Ativo, Fechado</span><span class="sxs-lookup"><span data-stu-id="7636e-188">New, Active, Closed</span></span>       | <span data-ttu-id="7636e-189">Pendente, Recebido</span><span class="sxs-lookup"><span data-stu-id="7636e-189">Pending, Received</span></span>            |
| <span data-ttu-id="7636e-190">Ativo</span><span class="sxs-lookup"><span data-stu-id="7636e-190">Active</span></span> | <span data-ttu-id="7636e-191">Ativo, Fechado</span><span class="sxs-lookup"><span data-stu-id="7636e-191">Active, Closed</span></span>            | <span data-ttu-id="7636e-192">Aceite</span><span class="sxs-lookup"><span data-stu-id="7636e-192">Accepted</span></span>                     |
| <span data-ttu-id="7636e-193">Fechado</span><span class="sxs-lookup"><span data-stu-id="7636e-193">Closed</span></span> | <span data-ttu-id="7636e-194">Fechado</span><span class="sxs-lookup"><span data-stu-id="7636e-194">Closed</span></span>                    | <span data-ttu-id="7636e-195">Won, Lost, Declined, expirou</span><span class="sxs-lookup"><span data-stu-id="7636e-195">Won, Lost, Declined, Expired</span></span> |

### <a name="request-example"></a><span data-ttu-id="7636e-196">Exemplo de pedido</span><span class="sxs-lookup"><span data-stu-id="7636e-196">Request example</span></span>

```http
PUT https://api.partner.microsoft.com/v1.0/engagements/referrals/49d90c72-3326-4f61-aacc-2cb57970448c HTTP/1.1
Authorization: Bearer <token>
Host: api.partner.microsoft.com
Content-Type: application/json

 {
    "id": "49d90c72-3326-4f61-aacc-2cb57970448c",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "createdDateTime": "2018-11-06T18:40:42.6178337Z",
    "updatedDateTime": "2018-11-06T18:40:42.6178337Z",
    "expirationDateTime": "2018-11-14T00:00:00Z",
    "status": "Closed",
    "substatus": "Won",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Independent",
    "target": [
        {
            "type": "BusinessProfileLocation",
            "id": "01e2abcd-52b0-4af3-a3ae-1fd1530b3563"
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
    },
    "eTag": "\"2500ec5a-0000-0000-0000-5bf4967d0000\"",

}
```

> [!IMPORTANT]
> <span data-ttu-id="7636e-197">Retire o `"links": { }` objeto do recurso PUT.</span><span class="sxs-lookup"><span data-stu-id="7636e-197">Remove the `"links": { }` object from the PUT resource.</span></span>

## <a name="rest-response"></a><span data-ttu-id="7636e-198">Resposta REST</span><span class="sxs-lookup"><span data-stu-id="7636e-198">REST Response</span></span>

<span data-ttu-id="7636e-199">Se for bem sucedido, este método devolve o recurso [de referência](referral-resources.md) povoado no organismo de resposta.</span><span class="sxs-lookup"><span data-stu-id="7636e-199">If successful, this method returns the populated [referral](referral-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7636e-200">Códigos de sucesso e erro de resposta</span><span class="sxs-lookup"><span data-stu-id="7636e-200">Response success and error codes</span></span>

<span data-ttu-id="7636e-201">Cada resposta vem com um código de estado HTTP que indica sucesso ou falha e informações adicionais de depuragem.</span><span class="sxs-lookup"><span data-stu-id="7636e-201">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7636e-202">Utilize uma ferramenta de rastreio de rede para ler este código, tipo de erro e parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="7636e-202">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7636e-203">Para obter a lista completa, consulte [códigos de erro](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="7636e-203">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7636e-204">Exemplo de resposta</span><span class="sxs-lookup"><span data-stu-id="7636e-204">Response example</span></span>

``` http
{
    "id": "4111fffc-f9ee-4d53-bba6-569135228642",
    "organizationId": "7d23e5ca-19dc-4eaa-aac8-5e6b559f0d1d",
    "organizationName": "Contoso Company",
    "engagementId": "37ef26aa-1d15-4533-9f93-a69bd33ab1e5",
    "createdDateTime": "2018-11-06T18:40:42.6178337Z",
    "updatedDateTime": "2018-11-06T18:43:38.9948636Z",
    "expirationDateTime": "2018-11-14T00:00:00Z",
    "status": "Closed",
    "substatus": "Won",
    "statusReason": "Customer engagement was a success!",
    "qualification": "SalesQualified",
    "type": "Independent",
    "target": [
        {
            "type": "BusinessProfileLocation",
            "id": "01e2abcd-52b0-4af3-a3ae-1fd1530b3563"
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
    "eTag": "\"2500ec5a-0000-0000-0000-5bf4967d0000\"",
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