---
title: Recursos de referência
description: Os recursos de encaminhamento representam um chumbo de vendas diretamente de um cliente, Microsoft, ou outro parceiro.
ms.date: 05/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.localizationpriority: medium
ms.openlocfilehash: 08438d208da57a4df40aeb609b14b6b6a6128d45
ms.sourcegitcommit: 0508b7302a3965fd5537b05c1f0397a1da014257
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/27/2020
ms.locfileid: "97770476"
---
# <a name="referral-resources"></a>Recursos de referência

Aplica-se a:

- Partner Center

Estes recursos representam um chumbo de vendas diretamente de um cliente, Microsoft, ou outro parceiro.

## <a name="referral"></a>Encaminhamento

Representa a referência.

| Propriedade              | Tipo                                              | Descrição                                                                                                       |
|-----------------------|---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| Id                    | string                                            | A identificação desta referência.                                                                                         |
| EngagementId          | string                                            | O EngagementID para esta referência. Várias referências podem ser associadas a um único EngagementID                 |
| Nome                  | string                                            | O nome da Referência.                 |
| ExternoReferênciaId   | string                                            | Um identificador externo para a referência. Exemplo: Guarde o seu próprio ID de chumbo/oportunidade Dynamics 365                    |
| CreatedDateTime       | cadeia no formato de hora de data UTC                    | A data em que a referência foi criada.                                                                                |
| Hora do Natal Atualizado       | cadeia no formato de hora de data UTC                    | A data em que a referência foi atualizada pela última vez.                                                                           |
| Expiração Hora do Fim    | cadeia no formato de hora de data UTC                    | A data da referência expirará.                                                                                |
| Estado                | [ReferênciaStatus](referral-resources.md#referralstatus)      | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento. |
| Subtátuo          | [ReferênciaSubstato](referral-resources.md#referralsubstatus)      | Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o sub estatuto de encaminhamento. |
| StatusReason          | string                                            | Uma mensagem descritiva sobre o estado. Exemplo: Por que a referência foi perdida? |
| Tipo de Referência          | [Tipo de Referência](referral-resources.md#referraltype)          | Representa o tipo de referência.                                                                                     |
| Qualificação         | [Qualificação de ReferênciaS](referral-resources.md#referralqualification)| Representa a qualidade da referência.                                                                           |
| CustomerProfile       | [CustomerProfile](referral-resources.md#customerprofile)    | Informação sobre o cliente.                                                                                     |
| Consent (Consentimento)               | [Consent (Consentimento)](referral-resources.md#consent)                    | O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores.         |
| Detalhes               | [ReferênciaDetails](referral-resources.md#referraldetails)    | Detalhes do cliente, notas, valor da oferta, data de fecho de moeda.                                                                |
| Equipa                  | [Membro](referral-resources.md#member)                      | Representa os utilizadores nas organizações envolvidas.                                |
| ConvidarContexto         | [ConvidarContexto](referral-resources.md#invitecontext)        | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.  |
| ETag                  | string                                            | Os ETags são utilizados e necessários para verificação de concordância na atualização dos recursos. |
| Destino         | [ReferênciaTarget](referral-resources.md#target)        | Representa informações adicionais que um utilizador pode fornecer ao convidar outra organização para o envolvimento do parceiro.  |

## <a name="referralstatus"></a>ReferênciaStatus

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.

| Valor           | Descrição                                                                                |
|-----------------|---------------------------------------------------------------------------------------------|
| Nenhum            |                                                                                             |
| Novo             | Representa uma nova referência.                                                                 |
| Ativo          | Representa uma referência ativa.                                                             |
| Fechado          | Representa uma referência fechada.                                                              |

## <a name="referralsubstatus"></a>ReferênciaSubstato

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.

| Valor           | Descrição                                                                                |
|-----------------|--------------------------------------------------------------------------------------------|
| Nenhum            |                                                                                            |
| Pendente         | Representa uma nova referência que está pendente.                                                 |
| Recebido        | Representa uma nova referência que foi recebida.                   |
| Aceite        | Representa uma referência ativa que foi aceite.                                                    |
| Vencido             | Representa uma referência fechada que foi ganha.                                            |
| Perdido            | Representa uma referência fechada que se perdeu.                                           |
| Recusado        | Representa uma referência fechada que foi recusada.                                       |
| Fora do prazo         | Representa uma referência fechada que expirou.                                             |

### <a name="status--substatus-transition-states"></a>Estado & Estados de transição substatus

| Estado                | Transição de Estado Permitida     | Substatus permitido                |
|-----------------------|-------------------------------|---------------------------------------|
| Novo                   | Novo, Ativo, Fechado           | Pendente, Recebido                     |
| Ativo                | Ativo, Fechado                | Aceite                              |
| Fechado                | Fechado                        | Won, Lost, Declined, expirou          |

## <a name="referraltype"></a>Tipo de Referência

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o tipo de referência.

| Propriedade              | Descrição                                                                     |
|-----------------------|---------------------------------------------------------------------------------|
| Partilhado                | Representa uma referência na qual todas as partes envolvidas colaborarão para encerrar.  |
| Independente           | Representa uma referência em que duas partes colaborarão para encerrar.           |

## <a name="referralqualification"></a>Qualificação de ReferênciaS

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o estado de encaminhamento.

| Valor                | Descrição                                                                                 |
|----------------------|---------------------------------------------------------------------------------------------|
| Nenhum                 | Representa uma referência que não tem medida de qualidade associada.                               |
| Direct               | Representa uma referência que foi criada diretamente por um cliente.                         |
| MarketingQualizado   | Representa uma referência que foi gerada através de sistemas de automação de marketing da Microsoft.   |
| VendasQualificadas       | Representa uma referência de um agente de vendas da Microsoft.                                         |

## <a name="customerprofile"></a>CustomerProfile

Contém as informações de contacto do cliente.

| Propriedade | Tipo                                                   | Descrição                                            |
|----------|--------------------------------------------------------|--------------------------------------------------------|
| Nome     | string                                                 | O nome da organização do cliente.                        |
| Endereço  | [Endereço](referral-resources.md#address)                         | O endereço do cliente.                           |
| Tamanho     | string                                                 | O número de colaboradores na organização de clientes. |
| Equipa     | [Membro](referral-resources.md#member)                           | Os contactos para a organização do cliente.            |
| IDs      | [CustomerProfileType](referral-resources.md#customerprofiletype) | Um [conjunto](https://docs.microsoft.com/dotnet/api/system.array) de valores que indicam IDs Externos para o cliente.                        |

## <a name="customerprofiletype"></a>CustomerProfileType

Contém os IDs Externos para o cliente.

| Propriedade | Tipo   | Descrição                                                                           |
|----------|--------|---------------------------------------------------------------------------------------|
| Duns     | string | O [número de Dun & Bradstreet](https://www.dnb.com/duns-number.html) para o cliente. |
| Externo | string | Uma identificação de cliente única para a sua organização.                                            |

## <a name="address"></a>Endereço

Um endereço para usar para o cliente.

| Propriedade     | Tipo   | Descrição                                                |
|--------------|--------|------------------------------------------------------------|
| Linha de Endereço1 | string | A primeira linha do endereço.                             |
| Linha de Endereço2 | string | A segunda linha do endereço. Esta propriedade é opcional. |
| City         | string | A cidade.                                                  |
| Estado        | string | O Estado.                                                 |
| PostalCode   | string | O código postal ou código postal                                |
| País      | string | O país/região no [formato de código de país ISO.](https://docs.microsoft.com/dotnet/api/system.globalization.regioninfo.threeletterisoregionname?view=netframework-4.7.2)             |
| Região       | string | A região.                                                |

## <a name="member"></a>Membro

Descreve informações de contacto para um indivíduo específico.

| Propriedade    | Tipo   | Descrição                  |
|-------------|--------|------------------------------|
| FirstName   | string | O primeiro nome do contacto.    |
| LastName    | string | O sobrenome do contacto.     |
| PhoneNumber | string | O número de telefone do contacto.  |
| E-mail       | string | O endereço de e-mail do contacto. |
| ContatoPreferência       | [ContatoPreferência](referral-resources.md#contactpreference) | A preferência do contacto por receber notificações por e-mail. |

## <a name="contactpreference"></a>ContatoPreferência

Descreve as preferências de contacto para receber notificações de e-mail.

| Propriedade    | Tipo   | Descrição                  |
|-------------|--------|------------------------------|
| Região   | string | A localidade da notificação por e-mail. [Todas as Culturas,](https://docs.microsoft.com/dotnet/api/system.globalization.culturetypes?view=netframework-4.7.2#System_Globalization_CultureTypes_AllCultures) [NeutralCultures](https://docs.microsoft.com/dotnet/api/system.globalization.culturetypes?view=netframework-4.7.2#System_Globalization_CultureTypes_NeutralCultures)e [SpecificCultures](https://docs.microsoft.com/dotnet/api/system.globalization.culturetypes?view=netframework-4.7.2#System_Globalization_CultureTypes_SpecificCultures) são apoiadas  |
| DesativaçõesNotificações    | bool | Irá desativar as notificações de e-mail para o utilizador.     |

## <a name="consent"></a>Consent (Consentimento)

O Consentimento assinala a partilha de informações com outras organizações e permite-lhes contactar os utilizadores.

| Propriedade                                         | Tipo      | Descrição                                                                                |
|--------------------------------------------------|-----------|--------------------------------------------------------------------------------------------|
| ConsentToShareInfoWithOthers                   | boolean   | Indica consentimento para partilhar informações pessoalmente identificáveis (PII) com outros.             |
| ConsentToContact                                 | boolean   | Indica consentimento para contactar os utilizadores.  |

## <a name="invitecontext"></a>ConvidarContexto

Informações adicionais que podem ser partilhadas ao convidar outra organização.

| Propriedade              | Tipo                                                       | Descrição                                                                   |
|-----------------------|------------------------------------------------------------|-------------------------------------------------------------------------------|
| Notas                 | string                                                     | Notas adicionais para a organização recetora.                |
| Convidados Por | [Convidados Por](referral-resources.md#invitedby)                                     | A identificação da organização que enviou a referência.                                   |

## <a name="invitedby"></a>Convidados Por

Informações adicionais que podem ser partilhadas ao convidar outra organização.

| Propriedade              | Tipo                                                       | Descrição                                                                   |
|-----------------------|------------------------------------------------------------|-------------------------------------------------------------------------------|
| OrganizationId        | string                                                     | A identificação da organização que enviou a referência.                |
| OrganizationName      | string                                                     | O nome da organização que enviou a referência.                                   |

## <a name="referraldetails"></a>ReferênciaDetails

Representa os detalhes de encaminhamento.

| Propriedade              | Tipo                                                       | Descrição                                                                   |
|-----------------------|------------------------------------------------------------|-------------------------------------------------------------------------------|
| Notas                 | string                                                     | Notas adicionais para a organização recetora.                |
| DealValue             | decimal                                                    | Valor da referência.                                    |
| Moeda              | string                                                    | O [símbolo da moeda ISO 4217](https://docs.microsoft.com/dotnet/api/system.globalization.regioninfo.isocurrencysymbol?view=netframework-4.7.2)                                   |
| Hora de Encerramento       | cadeia no formato de hora de data UTC                         | Data que o cliente está procurando fechar por perto.                           |
| Requisitos          | [Pedidos de Referência](referral-resources.md#referralrequirements)   | Indústria, produtos, tipo de serviço e soluções que o cliente está interessado.|

## <a name="referralrequirements"></a>Pedidos de Referência

Contém os requisitos do cliente.

| Propriedade        | Tipo                                                         | Descrição                                          |
|-----------------|--------------------------------------------------------------|------------------------------------------------------|
| Indústrias      | [Tag](referral-resources.md#tag)                                       | As indústrias em que o cliente está interessado.        |
| Produtos        | [Tag](referral-resources.md#tag)                                       | Os produtos em que o cliente está interessado.          |
| Serviços        | [Tag](referral-resources.md#tag)                                       | Os serviços que o cliente está interessado.          |
| Soluções       | [Marca de Soluções](referral-resources.md#solutiontag)                       | As soluções que o cliente está interessado.                             |

## <a name="solutiontag"></a>Marca de Soluções

Contém os detalhes da solução.

| Propriedade        | Tipo                                         | Descrição                                          |
|-----------------|----------------------------------------------|------------------------------------------------------|
| Id              | string                                       | A identificação da solução.        |
| Nome            | string                                       | O nome da solução.          |
| SolutionType    | [SolutionType](referral-resources.md#solutiontype)     | O tipo de solução.          |

## <a name="solutiontype"></a>SolutionType

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o tipo de solução.

| Propriedade        | Descrição                                                     |
|-----------------|-----------------------------------------------------------------|
| Nenhum            |                                                                  |
| Categoria        |  Alavanca nomes de solução pré-definidos.                            |
| Nome            |  Capacidade de referência soluções do catálogo da Microsoft. |

## <a name="target"></a>Destino

Descreve o alvo de referência.

| Propriedade                  | Tipo                                                  | Descrição                                                   |
|---------------------------|-------------------------------------------------------|---------------------------------------------------------------|
| Id                        | string                                                | A identificação do alvo de referência. |
| Tipo                      | [ReferênciaTargetType](referral-resources.md#targettype) | Tipo alvo de encaminhamento |

## <a name="targettype"></a>TargetType

Um [Enum](https://docs.microsoft.com/dotnet/api/system.enum) com valores que indicam o tipo de solução.

| Propriedade        | Descrição                                                     |
|-----------------|-----------------------------------------------------------------|
| Nenhum            |                                                                  |
| BusinessProfileLocation         |  Localização do perfil do parceiro.                            |
| SolutionProfile            |  Perfil de solução do parceiro. |

## <a name="tag"></a>Etiqueta

Descreve a etiqueta.

| Propriedade                  | Tipo                                                  | Descrição                                                   |
|---------------------------|-------------------------------------------------------|---------------------------------------------------------------|
| Id                        | string                                                | A identificação desta etiqueta.                                          |

### <a name="products"></a>Produtos

| Valor        |
|-----------------|
|Azure|
|EnterpriseMobilityAndSecurity|
|Troca|
|Empresas de Desenvolvimento|
|Dinâmica365Business|
|Dinâmica365Enterprise|
|DynamicsAX,GP,NAV,SL|
|Microsoft365|
|Office|
|Power BI|
|Project|
|SharePoint|
|SkypeForBusiness|
|Surface|
|SurfaceHub|
|SQL|
|Teams|
|Visio|
|Windows|
|Yammer|

### <a name="services"></a>Serviços

| Valor        |
|-----------------|
|ConsultoriaAndProfessional|
|Solution Personalizado (ISV)|
|ImplantaçãoOrmigação|
|Hardware|
|Integração|
|IPServices (ISV)|
|Aprendizagem ECertificação|
|Licenciamento|
|Serviços Geridos|
|Serviços de Projeto|

### <a name="industries"></a>Indústrias

| Valor        |
|-----------------|
|Agricultura, Silvicultura, Pesca &|
|Comunicações & Media|
|Education|
|Serviços Financeiros|
|Administração Pública|
|Cuidados de saúde|
|Hospitalidade|
|Fabrico|
|Utilitários & de Energia|
|Segurança Pública e Segurança Nacional|
|Retalho & Bens de Consumo|
|Serviços|
|Transporte & de viagem|
|Distribuição de & por grosso|

### <a name="solutions"></a>Soluções

| Valor        |
|-----------------|
|Avançados Analytics|
|Integração de Aplicações|
|Inteligência Artificial|
|AzureSecurityOperaçãoManagement|
    |AzureStack|
    |BackdisasterRecovery|
    |BigData|
    |Blockchain|
    |Chatbot|
    |CloudDataBaseMigration|
    |CloudMigration|
    |CloudVoice|
    |CognitiveServices|
    |Competitividade Da Imigração deDatabase|
    |Contentores|
    |ArmazémDeDados|
    |Base de dadosLinux|
    |Desenvolvimentos eTeste|
    |DevOps|
    |DigitalMedia|
    |Dynamics365forCustomerService|
    |Dynamics365forFieldService|
    |Dinâmicas365forFinanceOperations|
    |Dinâmica365forRetail|
    |Dinâmicas365forSales|
    |Dinâmica365forTalent|
    |DynamicsonAzure|
    |EnterpriseBusinessIntelligence|
    |Jogos|
    |HighPerformanceComputing|
    |HíbridoStorage|
    |Identidade e Gestão de Identidades|
    |Gestão de Informação|
    |InternetofThings|
    |MachineLearning|
    |Micro-aplicações de serviços|
    |Aplicações móveis|
    |MySQLPostgresMigrationtoAzure|
    |Redes|
    |Não-imigração|
    |RedhatonAzure|
    |RegulaçãoComplianceGDPR|
    |SAPonAzure|
    |ServerlessComputing|
    |SharepointonAzure|
    |SQLServerUpgrade|
    |Proteção contra ameaças|
    |WebDevelopment|

### <a name="customer-size"></a>Tamanho do cliente

| Valor        |
|-----------------|
|    1to50empres|
|    51to500empres|
|    Mais de 500 employees|
|    1to9empres|
|    10to50empres|
|    51to250empres|
|    251to1000employees|
|    1001to5000empresomes|
|    5001to100000empreso|
|    10001a200000empresoia|
|    Moreth20000employees|
