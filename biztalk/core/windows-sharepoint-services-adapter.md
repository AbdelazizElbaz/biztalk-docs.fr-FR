---
title: Adaptateur de Windows SharePoint Services | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows SharePoint Services adapters
ms.assetid: cbfc9bf3-912d-4849-ba8c-07a116888bbd
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a6f1365b11ce93717223ec35e395165e8d0e551
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-sharepoint-services-adapter"></a>Adaptateur Windows SharePoint Services
L'adaptateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour Microsoft Windows SharePoint Services fournit une intégration étroite de BizTalk Server avec Windows SharePoint Services et Microsoft Office. L'utilisation de l'adaptateur Windows SharePoint Services au sein de votre solution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] vous permet de bénéficier des fonctionnalités suivantes :  
  
-   Accès aisé aux messages entrants et sortants via Windows SharePoint Services.  
  
-   Capacité à modifier les messages XML à l’aide des applications Office telles que Microsoft Office InfoPath.  
  
-   Transformation bidirectionnelle des messages XML vers et depuis InfoPath.  
  
 L’adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] possède les composants suivants :  
  
|||  
|-|-|  
|Adaptateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] CSOM|Utilise le Modèle objet côté client (CSOM) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)]. L’adaptateur est installé lors de l’installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Aucune étape d’installation supplémentaire n’est nécessaire.<br /><br /> Le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation ***automatiquement*** installe le SharePoint Client composant redistribuable du modèle, qui est également disponible à l’adresse [http://go.microsoft.com/fwlink/p/?LinkId=263482](http://go.microsoft.com/fwlink/p/?LinkId=263482).|  
|Service Web [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] SSOM|**Option déconseillée**. Utilise le modèle SSOM (Service-Side Object Model) [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)].<br /><br /> Le service web est installé sur l’ordinateur [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)], qui peut se trouver sur le même ordinateur que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou sur un ordinateur différent.<br /><br /> Pour installer le service web, exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation sur le [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] ordinateur et recherchez **adaptateur Windows SharePoint Services**.|  
  
 [Annexe b : installer l’adaptateur SharePoint de Microsoft](../install-and-config-guides/appendix-b-install-the-microsoft-sharepoint-adapter.md) fournit des informations sur la [!INCLUDE[btsSharePointSvcsNoVersion](../includes/btssharepointsvcsnoversion-md.md)] installation.  
  
> [!NOTE]
>  L'authentification fédérée n'est pas prise en charge pour l'instant. Seule l'authentification par nom d'utilisateur et mot de passe est prise en charge.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [CSOM : L’adaptateur SharePoint Services](../core/csom-sharepoint-services-adapter.md)  
  
-   [SSOM : Le Service Web adaptateur SharePoint Services](../core/ssom-sharepoint-services-adapter-web-service.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des adaptateurs](../core/using-adapters.md)   
 [Développement d’Applications de BizTalk Server](../core/developing-biztalk-server-applications.md)