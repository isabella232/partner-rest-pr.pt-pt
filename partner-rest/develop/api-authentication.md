---
title: Autenticação da API de Parceiro
description: Configure as definições de autenticação para utilizar a API do Parceiro com AZure AD para autenticação.
ms.date: 05/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: c5810678dccc2be1c3c084c901299961d6ba7820
ms.sourcegitcommit: 3c165938f544ff226cbe11ca21ed5aa00448d9b4
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2020
ms.locfileid: "97770502"
---
# <a name="partner-api-authentication"></a><span data-ttu-id="30a19-103">Autenticação da API de Parceiro</span><span class="sxs-lookup"><span data-stu-id="30a19-103">Partner API authentication</span></span>

<span data-ttu-id="30a19-104">Aplica-se a:</span><span class="sxs-lookup"><span data-stu-id="30a19-104">Applies to:</span></span>

- <span data-ttu-id="30a19-105">Parceiro API</span><span class="sxs-lookup"><span data-stu-id="30a19-105">Partner API</span></span>

<span data-ttu-id="30a19-106">A API parceira utiliza o Azure Ative Directory (Azure AD) para a autenticação.</span><span class="sxs-lookup"><span data-stu-id="30a19-106">The Partner API utilizes Azure Active Directory (Azure AD) for authentication.</span></span> <span data-ttu-id="30a19-107">Quando interage com a API do Parceiro, deve configurar corretamente uma aplicação AD Azure e obter um token de acesso.</span><span class="sxs-lookup"><span data-stu-id="30a19-107">When you interact with the Partner API, you must correctly configure an Azure AD application and obtain an access token.</span></span> <span data-ttu-id="30a19-108">Pode obter fichas de acesso para [aplicação e acesso ao utilizador](#application-and-user-access) ou acesso [apenas a aplicações.](#application-only-access)</span><span class="sxs-lookup"><span data-stu-id="30a19-108">You can obtain access tokens for [application and user access](#application-and-user-access) or [application-only access](#application-only-access).</span></span>

## <a name="application-and-user-access"></a><span data-ttu-id="30a19-109">Aplicação e acesso ao utilizador</span><span class="sxs-lookup"><span data-stu-id="30a19-109">Application and user access</span></span>

<span data-ttu-id="30a19-110">Este método é recomendado para configurar **a aplicação e o acesso** do utilizador à API.</span><span class="sxs-lookup"><span data-stu-id="30a19-110">This method is recommended to set up **application and user access** to the API.</span></span>

1. <span data-ttu-id="30a19-111">Inicie sessão no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="30a19-111">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
2. <span data-ttu-id="30a19-112">Escolha o serviço **Azure Ative Directory.**</span><span class="sxs-lookup"><span data-stu-id="30a19-112">Choose the **Azure Active Directory** service.</span></span>
3. <span data-ttu-id="30a19-113">Escolha **as inscrições da App** e escolha novo registo de **candidaturas.**</span><span class="sxs-lookup"><span data-stu-id="30a19-113">Choose **App registrations**, then choose **New application registration**.</span></span>
4. <span data-ttu-id="30a19-114">Crie a sua nova aplicação.</span><span class="sxs-lookup"><span data-stu-id="30a19-114">Create your new application.</span></span> <span data-ttu-id="30a19-115">Para **o tipo de aplicação**, selecione **Native**.</span><span class="sxs-lookup"><span data-stu-id="30a19-115">For **Application type**, select **Native**.</span></span> <span data-ttu-id="30a19-116">Forneça um nome e URL e, em seguida, **selecione Criar**.</span><span class="sxs-lookup"><span data-stu-id="30a19-116">Provide a name and URL, then select **Create**.</span></span>
5. <span data-ttu-id="30a19-117">Escolha **permissões API** para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="30a19-117">Choose **API permissions** for the application.</span></span> <span data-ttu-id="30a19-118">No ecrã de permissões da **API do Pedido,** escolha **Adicionar uma permissão,** em seguida, escolher **APIs que a minha organização usa**</span><span class="sxs-lookup"><span data-stu-id="30a19-118">On the **Request API permissions** screen, choose **Add a permission**, then choose **APIs my organization uses**</span></span>
6. <span data-ttu-id="30a19-119">Pesquisa rumo à API do *Microsoft Partner* *(Microsoft Dev* `4990cffe-04e8-4e8b-808a-1175604b879f` Center).</span><span class="sxs-lookup"><span data-stu-id="30a19-119">Search for the *Microsoft Partner* (*Microsoft Dev Center*) API (`4990cffe-04e8-4e8b-808a-1175604b879f`).</span></span>

    ![Screenshot do request API permissões screen com uma pesquisa para a Microsoft Partner API](../images/SearchGatewayApi.png)

7. <span data-ttu-id="30a19-121">Desa estade as **permissões delegadas** no Centro de **Parceiros.**</span><span class="sxs-lookup"><span data-stu-id="30a19-121">Set the **Delegated Permissions** to **Partner Center**.</span></span>

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Parceiro Microsoft](../images/SelectUserPermission.png)
    
8. <span data-ttu-id="30a19-123">Procure a API do *Microsoft* Partner Partner (*Microsoft Partner Center* `fa3d9a0c-3fb0-42cc-9193-47c7ecd2edbd` ).</span><span class="sxs-lookup"><span data-stu-id="30a19-123">Search for the *Microsoft Partner* (*Microsoft Partner Center*) API (`fa3d9a0c-3fb0-42cc-9193-47c7ecd2edbd`).</span></span>

    ![Screenshot do Request API permissões screen com uma pesquisa para a API do Microsoft Partner Center](../images/SearchPCApi.png)
    
9. <span data-ttu-id="30a19-125">Selecione **o Microsoft Partner Center** e verifique **user_impersonation**.</span><span class="sxs-lookup"><span data-stu-id="30a19-125">Select **Microsoft Partner Center** and check **user_impersonation**.</span></span>

10. <span data-ttu-id="30a19-126">Desa estade as **permissões delegadas** no Centro de **Parceiros.**</span><span class="sxs-lookup"><span data-stu-id="30a19-126">Set the **Delegated Permissions** to **Partner Center**.</span></span>

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Microsoft Partner Center](../images/SelectPCUserPermission.png)

## <a name="application-only-access"></a><span data-ttu-id="30a19-128">Acesso apenas para aplicações</span><span class="sxs-lookup"><span data-stu-id="30a19-128">Application-only access</span></span>

<span data-ttu-id="30a19-129">Este método é recomendado para a configuração **de acesso apenas** à aplicação às APIs.</span><span class="sxs-lookup"><span data-stu-id="30a19-129">This method is recommended for **application-only access** setup to the APIs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30a19-130">Deve fornecer o ID da aplicação, a chave de aplicação e o ID do diretório da sua aplicação AZure AD.</span><span class="sxs-lookup"><span data-stu-id="30a19-130">You must provide the application ID, application key, and directory ID from your Azure AD application.</span></span>

1. <span data-ttu-id="30a19-131">Inicie sessão no [portal do Azure](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="30a19-131">Sign in to the [Azure portal](https://portal.azure.com/).</span></span>
2. <span data-ttu-id="30a19-132">Selecione o serviço **Azure Ative Directory.**</span><span class="sxs-lookup"><span data-stu-id="30a19-132">Select the **Azure Active Directory** service.</span></span>
3. <span data-ttu-id="30a19-133">Escolha **as inscrições da App** e, em seguida, selecione Novo registo de **aplicações.**</span><span class="sxs-lookup"><span data-stu-id="30a19-133">Choose **App registrations**, then select **New application registration**.</span></span>
4. <span data-ttu-id="30a19-134">Crie a sua nova aplicação.</span><span class="sxs-lookup"><span data-stu-id="30a19-134">Create your new application.</span></span> <span data-ttu-id="30a19-135">Para **o tipo de aplicação,** escolha aplicativo **Web/API.**</span><span class="sxs-lookup"><span data-stu-id="30a19-135">For **Application type**, choose **Web app/API**.</span></span> <span data-ttu-id="30a19-136">Introduza um **nome** de aplicação e **URL**.</span><span class="sxs-lookup"><span data-stu-id="30a19-136">Enter a an application **name** and **URL**.</span></span> <span data-ttu-id="30a19-137">Em seguida, escolha **Criar**.</span><span class="sxs-lookup"><span data-stu-id="30a19-137">Then choose **Create**.</span></span>
5. <span data-ttu-id="30a19-138">Escolha **permissões API** para a aplicação.</span><span class="sxs-lookup"><span data-stu-id="30a19-138">Choose **API permissions** for the application.</span></span> <span data-ttu-id="30a19-139">Escolha **Adicionar uma permissão,** em seguida, escolher **APIs que a minha organização usa**</span><span class="sxs-lookup"><span data-stu-id="30a19-139">Choose **Add a permission**, then choose **APIs my organization uses**</span></span>
6. <span data-ttu-id="30a19-140">Pesquisa rumo à API do *Microsoft Partner* *(Microsoft Dev* `4990cffe-04e8-4e8b-808a-1175604b879f` Center).</span><span class="sxs-lookup"><span data-stu-id="30a19-140">Search for the *Microsoft Partner* (*Microsoft Dev Center*) API (`4990cffe-04e8-4e8b-808a-1175604b879f`).</span></span>

    ![Screenshot do request API permissões screen com uma pesquisa para a Microsoft Partner API](../images/SearchGatewayApi.png)

7. <span data-ttu-id="30a19-142">Desa estade as **permissões delegadas** no Centro de **Parceiros.**</span><span class="sxs-lookup"><span data-stu-id="30a19-142">Set the **Delegated Permissions** to **Partner Center**.</span></span>

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Parceiro Microsoft](../images/SelectUserPermission.png)

8. <span data-ttu-id="30a19-144">Para a aplicação que registou, escolha **Propriedades** e, em seguida, selecione **copiar o ID da aplicação.**</span><span class="sxs-lookup"><span data-stu-id="30a19-144">For the application you registered, choose **Properties** and then select **copy the Application ID**.</span></span>
9. <span data-ttu-id="30a19-145">Escolha **Definições** e, em seguida, escolha **Certificados & Segredos**.</span><span class="sxs-lookup"><span data-stu-id="30a19-145">Choose **Settings**, then choose **Certificates & Secrets**.</span></span> <span data-ttu-id="30a19-146">Escolha **O Novo Segredo do Cliente** e decrete a **expiração** para **nunca expirar.**</span><span class="sxs-lookup"><span data-stu-id="30a19-146">Choose **New Client Secret** and set the **Expiration**  to **Never expires**.</span></span> <span data-ttu-id="30a19-147">Em seguida, escolha **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="30a19-147">Then choose **Save**.</span></span>
10. <span data-ttu-id="30a19-148">No menu **Chaves,** escolha **Copiar o valor da chave.**</span><span class="sxs-lookup"><span data-stu-id="30a19-148">On the **Keys** menu, choose **Copy the key value**.</span></span> <span data-ttu-id="30a19-149">Guarde uma cópia deste valor.</span><span class="sxs-lookup"><span data-stu-id="30a19-149">Save a copy of this value.</span></span>

> [!WARNING]
> <span data-ttu-id="30a19-150">Certifique-se de guardar uma cópia do valor chave para a chave que criou.</span><span class="sxs-lookup"><span data-stu-id="30a19-150">Be sure to save a copy of the key value for the key you created.</span></span> <span data-ttu-id="30a19-151">Terá de utilizar este valor chave mais tarde para obter um token.</span><span class="sxs-lookup"><span data-stu-id="30a19-151">You will need to use this key value later to obtain a token.</span></span>

## <a name="partner-consent"></a><span data-ttu-id="30a19-152">Consentimento do parceiro</span><span class="sxs-lookup"><span data-stu-id="30a19-152">Partner consent</span></span>

<span data-ttu-id="30a19-153">No portal de gestão Azure, selecione **aplicações Enterprise**.</span><span class="sxs-lookup"><span data-stu-id="30a19-153">In the Azure management portal, select **Enterprise applications**.</span></span> <span data-ttu-id="30a19-154">Procure a aplicação que criou na secção anterior e selecione essa aplicação.</span><span class="sxs-lookup"><span data-stu-id="30a19-154">Search for the application you created in the previous section, and select that application.</span></span> <span data-ttu-id="30a19-155">Selecione **Permissões** e, em seguida, selecione **Grant Admin Consent for Partner Account**.</span><span class="sxs-lookup"><span data-stu-id="30a19-155">Select **Permissions** , then select **Grant Admin Consent for Partner Account**.</span></span>
