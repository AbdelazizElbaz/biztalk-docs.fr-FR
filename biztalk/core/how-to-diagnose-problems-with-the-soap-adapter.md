---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c93333-cb32-49bc-a1c4-9d726ab41850
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db1d495eb301f93100a6ac9a4e50c8f1c57e5f5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-soap-adapter"></a>Diagnostic des problèmes relatifs à l'adaptateur SOAP
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur SOAP.  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a>Vérifiez le journal d’IIS et HTTPERR du serveur IIS pour les erreurs  
  
-   Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur SOAP. Les fichiers journaux IIS d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.  
  
     Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\HTTPERR\  
  
    > [!NOTE]
    >  Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Dépannage de l’adaptateur SOAP](../core/troubleshooting-the-soap-adapter.md)