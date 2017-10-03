---
title: "Comment diagnostiquer les problèmes avec Windows SharePoint Services adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55c29569-3814-43a7-93f8-a39c3464a831
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67aa43628e8db4384a411fd1cc4696b7955b3752
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-windows-sharepoint-services-adapter"></a>Comment faire pour diagnostiquer des problèmes avec l’adaptateur Windows SharePoint Services
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur Windows Sharepoint Services.  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a>Recherche des erreurs dans les fichiers journaux IIS et HTTPERR du serveur IIS  
  
-   Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur Windows Sharepoint Services. Les fichiers journaux IIS d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.  
  
-   Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\HTTPERR\  
  
    > [!NOTE]
    >  Le fichier journal HTTPERR est uniquement disponible sur les ordinateurs [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Résolution des problèmes de l’adaptateur Windows SharePoint Services](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)