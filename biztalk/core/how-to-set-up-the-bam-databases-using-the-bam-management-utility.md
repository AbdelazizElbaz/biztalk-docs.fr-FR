---
title: "Procédure : configurer des bases de données BAM à l’aide de l’utilitaire de gestion BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801338f4-b363-4f8e-b248-9c628065ded2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8cee3564b90b730334d2d891edd2e9abc221a367
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-set-up-the-bam-databases-using-the-bam-management-utility"></a>Configuration des bases de données BAM à l'aide de l'utilitaire de gestion de l'analyse BAM [BTS06]
Pour configurer les bases de données BAM, les administrateurs utilisent généralement l'utilitaire de configuration BizTalk Server. L'utilitaire de gestion de l'analyse BAM (bm.exe) constitue toutefois un autre moyen de configurer les bases de données BAM.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration requise pour exécuter la procédure décrite dans cette rubrique est la suivante :  
  
-   Vous devez disposer des autorisations d'administrateur sur le serveur SQL hébergeant les bases de données BAMPrimaryImport, BAMStarSchema et BAMArchive.  
  
-   Pour configurer les bases de données des services de notification SQL, vous devez disposer de l'autorisation d'administrateur et être membre du groupe des administrateurs locaux et de tout autre groupe d'administrateur ayant été configuré, par exemple le groupe des administrateurs BTS.  
  
-   Vous devez avoir un fichier de configuration BAM contenant des données XML à partir desquelles configurer les bases de données.  
  
### <a name="to-set-up-the-bam-databases-using-the-bam-management-utility"></a>Pour configurer les bases de données BAM à l'aide de l'utilitaire de gestion de l'analyse BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.  
  
3.  Tapez la commande suivante à l’invite de ligne de commande : **bm le programme d’installation-bases de données - ConfigFile :\<fichier de configuration\>**, où \< *fichier de configuration* \>est remplacé par le nom de votre fichier de configuration BAM. Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)