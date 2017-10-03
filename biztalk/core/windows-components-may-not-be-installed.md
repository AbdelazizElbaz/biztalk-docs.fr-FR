---
title: "Les composants de Windows ne peuvent pas être installés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc78ac0a-ee21-4633-afb3-1357efd29903
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506f9c310a75c9f65564e4feb047157731bafa66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="windows-components-may-not-be-installed"></a>Les composants Windows ne sont peut-être pas installés
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Le composant Windows suivant n’est peut-être pas être installé : serveur d’applications -&gt; Internet Information Services (IIS) -&gt; fichiers communs.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit lors d'une tentative de publication si Internet Information Services n'est pas installé sur l'ordinateur local.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour Windows 7 et Windows Vista SP2, installez IIS sur l'ordinateur local et configurez IIS comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **programmes**.  
  
2.  Cliquez sur **activer des fonctionnalités Windows et**. L'Assistant Fonctionnalités Windows s'affiche.  
  
3.  Pour ajouter le composant IIS, activez-le.  
  
 Pour [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)] et [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], installez IIS sur l'ordinateur local et configurez IIS comme suit :  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, puis cliquez sur **outils d’administration**.  
  
2.  Cliquez sur **le Gestionnaire de serveur**. La fenêtre Gestionnaire de serveur s'affiche.  
  
3.  Cliquez sur **ajouter des rôles**, Assistant Ajout de rôles s’affiche.  
  
4.  Pour ajouter, sélectionnez le composant IIS.