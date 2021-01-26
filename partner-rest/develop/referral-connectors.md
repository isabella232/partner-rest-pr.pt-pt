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
# <a name="referral-connectors"></a>Conectores de referência

Pode utilizar conectores de referência para sincronizar referências de parceiros com os leads de gestão de relacionamento com o cliente (CRM). Pode criar um conector de referência utilizando o [Microsoft Flow](https://flow.microsoft.com) como ponto final HTTPS para receber referências de parceiros. Em seguida, pode escrever a referência recebida pelo fluxo para um sistema crm como um fio.

## <a name="prerequisites"></a>Pré-requisitos

* Subscrição do Microsoft Flow
  * Conta com acesso do administrador a esta subscrição
* ID de aplicação Azure Ative Directory (Azure AD), id de utilizador, senha e iD do inquilino (usado para aceder à API do Parceiro). Para obter instruções de configuração, consulte [a autenticação do Parceiro](api-authentication.md).
* [Subscrição de aplicativo de função Azure.](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal)
* [Subscrição de evento webhook do Partner Center](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events) para [eventos atualizados de referência](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-created-event) e [referenciação.](https://docs.microsoft.com/partner-center/develop/partner-center-webhook-events#referral-updated-event)
* [Subscrição microsoft Dynamics 365](https://dynamics.microsoft.com)
  * Módulo de vendas habilitado
  * Conta com acesso do administrador a esta subscrição

## <a name="flow-overview"></a>Visão geral do fluxo

As referências são importadas para o CRM utilizando o seguinte fluxo:

1. O parceiro cria um webhook para receber notificações de encaminhamento.
2. O parceiro regista o webhook com o Partner Center. O parceiro também subscreve eventos webhook para quando as referências são criadas ou atualizadas.
3. O cliente de encaminhamento cria ou atualiza uma referência.
4. O sistema webhook do Partner Center verifica o registo do parceiro e envia uma notificação para o webhook.
5. Webhook recebe a notificação.
6. O documento de fluxo no fluxo da Microsoft usa um símbolo para fazer uma chamada para a API de referência do Partner Center.
7. O ponto final do fluxo recebe a referência.
8. O ponto final do fluxo cria o chumbo crm.

![Gráfico de fluxo que mostra os passos nesta secção para a importação de referências de parceiros para o CRM.](../images/referralwebhook.png)

## <a name="flow-document-process"></a>Processo de documento de fluxo

O documento de fluxo para um conector de referência sincroniza uma referência de parceiro com um chumbo CRM da Dynamics 365.

1. O conector recebe um símbolo para ligar a `https://api.partner.microsoft.com/v1.0/engagements/referrals` .
2. O conector obtém uma referência que desencadeou o conector utilizando `https://api.partner.microsoft.com/v1.0/engagements/referrals/{id}` .
3. O conector liga-se à Dinâmica 365.
4. O conector cria um novo chumbo ou atualiza um chumbo existente com as informações mais recentes sobre a referência.
5. O conector atualiza o encaminhamento com as últimas atualizações do chumbo do CRM.

![Gráfico de fluxo mostrando os passos nesta secção para o processo do documento de fluxo.](../images/ReferralFlowSteps.png)

## <a name="sample-referral-connector"></a>Conector de referência de amostra

O *conector de referência de amostra* que se segue mostra como sincronizar referências do Partner Center aos leads crm em Dynamics 365.

> [!IMPORTANT]
> Pode escrever para diferentes CRM substituindo os [conectores de fluxo](https://flow.microsoft.com/en-us/connectors/) no código de amostra.

### <a name="import-flow-synchronization-package"></a>Pacote de sincronização de fluxo de importação

Descarregue e importe o *pacote de código de amostra* para o Microsoft Flow e ligue-se à Dynamics 365:

1. Descarregue o pacote de [sincronização](https://github.com/microsoft/Partner-Center-Referrals/blob/master/flowconnectors/MicrosoftDynamicsCRM/PartnerReferralsToDynamicsCRMLead.zip?raw=true) de fluxo a partir do [repo GitHub](https://github.com/microsoft/Partner-Center-Referrals).
2. Inscreva-se no [Microsoft Flow](https://flow.microsoft.com) utilizando as credenciais apropriadas.
3. Escolha **Os Meus Fluxos** no menu de navegação. Em seguida, escolha **Import**.
4. Na página do **pacote Import,** selecione o pacote de sincronização de fluxo que descarregou. Em seguida, escolha **upload**.

    ![Tela de pacote de importação para ficheiros de pacotes](../images/importPackage.png)

5. Depois de o upload do pacote estar concluído, encontre o pacote que carregou no Conteúdo do **Pacote de Revisão.**

    ![Detalhes do ecrã do pacote de importação](../images/importPackageDetails.png)

6. Escolha o botão **Ação** (ícone de lápis) para o seu pacote carregado. Isto abre a lâmina **de configuração Import.**
7. Escolha o seu tipo **de configuração.**

    * Para criar um novo fluxo, **selecione Criar como novo,** e introduza um novo **nome de Recurso**.
    * Para atualizar um fluxo existente com o mesmo nome, selecione **Update**.

    ![Criar ou atualizar novo ecrã de pacakge](../images/CreateNewConnection.png)

8. Na página do **pacote De Importação,** encontre a sua ligação Dynamics 365 na secção **de Conteúdo de Pacote de Revisão** em **Recursos Relacionados**.
9. Escolha o botão **Ação** (ícone de lápis) para a sua ligação Dynamics 365. Isto abre a lâmina **de configuração Import** para este recurso relacionado.
10. Escolha **Criar novo** para criar uma nova ligação Dynamics 365 ou selecionar uma ligação existente.
11. Verifique se a página **de pacotes Import** mostra agora o tipo de configuração de fluxo selecionado e a ligação Dynamics 365. Em seguida, escolha **Import**.

    ![Tela de estado do pacote de importação](../images/importStatus.png)

12. Verifique se o seu recurso de fluxo está agora criado ou atualizado.

### <a name="configure-flow-parameters"></a>Configurar parâmetros de fluxo

Configure os parâmetros do seu recurso de fluxo:

1. No [Microsoft Flow,](https://flow.microsoft.com)escolha **My Flows** no menu de navegação.
2. Escolha o recurso de fluxo que criou ou atualizou na secção anterior.
3. Na página de fluxo, escolha **editar o fluxo.**
4. Escolha a variável **ID AAD-Application (cliente)** e introduza o ID da sua aplicação AZure AD.
5. Escolha a variável **UserId** e introduza o seu ID do utilizador.
6. Escolha a variável **UserPassword** e introduza a sua senha de utilizador.
7. Selecione a variável **de ID AAD-Directory (inquilino).** Insira a identificação do inquilino da sua aplicação AZure AD.
8. Escolha **Guardar** para salvar o seu fluxo.

    ![Tela de definições de variáveis de fluxo](../images/SetFlowVariables.png)

### <a name="authenticate-the-callback"></a>Autenticar o retorno

Autenticar o evento de retorno do Centro de Parceiros:

> [!TIP]
> Por exemplo, consulte o código da aplicação da [função](#sample-function-app-code) da amostra na secção seguinte.

1. [Crie uma aplicação de função Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-function-app-portal) que [autentica o evento de retorno do Centro de Parceiros.](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#how-to-authenticate-the-callback)

    1. Verifique se os cabeçalhos necessários estão presentes **(Autorização**, **x-ms-certificate-url,** e **x-ms-signature-algorithm).**
    2. Faça o download do certificado utilizado para assinar o conteúdo **(x-ms-certificate-url).**
    3. Verifique a cadeia de certificados.
    4. Verifique a **Organização** do certificado.
    5. Leia o conteúdo com a codificação UTF-8 num tampão.
    6. Crie um RSA Crypto Provider.
    7. [Verifique se a assinatura corresponde ao](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#example-for-signature-validation) que foi assinado com o algoritmo de haxixe especificado (por exemplo, SHA256).
    8. Se a verificação for bem sucedida, uma mensagem **OK** é devolvida.

2. Note o URI de retorno de chamada gerado para o ponto final HTTP da sua aplicação de funções. Este URI é apresentado quando cria a sua aplicação de função. Também pode encontrar este URI na página de recursos Azure da sua aplicação de funções.
3. No [Microsoft Flow,](https://flow.microsoft.com)edite o fluxo "Partner Referral to Microsoft Dynamics CRM Lead" que importou na secção *[Pacote de sincronização de fluxos de importação](#import-flow-synchronization-package)*.

    1. Adicione o valor do URI da aplicação de função ao passo de "validação do certificado de gancho web".
    2. Copie e cole o URI de chamada da sua aplicação de função no documento de fluxo.
    3. Guarde o seu documento de fluxo.

#### <a name="sample-function-app-code"></a>Código de aplicação de função da amostra

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

### <a name="register-flow-with-partner-center"></a>Registar fluxo com o Partner Center

Registe o seu recurso de fluxo com o Partner Center para desencadear o fluxo e receber eventos webhook:

1. No [Microsoft Flow,](https://flow.microsoft.com)escolha **My Flows** no menu de navegação.
2. Escolha o fluxo que criou ou atualizou.
3. Na página de fluxo, escolha **editar o fluxo.**
4. Copie e guarde o **URL HTTP POST do** fluxo. Terá de utilizar este URL para ativar o fluxo.
5. [Registe-se para receber eventos webhook](https://docs.microsoft.com/partner-center/develop/partner-center-webhooks#register-to-receive-events) quando as referências forem criadas ou atualizadas. Utilize o seguinte formato corporal:

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
