---
title: Comment faire pour sauvegarder la Configuration de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14f89050-c204-4d44-a875-299e690489ef
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad54aba8f8f49adeb8534bdbe28add15f0fe9638
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-biztalk-server-configuration"></a>Sauvegarde de la configuration de BizTalk Server
Dans le cadre de la sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez sauvegarder les paramètres de configuration associés à l'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fait de disposer d'une copie des fichiers de configuration originaux simplifie grandement le processus de restauration en cas de défaillance matérielle impliquant le remplacement de l'ordinateur.  
  
 Les paramètres de configuration de chaque ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont stockés dans un fichier XML créé par le gestionnaire de configuration de BizTalk Server. Chaque fois que vous modifiez la configuration de vos serveurs BizTalk, vous devez exporter le fichier de configuration mis à jour vers votre emplacement de sauvegarde. Ainsi, le fichier de configuration reste disponible si vous devez remplacer votre serveur BizTalk.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs de BizTalk Server.  
  
### <a name="to-back-up-the-biztalk-server-configuration"></a>Pour sauvegarder la configuration de BizTalk Server  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft BizTalk Server**, puis cliquez sur **Configuration de BizTalk Server**.  
  
2.  Dans **Configuration de Microsoft BizTalk Server**, cliquez sur **exporter la Configuration**.  
  
3.  Dans le **Enregistrer sous** boîte de dialogue, accédez à l’emplacement où vous stockez vos sauvegardes.  
  
4.  Dans le **nom de fichier** zone, tapez un nom pour le fichier de configuration, puis cliquez sur **enregistrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde d’un ordinateur exécutant BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md)   
 [Comment récupérer la Configuration de BizTalk Server](../core/how-to-recover-the-biztalk-server-configuration.md)