---
title: "Résolution des problèmes de non - WCF ligne des adaptateurs pour les entreprises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d5f7877-656f-406e-9edb-d6b9a0705b02
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba36ed8a8efb62e2eb8e885791c3c28012dcc49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-non-wcf-line-of-business-adapters"></a>Dépannage des adaptateurs LOB (Line of Business) non-WCF
## <a name="failed-to-retrieve-error"></a>Erreur « Échec d’extraction »  
 Lors de l’utilisation d’un adaptateur LOB (Line of Business) non-WCF, les erreurs suivantes peuvent se produire :  
  
-   Échec d’extraction du système  
  
-   L’agent de navigation : erreur interceptée dans le constructeur. L’ordinateur cible a expressément refusé la connexion.  
  
-   Agent d’exécution : erreur interceptée dans le constructeur. L’ordinateur cible a expressément refusé la connexion.  
  
### <a name="cause"></a>Cause  
 Les adaptateurs LOB utilisent l’accès à distance .NET. Si l’activation de l’accès à distance .NET prend plus de temps que prévu, l’adaptateur risque de renvoyer ces erreurs.  
  
### <a name="resolution"></a>Résolution  
 Créer le **StartAgentSleep** clé de Registre et augmentez la valeur de délai d’attente :  
  
1.  Ouvrez le Registre et accédez à *HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*.  
  
2.  Créez une valeur DWORD avec les propriétés suivantes :  
  
     Nom : StartAgentSleep  
  
     Base : décimal  
  
     Données de la valeur : 1000  
  
 Les données de la valeur sont mesurées en millisecondes (ms). 1 000 ms équivalent à 1 seconde.  
  
 Dans certains systèmes, une seconde n’est pas une valeur suffisante. Augmentez la valeur et testez le résultat pour déterminer le délai d’attente approprié nécessaire.  
  
> [!IMPORTANT]
>  Ajout de la **StartAgentSleep** impacts de clé de Registre **tous les** les adaptateurs WCF LOB.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage des adaptateurs BizTalk Server](../core/troubleshooting-biztalk-server-adapters.md)