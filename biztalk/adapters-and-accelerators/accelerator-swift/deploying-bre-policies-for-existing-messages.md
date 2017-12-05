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
ms.openlocfilehash: 4cd094feabe1ba23a6a73c89aae3a1042b8f7fc9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploying-bre-policies-for-existing-messages"></a>Déploiement de stratégies BRE pour les Messages existants
**Pour déployer des règles métier connexes :**  
  
1.  Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **l’utilitaire de déploiement BRE**.  
  
2.  Dans l’utilitaire de déploiement BRE, cliquez sur **Parcourir**.  
  
3.  Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez **SWIFT MX schéma**, puis cliquez sur **OK**.  
  
4.  Cliquez sur **déployer**.  
  
     Selon les schémas déployés avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE. Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant : « déploiement s’est terminée. Afficher le fichier journal ou l’éditeur des règles d’entreprise pour plus d’informations. »  
  
5.  Fermez la boîte de dialogue Utilitaire de déploiement BRE SWIFT.  
  
6.  Dans l’Explorateur Windows, accédez à  *\<lecteur\>*: \Documents and Settings\All Users\Application Data pour vérifier que le fichier journal BREDeploymentLog.txt figure dans le dossier.  
  
7.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **services.msc**, puis cliquez sur **OK**. Dans la fenêtre Services (Local), cliquez sur **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.