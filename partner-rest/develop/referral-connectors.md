---
title: Conectores de referência.
description: Sincronizar referências de parceiros com cabos CRM Dynamics 365 utilizando o Microsoft Flow.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 0a62023feb03114bb7ba1136b7700875f24c2e01
ms.sourcegitcommit: 0508b7302a3965fd5537b05c1f0397a1da014257
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2020
ms.locfileid: "97770475"
---
# <a name="referral-connectors"></a><span data-ttu-id="94b8a-103">Conectores de referência</span><span class="sxs-lookup"><span data-stu-id="94b8a-103">Referral connectors</span></span>

<span data-ttu-id="94b8a-104">Pode utilizar conectores de referência para sincronizar referências de parceiros com os leads de gestão de relacionamento com o cliente (CRM).</span><span class="sxs-lookup"><span data-stu-id="94b8a-104">You can use referral connectors to synchronize partner referrals with customer relationship management (CRM) leads.</span></span> <span data-ttu-id="94b8a-105">Pode criar um conector de referência utilizando o [Microsoft Flow](https://flow.microsoft.com) como ponto final HTTPS para receber referências de parceiros.</span><span class="sxs-lookup"><span data-stu-id="94b8a-105">You can create a referral connector using [Microsoft Flow](https://flow.microsoft.com) as the HTTPS endpoint to receive partner referrals.</span></span> <span data-ttu-id="94b8a-106">Em seguida, pode escrever a referência recebida pelo fluxo para um sistema crm como um fio.</span><span class="sxs-lookup"><span data-stu-id="94b8a-106">You can then write the referral received by the flow to a CRM system as a lead.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="94b8a-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="94b8a-107">Prerequisites</span></span>

* <span data-ttu-id="94b8a-108">Subscrição do Microsoft Flow</span><span class="sxs-lookup"><span data-stu-id="94b8a-108">Microsoft Flow subscription</span></span>
  * <span data-ttu-id="94b8a-109">Conta com acesso do administrador a esta subscrição</span><span class="sxs-lookup"><span data-stu-id="94b8a-109">Account with administrator access to this subscription</span></span>
* <span data-ttu-id="94b8a-110">ID de aplicação Azure Ative Directory (Azure AD), id de utilizador, senha e iD do inquilino (usado para aceder à API do Parceiro).</span><span class="sxs-lookup"><span data-stu-id="94b8a-110">Azure Active Directory (Azure AD) application ID, user id, password and tenant ID (used to access the Partner API).</span></span> <span data-ttu-id="94b8a-111">Para obter instruções de configuração, consulte [a autenticação do Parceiro](api-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="94b8a-111">For setup instructions, see [Partner authentication](api-authentication.md).</span></span>
* <span data-ttu-id="94b8a-112">[Subscrição de aplicativo de função Azure.](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal)</span><span class="sxs-lookup"><span data-stu-id="94b8a-112">[Azure function app](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal) subscription.</span></span>
* <span data-ttu-id="94b8a-113">[Subscrição de evento webhook do Partner Center](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events) para [eventos atualizados de referência](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-created-event) e [referenciação.](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-updated-event)</span><span class="sxs-lookup"><span data-stu-id="94b8a-113">[Partner Center webhook event](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events) subscription to [Referral Created](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-created-event) and [Referral Updated](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-updated-event) events.</span></span>
* <span data-ttu-id="94b8a-114">[Subscrição microsoft Dynamics 365](https://dynamics.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="94b8a-114">[Microsoft Dynamics 365](https://dynamics.microsoft.com) subscription</span></span>
  * <span data-ttu-id="94b8a-115">Módulo de vendas habilitado</span><span class="sxs-lookup"><span data-stu-id="94b8a-115">Sales module enabled</span></span>
  * <span data-ttu-id="94b8a-116">Conta com acesso do administrador a esta subscrição</span><span class="sxs-lookup"><span data-stu-id="94b8a-116">Account with administrator access to this subscription</span></span>

## <a name="flow-overview"></a><span data-ttu-id="94b8a-117">Visão geral do fluxo</span><span class="sxs-lookup"><span data-stu-id="94b8a-117">Flow overview</span></span>

<span data-ttu-id="94b8a-118">As referências são importadas para o CRM utilizando o seguinte fluxo:</span><span class="sxs-lookup"><span data-stu-id="94b8a-118">Referrals are imported into the CRM using the following flow:</span></span>

1. <span data-ttu-id="94b8a-119">O parceiro cria um webhook para receber notificações de encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="94b8a-119">Partner sets up a webhook to receive referral notifications.</span></span>
2. <span data-ttu-id="94b8a-120">O parceiro regista o webhook com o Partner Center.</span><span class="sxs-lookup"><span data-stu-id="94b8a-120">Partner registers the webhook with Partner Center.</span></span> <span data-ttu-id="94b8a-121">O parceiro também subscreve eventos webhook para quando as referências são criadas ou atualizadas.</span><span class="sxs-lookup"><span data-stu-id="94b8a-121">The partner also subscribes to webhook events for when referrals are created or updated.</span></span>
3. <span data-ttu-id="94b8a-122">O cliente de encaminhamento cria ou atualiza uma referência.</span><span class="sxs-lookup"><span data-stu-id="94b8a-122">Referral client creates or updates a referral.</span></span>
4. <span data-ttu-id="94b8a-123">O sistema webhook do Partner Center verifica o registo do parceiro e envia uma notificação para o webhook.</span><span class="sxs-lookup"><span data-stu-id="94b8a-123">Partner Center webhook system checks for the partner's registration and sends a notification to the webhook.</span></span>
5. <span data-ttu-id="94b8a-124">Webhook recebe a notificação.</span><span class="sxs-lookup"><span data-stu-id="94b8a-124">Webhook receives the notification.</span></span>
6. <span data-ttu-id="94b8a-125">O documento de fluxo no fluxo da Microsoft usa um símbolo para fazer uma chamada para a API de referência do Partner Center.</span><span class="sxs-lookup"><span data-stu-id="94b8a-125">Flow document in Microsoft flow uses a token to make a call to the Partner Center referral API.</span></span>
7. <span data-ttu-id="94b8a-126">O ponto final do fluxo recebe a referência.</span><span class="sxs-lookup"><span data-stu-id="94b8a-126">Flow endpoint gets the referral.</span></span>
8. <span data-ttu-id="94b8a-127">O ponto final do fluxo cria o chumbo crm.</span><span class="sxs-lookup"><span data-stu-id="94b8a-127">Flow endpoint creates the CRM lead.</span></span>

![Gráfico de fluxo que mostra os passos nesta secção para a importação de referências de parceiros para o CRM.](../images/referralwebhook.png)

## <a name="flow-document-process"></a><span data-ttu-id="94b8a-129">Processo de documento de fluxo</span><span class="sxs-lookup"><span data-stu-id="94b8a-129">Flow document process</span></span>

<span data-ttu-id="94b8a-130">O documento de fluxo para um conector de referência sincroniza uma referência de parceiro com um chumbo CRM da Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="94b8a-130">The flow document for a referral connector synchronizes a partner referral with a CRM lead from Dynamics 365.</span></span>

1. <span data-ttu-id="94b8a-131">O conector recebe um símbolo para ligar a `https://api.partner.microsoft.com/v1.0/engagements/referrals` .</span><span class="sxs-lookup"><span data-stu-id="94b8a-131">Connector gets a token to connect to `https://api.partner.microsoft.com/v1.0/engagements/referrals`.</span></span>
2. <span data-ttu-id="94b8a-132">O conector obtém uma referência que desencadeou o conector utilizando `https://api.partner.microsoft.com/v1.0/engagements/referrals/{id}` .</span><span class="sxs-lookup"><span data-stu-id="94b8a-132">Connector obtains referral that triggered the connector using `https://api.partner.microsoft.com/v1.0/engagements/referrals/{id}`.</span></span>
3. <span data-ttu-id="94b8a-133">O conector liga-se à Dinâmica 365.</span><span class="sxs-lookup"><span data-stu-id="94b8a-133">Connector connects to Dynamics 365.</span></span>
4. <span data-ttu-id="94b8a-134">O conector cria um novo chumbo ou atualiza um chumbo existente com as informações mais recentes sobre a referência.</span><span class="sxs-lookup"><span data-stu-id="94b8a-134">Connector creates a new lead or updates an existing lead with the latest information on the referral.</span></span>
5. <span data-ttu-id="94b8a-135">O conector atualiza o encaminhamento com as últimas atualizações do chumbo do CRM.</span><span class="sxs-lookup"><span data-stu-id="94b8a-135">Connector updates referral with the latest updates from the CRM lead.</span></span>

![Gráfico de fluxo mostrando os passos nesta secção para o processo do documento de fluxo.](../images/ReferralFlowSteps.png)

## <a name="sample-referral-connector"></a><span data-ttu-id="94b8a-137">Conector de referência de amostra</span><span class="sxs-lookup"><span data-stu-id="94b8a-137">Sample referral connector</span></span>

<span data-ttu-id="94b8a-138">O *conector de referência de amostra* que se segue mostra como sincronizar referências do Partner Center aos leads crm em Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="94b8a-138">The following *sample referral connector* shows how to synchronize Partner Center referrals to CRM leads in Dynamics 365.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94b8a-139">Pode escrever para diferentes CRM substituindo os [conectores de fluxo](https://flow.microsoft.com/en-us/connectors/) no código de amostra.</span><span class="sxs-lookup"><span data-stu-id="94b8a-139">You can write to different CRMs by replacing the [flow connectors](https://flow.microsoft.com/en-us/connectors/) in the sample code.</span></span>

### <a name="import-flow-synchronization-package"></a><span data-ttu-id="94b8a-140">Pacote de sincronização de fluxo de importação</span><span class="sxs-lookup"><span data-stu-id="94b8a-140">Import flow synchronization package</span></span>

<span data-ttu-id="94b8a-141">Descarregue e importe o *pacote de código de amostra* para o Microsoft Flow e ligue-se à Dynamics 365:</span><span class="sxs-lookup"><span data-stu-id="94b8a-141">Download and import the *sample code package* into Microsoft Flow and connect to Dynamics 365:</span></span>

1. <span data-ttu-id="94b8a-142">Descarregue o pacote de [sincronização](https://github.com/microsoft/Partner-Center-Referrals/blob/master/flowconnectors/MicrosoftDynamicsCRM/PartnerReferralsToDynamicsCRMLead.zip?raw=true) de fluxo a partir do [repo GitHub](https://github.com/microsoft/Partner-Center-Referrals).</span><span class="sxs-lookup"><span data-stu-id="94b8a-142">Download the [flow synchronization package](https://github.com/microsoft/Partner-Center-Referrals/blob/master/flowconnectors/MicrosoftDynamicsCRM/PartnerReferralsToDynamicsCRMLead.zip?raw=true) from the [GitHub repo](https://github.com/microsoft/Partner-Center-Referrals).</span></span>
2. <span data-ttu-id="94b8a-143">Inscreva-se no [Microsoft Flow](https://flow.microsoft.com) utilizando as credenciais apropriadas.</span><span class="sxs-lookup"><span data-stu-id="94b8a-143">Sign in to [Microsoft Flow](https://flow.microsoft.com) using the appropriate credentials.</span></span>
3. <span data-ttu-id="94b8a-144">Escolha **Os Meus Fluxos** no menu de navegação.</span><span class="sxs-lookup"><span data-stu-id="94b8a-144">Choose **My Flows** in the navigation menu.</span></span> <span data-ttu-id="94b8a-145">Em seguida, escolha **Import**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-145">Then choose **Import**.</span></span>
4. <span data-ttu-id="94b8a-146">Na página do **pacote Import,** selecione o pacote de sincronização de fluxo que descarregou.</span><span class="sxs-lookup"><span data-stu-id="94b8a-146">On the **Import package** page, select the flow synchronization package that you downloaded.</span></span> <span data-ttu-id="94b8a-147">Em seguida, escolha **upload**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-147">Then choose **Upload**.</span></span>

    ![Tela de pacote de importação para ficheiros de pacotes](../images/importPackage.png)

5. <span data-ttu-id="94b8a-149">Depois de o upload do pacote estar concluído, encontre o pacote que carregou no Conteúdo do **Pacote de Revisão.**</span><span class="sxs-lookup"><span data-stu-id="94b8a-149">After the package upload is complete, find the package you uploaded in the **Review Package Content** .</span></span>

    ![Detalhes do ecrã do pacote de importação](../images/importPackageDetails.png)

6. <span data-ttu-id="94b8a-151">Escolha o botão **Ação** (ícone de lápis) para o seu pacote carregado.</span><span class="sxs-lookup"><span data-stu-id="94b8a-151">Choose the **Action** button (pencil icon) for your uploaded package.</span></span> <span data-ttu-id="94b8a-152">Isto abre a lâmina **de configuração Import.**</span><span class="sxs-lookup"><span data-stu-id="94b8a-152">This opens the **Import setup** blade.</span></span>
7. <span data-ttu-id="94b8a-153">Escolha o seu tipo **de configuração.**</span><span class="sxs-lookup"><span data-stu-id="94b8a-153">Choose your **Setup** type.</span></span>

    * <span data-ttu-id="94b8a-154">Para criar um novo fluxo, **selecione Criar como novo,** e introduza um novo **nome de Recurso**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-154">To create a new flow, select **Create as new**, and enter a new **Resource name**.</span></span>
    * <span data-ttu-id="94b8a-155">Para atualizar um fluxo existente com o mesmo nome, selecione **Update**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-155">To update an existing flow with the same name, select **Update**.</span></span>

    ![Criar ou atualizar novo ecrã de pacakge](../images/CreateNewConnection.png)

8. <span data-ttu-id="94b8a-157">Na página do **pacote De Importação,** encontre a sua ligação Dynamics 365 na secção **de Conteúdo de Pacote de Revisão** em **Recursos Relacionados**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-157">On the **Import package** page, find your Dynamics 365 connection in the **Review Package Content** section under **Related Resources**.</span></span>
9. <span data-ttu-id="94b8a-158">Escolha o botão **Ação** (ícone de lápis) para a sua ligação Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="94b8a-158">Choose the **Action** button (pencil icon) for your Dynamics 365 connection.</span></span> <span data-ttu-id="94b8a-159">Isto abre a lâmina **de configuração Import** para este recurso relacionado.</span><span class="sxs-lookup"><span data-stu-id="94b8a-159">This opens the **Import setup** blade for this related resource.</span></span>
10. <span data-ttu-id="94b8a-160">Escolha **Criar novo** para criar uma nova ligação Dynamics 365 ou selecionar uma ligação existente.</span><span class="sxs-lookup"><span data-stu-id="94b8a-160">Choose **Create new** to create a new Dynamics 365 connection, or select an existing connection.</span></span>
11. <span data-ttu-id="94b8a-161">Verifique se a página **de pacotes Import** mostra agora o tipo de configuração de fluxo selecionado e a ligação Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="94b8a-161">Verify that the **Import package** page now shows your selected flow setup type and Dynamics 365 connection.</span></span> <span data-ttu-id="94b8a-162">Em seguida, escolha **Import**.</span><span class="sxs-lookup"><span data-stu-id="94b8a-162">Then choose **Import**.</span></span>

    ![Tela de estado do pacote de importação](../images/importStatus.png)

12. <span data-ttu-id="94b8a-164">Verifique se o seu recurso de fluxo está agora criado ou atualizado.</span><span class="sxs-lookup"><span data-stu-id="94b8a-164">Verify that your flow resource is now created or updated.</span></span>

### <a name="configure-flow-parameters"></a><span data-ttu-id="94b8a-165">Configurar parâmetros de fluxo</span><span class="sxs-lookup"><span data-stu-id="94b8a-165">Configure flow parameters</span></span>

<span data-ttu-id="94b8a-166">Configure os parâmetros do seu recurso de fluxo:</span><span class="sxs-lookup"><span data-stu-id="94b8a-166">Configure the parameters of your flow resource:</span></span>

1. <span data-ttu-id="94b8a-167">No [Microsoft Flow,](https://flow.microsoft.com)escolha **My Flows** no menu de navegação.</span><span class="sxs-lookup"><span data-stu-id="94b8a-167">In [Microsoft Flow](https://flow.microsoft.com), choose **My Flows** in the navigation menu.</span></span>
2. <span data-ttu-id="94b8a-168">Escolha o recurso de fluxo que criou ou atualizou na secção anterior.</span><span class="sxs-lookup"><span data-stu-id="94b8a-168">Choose the flow resource you created or updated in the previous section.</span></span>
3. <span data-ttu-id="94b8a-169">Na página de fluxo, escolha **editar o fluxo.**</span><span class="sxs-lookup"><span data-stu-id="94b8a-169">On the flow page, choose **Edit flow**.</span></span>
4. <span data-ttu-id="94b8a-170">Escolha a variável **ID AAD-Application (cliente)** e introduza o ID da sua aplicação AZure AD.</span><span class="sxs-lookup"><span data-stu-id="94b8a-170">Choose the **AAD-Application (client) ID** variable and enter the ID of your Azure AD application.</span></span>
5. <span data-ttu-id="94b8a-171">Escolha a variável **UserId** e introduza o seu ID do utilizador.</span><span class="sxs-lookup"><span data-stu-id="94b8a-171">Choose the **UserId** variable and enter your user ID.</span></span>
6. <span data-ttu-id="94b8a-172">Escolha a variável **UserPassword** e introduza a sua senha de utilizador.</span><span class="sxs-lookup"><span data-stu-id="94b8a-172">Choose the **UserPassword** variable and enter your user password.</span></span>
7. <span data-ttu-id="94b8a-173">Selecione a variável **de ID AAD-Directory (inquilino).**</span><span class="sxs-lookup"><span data-stu-id="94b8a-173">Select the **AAD-Directory (tenant) ID** variable.</span></span> <span data-ttu-id="94b8a-174">Insira a identificação do inquilino da sua aplicação AZure AD.</span><span class="sxs-lookup"><span data-stu-id="94b8a-174">Enter the tenant ID of your Azure AD application.</span></span>
8. <span data-ttu-id="94b8a-175">Escolha **Guardar** para salvar o seu fluxo.</span><span class="sxs-lookup"><span data-stu-id="94b8a-175">Choose **Save** to save your flow.</span></span>

    ![Tela de definições de variáveis de fluxo](../images/SetFlowVariables.png)

### <a name="authenticate-the-callback"></a><span data-ttu-id="94b8a-177">Autenticar o retorno</span><span class="sxs-lookup"><span data-stu-id="94b8a-177">Authenticate the callback</span></span>

<span data-ttu-id="94b8a-178">Autenticar o evento de retorno do Centro de Parceiros:</span><span class="sxs-lookup"><span data-stu-id="94b8a-178">Authenticate the callback event from the Partner Center:</span></span>

> [!TIP]
> <span data-ttu-id="94b8a-179">Por exemplo, consulte o código da aplicação da [função](#sample-function-app-code) da amostra na secção seguinte.</span><span class="sxs-lookup"><span data-stu-id="94b8a-179">For an example, see the [sample function app code](#sample-function-app-code) in the following section.</span></span>

1. <span data-ttu-id="94b8a-180">[Crie uma aplicação de função Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal) que [autentica o evento de retorno do Centro de Parceiros.](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#how-to-authenticate-the-callback)</span><span class="sxs-lookup"><span data-stu-id="94b8a-180">[Create an Azure function app](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal) that [authenticates the callback event from the Partner Center](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#how-to-authenticate-the-callback).</span></span>

    1. <span data-ttu-id="94b8a-181">Verifique se os cabeçalhos necessários estão presentes **(Autorização**, **x-ms-certificate-url,** e **x-ms-signature-algorithm).**</span><span class="sxs-lookup"><span data-stu-id="94b8a-181">Verify that the required headers are present (**Authorization**, **x-ms-certificate-url**, and **x-ms-signature-algorithm**).</span></span>
    2. <span data-ttu-id="94b8a-182">Faça o download do certificado utilizado para assinar o conteúdo **(x-ms-certificate-url).**</span><span class="sxs-lookup"><span data-stu-id="94b8a-182">Download the certificate used to sign the content (**x-ms-certificate-url**).</span></span>
    3. <span data-ttu-id="94b8a-183">Verifique a cadeia de certificados.</span><span class="sxs-lookup"><span data-stu-id="94b8a-183">Verify the certificate chain.</span></span>
    4. <span data-ttu-id="94b8a-184">Verifique a **Organização** do certificado.</span><span class="sxs-lookup"><span data-stu-id="94b8a-184">Verify the **Organization** of the certificate.</span></span>
    5. <span data-ttu-id="94b8a-185">Leia o conteúdo com a codificação UTF-8 num tampão.</span><span class="sxs-lookup"><span data-stu-id="94b8a-185">Read the content with UTF-8 encoding into a buffer.</span></span>
    6. <span data-ttu-id="94b8a-186">Crie um RSA Crypto Provider.</span><span class="sxs-lookup"><span data-stu-id="94b8a-186">Create an RSA Crypto Provider.</span></span>
    7. <span data-ttu-id="94b8a-187">[Verifique se a assinatura corresponde ao](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#example-for-signature-validation) que foi assinado com o algoritmo de haxixe especificado (por exemplo, SHA256).</span><span class="sxs-lookup"><span data-stu-id="94b8a-187">[Verify that the signature matches](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#example-for-signature-validation) what was signed with the specified hash algorithm (for example, SHA256).</span></span>
    8. <span data-ttu-id="94b8a-188">Se a verificação for bem sucedida, uma mensagem **OK** é devolvida.</span><span class="sxs-lookup"><span data-stu-id="94b8a-188">If the verification succeeds, an **OK** message is returned.</span></span>

2. <span data-ttu-id="94b8a-189">Note o URI de retorno de chamada gerado para o ponto final HTTP da sua aplicação de funções.</span><span class="sxs-lookup"><span data-stu-id="94b8a-189">Note the generated callback URI for your function app's HTTP endpoint.</span></span> <span data-ttu-id="94b8a-190">Este URI é apresentado quando cria a sua aplicação de função.</span><span class="sxs-lookup"><span data-stu-id="94b8a-190">This URI is displayed when you create your function app.</span></span> <span data-ttu-id="94b8a-191">Também pode encontrar este URI na página de recursos Azure da sua aplicação de funções.</span><span class="sxs-lookup"><span data-stu-id="94b8a-191">You can also find this URI on your function app's Azure resource page.</span></span>
3. <span data-ttu-id="94b8a-192">No [Microsoft Flow,](https://flow.microsoft.com)edite o fluxo "Partner Referral to Microsoft Dynamics CRM Lead" que importou na secção *[Pacote de sincronização de fluxos de importação](#import-flow-synchronization-package)*.</span><span class="sxs-lookup"><span data-stu-id="94b8a-192">In [Microsoft Flow](https://flow.microsoft.com), edit the flow "Partner Referral to Microsoft Dynamics CRM Lead" that you imported in the section *[Import flow synchronization package](#import-flow-synchronization-package)*.</span></span>

    1. <span data-ttu-id="94b8a-193">Adicione o valor do URI da aplicação de função ao passo de "validação do certificado de gancho web".</span><span class="sxs-lookup"><span data-stu-id="94b8a-193">Add the value of the function app's URI to the "web hook certificate validation" step.</span></span>
    2. <span data-ttu-id="94b8a-194">Copie e cole o URI de chamada da sua aplicação de função no documento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="94b8a-194">Copy and paste your function app's callback URI into the flow document.</span></span>
    3. <span data-ttu-id="94b8a-195">Guarde o seu documento de fluxo.</span><span class="sxs-lookup"><span data-stu-id="94b8a-195">Save your flow document.</span></span>

#### <a name="sample-function-app-code"></a><span data-ttu-id="94b8a-196">Código de aplicação de função da amostra</span><span class="sxs-lookup"><span data-stu-id="94b8a-196">Sample function app code</span></span>

```csharp
using System.Net;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Primitives;
using Newtonsoft.Json;
using Microsoft.Azure.WebJobs;
using Microsoft.Extensions.Logging;
using System;
using System.IO;
using System.Linq;
using System.Net.Http;
using System.Security.Cryptography.X509Certificates;
using System.Text;
using System.Threading.Tasks;

public static async Task<IActionResult> Run(HttpRequest req, ILogger log)
{
    string requestBody = null;
    if (!string.IsNullOrWhiteSpace(GetFirstValueFromHeader(req, "x-ms-certificate-url")) && !string.IsNullOrWhiteSpace(GetFirstValueFromHeader(req, "x-ms-signature-algorithm")))
    {
        var certificateUrl = req?.Headers["x-ms-certificate-url"].First();
        try
        {
            string resultContent = null;
            using (var client = new HttpClient())
            {
                var result = await client.GetAsync(req.Headers["x-ms-certificate-url"].First());
                resultContent = await result.Content.ReadAsStringAsync();
                log.LogInformation(resultContent);
            }
            if (!string.IsNullOrEmpty(resultContent))
            {
                var certificate = new X509Certificate2(Encoding.UTF8.GetBytes(resultContent));
                var validationResult = certificate.Verify() && certificate.Issuer.Contains("O=Microsoft Corporation");
                if (validationResult)
                {
                    return new OkResult();
                }
                else
                {
                    return new BadRequestResult();
                }
            }
        }
        catch (Exception)
        {
            new BadRequestObjectResult("Certificate could not be retrieved, invalid caller to flow");
        }

        requestBody = await new StreamReader(req.Body).ReadToEndAsync();
        dynamic data = JsonConvert.DeserializeObject(requestBody);
    }
    else
    {
        new BadRequestObjectResult("Missing headers");
    }

    return new BadRequestObjectResult("Certificate validation failed");
}

private static string GetFirstValueFromHeader(HttpRequest request, string headerName)
{
    StringValues matchingHeaderValues;
    request.Headers.TryGetValue(headerName, out matchingHeaderValues);
    return matchingHeaderValues.Count != 0 ? matchingHeaderValues.First() : string.Empty;
}
```

### <a name="register-flow-with-partner-center"></a><span data-ttu-id="94b8a-197">Registar fluxo com o Partner Center</span><span class="sxs-lookup"><span data-stu-id="94b8a-197">Register flow with Partner Center</span></span>

<span data-ttu-id="94b8a-198">Registe o seu recurso de fluxo com o Partner Center para desencadear o fluxo e receber eventos webhook:</span><span class="sxs-lookup"><span data-stu-id="94b8a-198">Register your flow resource with the Partner Center to trigger the flow and receive webhook events:</span></span>

1. <span data-ttu-id="94b8a-199">No [Microsoft Flow,](https://flow.microsoft.com)escolha **My Flows** no menu de navegação.</span><span class="sxs-lookup"><span data-stu-id="94b8a-199">In [Microsoft Flow](https://flow.microsoft.com), choose **My Flows** in the navigation menu.</span></span>
2. <span data-ttu-id="94b8a-200">Escolha o fluxo que criou ou atualizou.</span><span class="sxs-lookup"><span data-stu-id="94b8a-200">Choose the flow you created or updated.</span></span>
3. <span data-ttu-id="94b8a-201">Na página de fluxo, escolha **editar o fluxo.**</span><span class="sxs-lookup"><span data-stu-id="94b8a-201">On the flow page, choose **Edit flow**.</span></span>
4. <span data-ttu-id="94b8a-202">Copie e guarde o **URL HTTP POST do** fluxo.</span><span class="sxs-lookup"><span data-stu-id="94b8a-202">Copy and save the flow's **HTTP POST URL**.</span></span> <span data-ttu-id="94b8a-203">Terá de utilizar este URL para ativar o fluxo.</span><span class="sxs-lookup"><span data-stu-id="94b8a-203">You will need to use this URL to trigger the flow.</span></span>
5. <span data-ttu-id="94b8a-204">[Registe-se para receber eventos webhook](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#register-to-receive-events) quando as referências forem criadas ou atualizadas.</span><span class="sxs-lookup"><span data-stu-id="94b8a-204">[Register to receive webhook events](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#register-to-receive-events) when referrals are created or updated.</span></span> <span data-ttu-id="94b8a-205">Utilize o seguinte formato corporal:</span><span class="sxs-lookup"><span data-stu-id="94b8a-205">Use the following body format:</span></span>

```json
{
    "WebhookUrl": "<<FlowUrl>>",
    "WebhookEvents": [
        "referral-created",
        "referral-updated"
    ],
    "signatureTokenToMsSignatureHeader": true
}
```
