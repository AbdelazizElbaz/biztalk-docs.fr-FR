---
title: "Comment mettre à jour la Configuration BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 714a834e-1879-4019-9b54-e511705bd67a
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee5958120e364cc0c2661ead6100bd2ba5502226
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a>Mise à jour de la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM
Les administrateurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour mettre à jour une installation BAM existante.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer des autorisations d'administrateur sur la base de données BAM mise à jour.  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a>Pour mettre à jour la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm update-config - FileName :\<le fichier de configuration >**, où \< *fichier de configuration*> est remplacé par le nom de votre analyse BAM fichier de configuration. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)