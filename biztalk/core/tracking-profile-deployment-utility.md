---
title: "Utilitaire de déploiement de profil de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d631b7c-a40f-4cee-88a4-3d932ab7fde0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 672879df2c1c5217d8a9710dad000609dd95d0c2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="tracking-profile-deployment-utility"></a>Utilitaire de déploiement de profil de suivi
Les développeurs utilisent l'utilitaire bttdeploy pour appliquer des modèles de suivi à l'infrastructure BAM et les supprimer. En pratique, l'utilisation de l'utilitaire bttdeploy revient à cliquer sur l'option de menu Appliquer le modèle de suivi de l'Éditeur de modèle de suivi (TPE).  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
 **Utilisation**  
  
 **nom de fichier BttDeploy.exe [options]**  
  
|Option| Description|  
|------------|-----------------|  
|/h ou /?|Facultatif : Affiche la syntaxe pour bttdeploy.|  
|/mgdb \<nom du serveur [, port]\>\\< nom de la base de données\>|Facultatif : Spécifie que le serveur d’administration, le port et le nom de la base de données à laquelle appliquer le profil. **Remarque :** lorsque vous utilisez ce paramètre, le port est facultatif.|  
|/remove|Facultatif : Spécifie que le modèle de suivi à supprimer de la base de données BAM.|  
|filename|Nom du fichier de modèle de suivi à appliquer ou à supprimer.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)   
 [Comment supprimer des profils de suivi orphelins](../core/how-to-remove-orphaned-tracking-profiles.md)