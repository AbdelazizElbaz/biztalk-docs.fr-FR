---
title: "Déploiement de stratégies BRE pour les Messages existants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 585c903d-ee44-4e92-8798-febb176367e3
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b03f6f3319e90d4782e1e9e5fd7e2a7e2a27b527
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-bre-policies-for-existing-messages"></a>Déploiement de stratégies BRE pour les Messages existants
**Pour déployer des règles métier connexes :**  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **l’utilitaire de déploiement BRE**.  
  
2.  Dans l’utilitaire de déploiement BRE, cliquez sur **Parcourir**.  
  
3.  Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez **SWIFT MX schéma**, puis cliquez sur **OK**.  
  
4.  Cliquez sur **déployer**.  
  
     Selon les schémas déployés avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE. Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant : « déploiement s’est terminée. Afficher le fichier journal ou l’éditeur des règles d’entreprise pour plus d’informations. »  
  
5.  Fermez la boîte de dialogue Utilitaire de déploiement BRE SWIFT.  
  
6.  Dans l’Explorateur Windows, accédez à  *\<lecteur >*: \Documents and Settings\All Users\Application Data pour vérifier que le fichier journal BREDeploymentLog.txt figure dans le dossier.  
  
7.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **services.msc**, puis cliquez sur **OK**. Dans la fenêtre Services (Local), cliquez sur **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.