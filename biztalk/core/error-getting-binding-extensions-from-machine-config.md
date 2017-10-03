---
title: "Erreur d’obtention des extensions de liaison à partir de machine.config | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8dfdedb58e4372caed38c7c272cbaaf65fefbcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-getting-binding-extensions-from-machineconfig"></a>Erreur lors de l'obtention des extensions de liaison à partir de machine.config.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Erreur lors de l'obtention des extensions de liaison à partir de machine.config.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lorsque la configuration de liaison d'un emplacement de réception ou d'un port d'envoi possède une extension de liaison mais que celle-ci n'est pas définie dans le fichier machine.config. Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Définissez l'extension de liaison utilisée dans l'emplacement de réception ou le port d'envoi du fichier machine.config. Par ailleurs, pour qu'un comportement personnalisé ou un élément de liaison fonctionne avec l'adaptateur WCF-Custom, procédez comme suit :  
  
1.  Copiez l'assembly dans le GAC (Global Assembly Cache).  
  
2.  Modifiez votre fichier machine.config (trouvé dans **%FrameworkDir%\v4.0.30319\CONFIG**).  
  
    1.  Charge le comportement de votre DLL à l’intérieur de l’éditeur de Configuration de Service (**svcConfigEditor.exe**).  
  
    2.  Enregistrer la configuration pour un **app.config** fichier  
  
    3.  Copiez et collez le **system.servicemodel** section des extensions dans une section similaire dans le fichier machine.config. Si **system.servicemodel** section n’est pas présente dans le fichier, vous devez en créer un. Vous trouverez ci-dessous un exemple de la section de configuration d'un fichier machine.config :  
  
        ```  
          <system.serviceModel>  
            <extensions>  
              <behaviorExtensions>  
                <add name="BizTalkWcfContractNamespaceTestServiceBehaviorExtension" type="ASB.BizTalk.Samples.BizTalkWcfContractNamespaceTestServiceBehaviorExtension, CustomBizTalkWcfBehaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=7631521c07cf34b4" />  
              </behaviorExtensions>  
            </extensions>  
          </system.serviceModel>  
        ```  
  
> [!NOTE]
>  Le code ci-dessus peut également être ajouté à l’onglet Extensions WCF. Si l’extension doit être du côté réception, consultez le  **\<nom d’hôte > boîte de dialogue Propriétés, les Extensions WCF** onglet (WCF-Custom ou Gestionnaire de réception de l’adaptateur WCF-CustomIsolated) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. Si l’extension doit se trouver du côté envoi, consultez  **\<nom d’hôte > boîte de dialogue Propriétés, les Extensions WCF** onglet (Gestionnaire d’envoi WCF-Custom adaptateur) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 3. Fermez et rouvrez la console Administration. L'adaptateur WCF-Custom doit désormais inclure le comportement personnalisé. Une fois activé, le port ne doit pas être désactivé.