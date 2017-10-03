---
title: "Utilitaire de déploiement BRE | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BRE Deployment utility
- deploying, BRE Deployment utility
ms.assetid: 5b04592c-ea1e-4ded-8ca4-dcd051d6375e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f40a75d898369cfc730ba5cb4f25c199e1333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bre-deployment-utility"></a>Utilitaire de déploiement BRE
Vous pouvez utiliser l’utilitaire de déploiement du moteur BRE à publier et déployer les vocabulaires de moteur de règles d’entreprise (BRE) et les stratégies requises pour un schéma SWIFT. Publication et le déploiement de ces stratégies et les vocabulaires sont requis pour activer la validation BRE pour le type de message.  
  
 Vous pouvez également déployer des règles d’entreprise en utilisant les Guides de mise en production de normes de SWIFT (SRGs) pour identifier les règles requises, puis en utilisant la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outil Éditeur des règles d’entreprise pour déployer les stratégies et vocabulaires. Toutefois, il est beaucoup plus facile d’à l’aide de l’utilitaire de déploiement du moteur BRE.  
  
 L’utilitaire de déploiement du moteur BRE effectue les opérations suivantes :  
  
-   Examine l’assembly déployé que vous spécifiez et détermine les schémas de message que vous avez déployé l’assembly.  
  
-   Publie le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_CodeLists.xml et [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Functions.xml les vocabulaires requis pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] le traitement des règles d’entreprise.  
  
-   Publie et déploie les SWIFT base stratégies (stratégie de référence, la stratégie d’identificateur de tiers et les stratégies de règles de réseau) associées avec les schémas de message.  
  
-   Publie et déploie la stratégie principal et la stratégie de validation associée à chaque schéma de message.  
  
-   Génère un fichier journal qui indique toutes les étapes nécessaires. Ce fichier est BREDeploymentLog.txt dans les \< *lecteur*> : \Documents and Settings\All Users\Application et recommencez.  
  
    > [!NOTE]
    >  L’utilitaire de déploiement du moteur BRE ne déploie pas les stratégies de Master BIC et Validation BIC. Vous devez déployer à l’aide de l’Assistant Déploiement du moteur de règles.  
  
    > [!NOTE]
    >  Si vous avez installé [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] dans un répertoire par défaut (autre que C:\Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]), ou que vous travaillez sur un ordinateur 64 bits, l’utilitaire de déploiement du moteur BRE ne fonctionnera pas correctement tant que vous modifiez les chemins d’accès dans le Fichier bredeployment.exe.config modifié. Ce fichier de configuration se trouve dans le \< *lecteur*> : \Program Files\Microsoft [!INCLUDE[btaA4SWIFTNoVersion](../../includes/btaa4swiftnoversion-md.md)]\SDK\Tools dossier. Pour mettre à jour la configuration de l’utilitaire, ouvrez BREDeployment.exe.config dans le bloc-notes et modifier les dossiers pour les stratégies de base, les schémas et les répertoires de vocabulaire.  
  
 Vous pouvez également utiliser l’utilitaire de déploiement à l’inverse de ce processus, l’annulation du déploiement et annulation de la publication les stratégies et vocabulaires. L’utilitaire a deux déployer et annuler le déploiement de fonctionnalités.  
  
### <a name="to-use-the-bre-deployment-utility"></a>Pour utiliser l’utilitaire de déploiement du moteur BRE  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **l’utilitaire de déploiement BRE**.  
  
2.  Dans l’utilitaire de déploiement BRE, cliquez sur **Parcourir**.  
  
3.  Sélectionnez l’ou les assemblys pour lesquels vous souhaitez publier et déployer des stratégies et des vocabulaires, puis cliquez sur déployé **OK**.  
  
4.  Cliquez sur **déployer**.  
  
    > [!NOTE]
    >  Selon les schémas que vous avez déployé avec cet assembly, l’utilitaire de déploiement du moteur BRE passe par le processus d’identification des règles associées et de les publier pour une utilisation avec le moteur BRE. Lorsque vous avez terminé, l’utilitaire de déploiement du moteur BRE affiche le message suivant : **fin du déploiement**. Utilisez l’éditeur des règles d’entreprise pour vérifier la réussite du déploiement.  
  
    > [!NOTE]
    >  Pour annuler le déploiement de stratégies et des vocabulaires, cliquez sur **annuler le déploiement**. Le processus d’annuler le déploiement n’annulez pas le déploiement vocabulaires A4SWIFT_CodeLists.xml et A4SWIFT_Functions.xml, lequel peuvent être utilisés par d’autres stratégies déployées.  
  
5.  Recherchez \< *lecteur*> : \Documents and Settings\All Users\Application Data pour confirmer que l’utilitaire créé le journal fichier BREDeploymentLog.txt.  
  
    > [!NOTE]
    >  Vous pouvez ouvrir le fichier journal à l’aide d’un éditeur de texte pour vérifier chaque étape de déploiement.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils](../../adapters-and-accelerators/accelerator-swift/tools.md)