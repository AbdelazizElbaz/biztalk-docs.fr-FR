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
ms.openlocfilehash: b08209d3b3a1555bbc674e469ea9f8a4b1f81a9d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-the-bam-configuration-using-the-bam-management-utility"></a>Mise à jour de la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM
Les administrateurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour mettre à jour une installation BAM existante.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer des autorisations d'administrateur sur la base de données BAM mise à jour.  
  
### <a name="to-update-the-bam-configuration-using-the-bam-management-utility"></a>Pour mettre à jour la configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm update-config - FileName :\<le fichier de configuration\>**, où \< *fichier de configuration* \> est remplacé par le nom de votre fichier de configuration BAM. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)