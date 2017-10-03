---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91f818dd-11fa-4ea4-b904-e8e00b3e49b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 545e095624c30b4611c74dcfbdead13d685164ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-http-adapter"></a>Diagnostic des problèmes relatifs à l'adaptateur HTTP
Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur HTTP.  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a>Recherche des erreurs dans les fichiers journaux IIS et HTTPERR du serveur IIS  
  
-   Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur HTTP. Ces fichiers journaux se trouvent par défaut dans le répertoire suivant (Windows Server) :  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.  
  
     Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :  
  
     *%Windir%\\*system32\LogFiles\HTTPERR\  
  
    > [!NOTE]
    >  Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateurs.  
  
### <a name="isolate-problems-with-the-http-send-adapter-by-posting-to-the-destination-url-with-a-client-that-uses-the-systemnethttpwebrequest-class"></a>Isolez le problème relatif à l'adaptateur d'envoi HTTP en le publiant sur l'URL de destination à l'aide d'un client qui utilise la classe System.Net.HttpWebRequest.  
  
1.  Si l'adaptateur d'envoi HTTP génère des erreurs lors de la publication sur l'URL de destination, créez un client qui utilise les classes System.Net.HttpWebRequest et HttpWebResponse pour effectuer la publication sur l'URL de destination. Cette méthode permet de déterminer si le problème est spécifique à l'adaptateur d'envoi HTTP ou s'il concerne la publication sur l'URL de destination en général.  
  
2.  Pour plus d’informations sur la création d’un client qui utilise les classes System.Net.HttpWebRequest et HttpWebResponse, consultez [comment utiliser les classes System.Net nouvelles pour créer un client HTTP](http://go.microsoft.com/fwlink/?LinkId=66987).  
  
## <a name="see-also"></a>Voir aussi  
 [Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [Dépannage de l’adaptateur HTTP](../core/troubleshooting-the-http-adapter.md)