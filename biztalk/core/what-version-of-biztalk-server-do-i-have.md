---
title: "Quelle version de BizTalk Server possédez-vous ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb651202-f682-4e5f-8a79-221877af20a7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce5508a3b7c78e52fe5fcbef40e351dce58f2816
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-version-of-biztalk-server-do-i-have"></a>Quelle version de BizTalk Server possédez-vous ?
Vous pouvez exécuter différentes versions et éditions de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette rubrique vous montre comment déterminer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] informations sur l’installation, y compris le chemin d’installation, Édition et numéro de version.  
  
## <a name="use-the-registry"></a>Utiliser le Registre
  
1.  Sélectionnez **Démarrer**, type `regedt32`, puis ouvrez-le.  
  
2.  Développez **HKEY_LOCAL_MACHINE**, développez **logiciel**, développez **Microsoft**, développez **BizTalk Server**, puis sélectionnez **3.0**.  
  
3.  Le volet droit affiche les informations d’installation, à savoir :  
  
    |Sous-clé| Description|  
    |--------------|-----------------|  
    |**Chemin d’installation**|Répertorie le chemin d’installation sous lequel vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
    |**ProductEdition**|Répertorie l’édition, ainsi que les informations suivantes :<br /><br /> -Développeur<br />-Branche<br />-Standard<br />-Entreprise|  
    |**Version de produit**|Répertorie la version de base. Pour la version de produit spécifique, y compris les service packs et mises à jour cumulatives, consultez [Versions BizTalk](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).|  

## <a name="use-the-control-panel"></a>Utilisez le panneau de configuration

1.  Sélectionnez **Démarrer**, type `Programs and Features`, puis ouvrez-le.  

2. Dans la liste, sélectionnez **Microsoft BizTalk Server**. La version et l’édition sont répertoriées.

Consultez [Versions BizTalk](http://social.technet.microsoft.com/wiki/contents/articles/7915.biztalk-versions.aspx).
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../core/getting-started-with-biztalk-server.md)