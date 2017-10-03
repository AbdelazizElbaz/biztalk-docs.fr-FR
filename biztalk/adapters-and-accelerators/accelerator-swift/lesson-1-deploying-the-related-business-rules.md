---
title: "Leçon 1 : Déploiement des règles métier connexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, deploying
- deploying, business rules
ms.assetid: f8f5b103-4b66-4836-8165-99692574961a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e52712730546847a821d53a5f8013fff4d553501
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-deploying-the-related-business-rules"></a>Leçon 1 : Déploiement des règles métier connexes
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] inclut un programme dans A4SWIFT Software Development Kit (SDK) appelé l’utilitaire de déploiement du moteur de règles d’entreprise (BRE). Dans cette leçon, vous utilisez cet utilitaire pour inspecter un assembly pour les schémas déployés, déterminer les règles requises et déployer les stratégies pour chaque schéma et les vocabulaires nécessaires.  
  
 Vous pouvez également déployer des règles en utilisant les Guides de mise en production normes SWIFT (SRG) pour identifier les règles nécessaires, puis utiliser l’outil Éditeur des règles d’entreprise pour déployer les stratégies et vocabulaires.  
  
### <a name="to-deploy-the-related-business-rules"></a>Pour déployer les règles d’entreprise connexes  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator pour SWIFT**, puis cliquez sur **BRE Utilitaire de déploiement**.  
  
2.  Dans la boîte de dialogue Utilitaire de déploiement du moteur BRE, cliquez sur **Parcourir**.  
  
3.  Dans la boîte de dialogue .NET Global Assembly Cache, sélectionnez **SWIFTSchemas**, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  SWIFTSchemas fait référence à l’assembly déployé précédemment.  
  
4.  Cliquez sur **déployer**.  
  
     Selon les schémas que vous avez déployé avec cet assembly, l’utilitaire de déploiement identifie les règles associées et les publie pour une utilisation avec le moteur BRE. Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant :  
  
     **Fin du déploiement. Pour plus d’informations, consulter le fichier journal ou l’éditeur des règles d’entreprise.**  
  
5.  Fermez la boîte de dialogue Utilitaire de déploiement BRE SWIFT.  
  
6.  Dans l’Explorateur Windows, accédez à \< *lecteur*> : \Documents and Settings\All Users\Application Data pour confirmer que le fichier journal **BREDeploymentLog.txt** apparaît dans le dossier.  
  
    > [!NOTE]
    >  Vous pouvez ouvrir le fichier journal à l’aide d’un éditeur de texte pour confirmer chacune des étapes de déploiement.  
  
7.  Redémarrez le Service de mise à jour de moteur de règle. En cliquant sur **Démarrer**, puis sur **exécuter**, saisie **services.msc**, puis en cliquant sur **OK**. Dans le **Services (Local)** fenêtre, avec le bouton droit **Service de mise à jour du moteur de règles**, puis cliquez sur **redémarrer**.  
  
 Passez à [leçon 2 : confirmer le déploiement à l’aide de l’outil de Composer de règle métier](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md).