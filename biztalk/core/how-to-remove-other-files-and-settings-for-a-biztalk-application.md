---
title: "Comment supprimer les autres fichiers et paramètres d’une Application BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [applications], deleting settings
- managing [applications], deleting files
- undeploying, settings
- applications, undeploying
- undeploying, files
ms.assetid: b947831a-c988-435c-92ec-45f3fd6967de
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e9ad98e0f0fc1e65281a1d8195be4f4a708d004f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-other-files-and-settings-for-a-biztalk-application"></a>Suppression d'autres fichiers et paramètres pour une application BizTalk
Cette rubrique explique comment supprimer des fichiers et des paramètres d’une application BizTalk qui ne peuvent pas être supprimés lorsque vous désinstallez l’application (qui est décrite dans [comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)). Par exemple, les certificats, les entrées de registre COM et COM+, ainsi que les fichiers COM ne sont pas supprimés sauf si l'application incluait un script de post-traitement qui les a supprimés lors de la désinstallation.  
  
> [!CAUTION]
>  Avant de supprimer tout élément partagé, vérifiez qu'aucune autre application ne l'utilise, sinon celle-ci ne fonctionnera pas correctement.  
  
> [!NOTE]
>  Nous vous recommandons d'automatiser cette suppression à l'aide d'un script de post-traitement. Pour plus d’informations, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
-   **Supprimer les certificats.** Il existe deux façons de supprimer des certificats du magasin de certificats : à l'aide de l'outil de ligne de commande Certificate Manager (certmgr.exe) ou du composant logiciel enfichable Certificats. Certmgr.exe est installé avec le Kit de développement .NET SDK, qui est l'un des composants requis pour l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez l'exécuter manuellement ou à partir d'un script de post-traitement. Pour plus d’informations sur l’utilisation de certmgr.exe, voir [outil Certificate Manager (certmgr.exe)](http://go.microsoft.com/fwlink/?LinkId=56198) sur le site Web de Microsoft.  
  
     Le composant logiciel enfichable Certificats est inclus à la fois dans Windows Server 2008 et Windows Vista. Pour supprimer un certificat, ouvrez le composant affichable selon la procédure décrite dans la rubrique « Démarrage du composant logiciel enfichable Certificats » de l'aide de votre système d'exploitation, puis supprimez le certificat selon la procédure décrite dans la rubrique « Supprimer un certificat » de l'aide du composant Certificats.  
  
-   **Supprimer des assemblys à partir du Registre Windows.** Pour supprimer des assemblys .NET et BizTalk du registre Windows, utilisez regsvcs ou regasm inclus avec le Kit de développement .NET SDK, l'un des composants requis de l'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [.NET Services Installation Tool (Regsvcs.exe)](http://go.microsoft.com/fwlink/?LinkId=56199) et [outil Assembly Registration Tool (Regasm.exe)](http://go.microsoft.com/fwlink/?LinkId=56200) sur le site Web de Microsoft.  
  
-   **Supprimer des composants COM à partir du Registre Windows.** Pour supprimer des composants COM du Registre Windows, utilisez regsvr32. Pour obtenir des informations de référence, reportez-vous à la rubrique "Regsvr32" dans l'aide de votre système d'exploitation. Cet outil est inclus à la fois dans Windows Server 2008 et Windows Vista Professionnel.  
  
-   **Désinstaller des assemblys du global assembly cache (GAC).** Les assemblys ne sont pas désinstallés automatiquement du GAC. Vous pouvez désinstaller un assembly du GAC manuellement ou à l'aide d'un script. Pour plus d’informations, consultez [comment désinstaller un Assembly du GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour supprimer les fichiers et paramètres décrits dans cette rubrique, vous devez être connecté avec un compte disposant d'autorisations en écriture sur le registre Windows, le GAC ou le magasin de certificats, selon les éléments à supprimer. Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation du déploiement des Applications BizTalk](../core/undeploying-biztalk-applications.md)   
 [Comment désinstaller une Application BizTalk](../core/how-to-uninstall-a-biztalk-application.md)