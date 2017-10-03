---
title: "Le serveur Web sur le port d’hôte introuvable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c253fd5e-b815-4697-a06d-67af65a35589
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dce09ce00a169ad14bbc8ae2ab28fe70c039c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="web-server-on-host-port-not-found"></a>Serveur Web introuvable sur le port de l'hôte
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|ID d'événement|0|  
|Source de l'événement|0|  
|Composant|0|  
|Nom symbolique|0|  
|Texte du message|Serveur Web sur l’hôte « {0} » {{1} de port introuvable|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le service World Wide Web n'est pas en cours d'exécution.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La procédure suivante permet de démarrer le service World Wide Web.  
  
#### <a name="to-start-the-world-wide-web-service"></a>Pour démarrer le service World Wide Web  
  
1.  Cliquez sur **Démarrer**, cliquez sur **le panneau de configuration**, double-cliquez sur **outils d’administration**, double-cliquez sur **Services.**  
  
2.  Dans la colonne nom, recherchez **World Wide Web Publishing**. Vérifiez que l’état est **démarré**.  
  
3.  Retour à la **outils d’administration** fenêtre. Double-cliquez sur **Internet Information Services**.  
  
4.  Développez la zone du dossier et recherchez le site Web.  
  
5.  Vérifiez que l’état est **démarré**.