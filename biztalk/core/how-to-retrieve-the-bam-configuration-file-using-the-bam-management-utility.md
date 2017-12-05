---
title: "Comment récupérer le fichier de Configuration BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67ce5e0c-467a-486c-8eec-217a2a26d7b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef0f4802aa44a042f39adbdc9f169b11a16796d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a>Extraction du fichier de configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM
Les administrateurs et les développeurs peuvent utiliser l'utilitaire de gestion de l'analyse BAM pour récupérer la configuration existante de l'infrastructure BAM. La configuration récupérée peut être utilisée pour migrer une installation BAM sur un nouveau serveur. Elle peut également être modifiée et utilisée pour mettre à jour une installation BAM existante.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Bases de données BAM configurées  
  
-   Autorisations de lecture dans la base de données d'importation principale BAM  
  
### <a name="to-retrieve-the-bam-configuration-file-using-the-bam-management-utility"></a>Pour extraire le fichier de configuration BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm get-config - FileName :\<fichier de sortie\>**, où \< *fichier de sortie* \> est remplacé par le nom de votre fichier de configuration BAM. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)