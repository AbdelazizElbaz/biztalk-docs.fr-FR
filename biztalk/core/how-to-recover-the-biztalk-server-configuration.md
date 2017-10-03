---
title: "Comment récupérer la Configuration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1d39e50-4296-49c7-bd1e-63b1325af168
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9935c2c565d78d0bc102d4aef86959c2a9066e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-the-biztalk-server-configuration"></a>Récupération de la configuration de BizTalk Server
Dans le cadre de la restauration de votre serveur BizTalk, vous devez également importer le fichier de configuration créé lors de l'installation de BizTalk Server.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs.  
  
### <a name="to-recover-the-biztalk-server-configuration"></a>Pour récupérer la configuration de BizTalk Server  
  
1.  À l'aide du Bloc-notes, modifiez le fichier de configuration de BizTalk Server que vous aviez préalablement sauvegardé, puis entrez les mots de passe pour les comptes d'utilisateur de tous les services BizTalk Server.  
  
2.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
3.  Dans **Configuration de Microsoft BizTalk Server**, cliquez sur **importer la Configuration**.  
  
     Vérifiez qu'aucune icône d'invalidation ne s'affiche devant un composant. Si l'un d'entre eux rencontre des erreurs de configuration, vous devez les corriger dès maintenant.  
  
4.  Cliquez sur **Appliquer la configuration**.  
  
     Après avoir configuré tous les composants de BizTalk Server, fermez la fenêtre de configuration.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [Comment faire pour sauvegarder la Configuration de BizTalk Server](../core/how-to-back-up-the-biztalk-server-configuration.md)