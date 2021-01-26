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
# <a name="partner-api-authentication"></a>Autenticação da API de Parceiro

Aplica-se a:

- Parceiro API

A API parceira utiliza o Azure Ative Directory (Azure AD) para a autenticação. Quando interage com a API do Parceiro, deve configurar corretamente uma aplicação AD Azure e obter um token de acesso. Pode obter fichas de acesso para [aplicação e acesso ao utilizador](#application-and-user-access) ou acesso [apenas a aplicações.](#application-only-access)

## <a name="application-and-user-access"></a>Aplicação e acesso ao utilizador

Este método é recomendado para configurar **a aplicação e o acesso** do utilizador à API.

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).
2. Escolha o serviço **Azure Ative Directory.**
3. Escolha **as inscrições da App** e escolha novo registo de **candidaturas.**
4. Crie a sua nova aplicação. Para **o tipo de aplicação**, selecione **Native**. Forneça um nome e URL e, em seguida, **selecione Criar**.
5. Escolha **permissões API** para a aplicação. No ecrã de permissões da **API do Pedido,** escolha **Adicionar uma permissão,** em seguida, escolher **APIs que a minha organização usa**
6. Pesquisa rumo à API do *Microsoft Partner* *(Microsoft Dev* `4990cffe-04e8-4e8b-808a-1175604b879f` Center).

    ![Screenshot do request API permissões screen com uma pesquisa para a Microsoft Partner API](../images/SearchGatewayApi.png)

7. Desa estade as **permissões delegadas** no Centro de **Parceiros.**

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Parceiro Microsoft](../images/SelectUserPermission.png)
    
8. Procure a API do *Microsoft* Partner Partner (*Microsoft Partner Center* `fa3d9a0c-3fb0-42cc-9193-47c7ecd2edbd` ).

    ![Screenshot do Request API permissões screen com uma pesquisa para a API do Microsoft Partner Center](../images/SearchPCApi.png)
    
9. Selecione **o Microsoft Partner Center** e verifique **user_impersonation**.

10. Desa estade as **permissões delegadas** no Centro de **Parceiros.**

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Microsoft Partner Center](../images/SelectPCUserPermission.png)

## <a name="application-only-access"></a>Acesso apenas para aplicações

Este método é recomendado para a configuração **de acesso apenas** à aplicação às APIs.

> [!IMPORTANT]
> Deve fornecer o ID da aplicação, a chave de aplicação e o ID do diretório da sua aplicação AZure AD.

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).
2. Selecione o serviço **Azure Ative Directory.**
3. Escolha **as inscrições da App** e, em seguida, selecione Novo registo de **aplicações.**
4. Crie a sua nova aplicação. Para **o tipo de aplicação,** escolha aplicativo **Web/API.** Introduza um **nome** de aplicação e **URL**. Em seguida, escolha **Criar**.
5. Escolha **permissões API** para a aplicação. Escolha **Adicionar uma permissão,** em seguida, escolher **APIs que a minha organização usa**
6. Pesquisa rumo à API do *Microsoft Partner* *(Microsoft Dev* `4990cffe-04e8-4e8b-808a-1175604b879f` Center).

    ![Screenshot do request API permissões screen com uma pesquisa para a Microsoft Partner API](../images/SearchGatewayApi.png)

7. Desa estade as **permissões delegadas** no Centro de **Parceiros.**

    ![Screenshot do ecrã de configuração de permissões delegadas para a API do Parceiro Microsoft](../images/SelectUserPermission.png)

8. Para a aplicação que registou, escolha **Propriedades** e, em seguida, selecione **copiar o ID da aplicação.**
9. Escolha **Definições** e, em seguida, escolha **Certificados & Segredos**. Escolha **O Novo Segredo do Cliente** e decrete a **expiração** para **nunca expirar.** Em seguida, escolha **Guardar**.
10. No menu **Chaves,** escolha **Copiar o valor da chave.** Guarde uma cópia deste valor.

> [!WARNING]
> Certifique-se de guardar uma cópia do valor chave para a chave que criou. Terá de utilizar este valor chave mais tarde para obter um token.

## <a name="partner-consent"></a>Consentimento do parceiro

No portal de gestão Azure, selecione **aplicações Enterprise**. Procure a aplicação que criou na secção anterior e selecione essa aplicação. Selecione **Permissões** e, em seguida, selecione **Grant Admin Consent for Partner Account**.
