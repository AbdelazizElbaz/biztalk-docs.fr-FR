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
ms.openlocfilehash: 3c4d261069b83741413e255a3f8bacd6dd9260d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
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
|/mgdb \<nom du serveur [, port] >\\< nom de la base de données\>|Facultatif : Spécifie que le serveur d’administration, le port et le nom de la base de données à laquelle appliquer le profil. **Remarque :** lorsque vous utilisez ce paramètre, le port est facultatif.|  
|/remove|Facultatif : Spécifie que le modèle de suivi à supprimer de la base de données BAM.|  
|filename|Nom du fichier de modèle de suivi à appliquer ou à supprimer.|  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)   
 [Comment supprimer des profils de suivi orphelins](../core/how-to-remove-orphaned-tracking-profiles.md)