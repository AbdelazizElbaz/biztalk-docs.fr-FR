---
title: "Procédure pas à pas : Modification de la stratégie | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dd74440-2a45-4a1a-8e36-98796e1e1392
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7292d541adaf0ae2242d1c504f1a845dde66f5dd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-modifying-the-policy"></a>Procédure pas à pas : Modification de la stratégie
Cette procédure pas à pas fournit des instructions détaillées pour la création d’une nouvelle version de la **POVocabulary**, création d’une nouvelle version de la **ProcessPurchaseOrder** stratégie et à l’aide de la dernière version de la **POVocabulary** dans la nouvelle version de la **ProcessPurchaseOrder** stratégie.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez effectuer la [procédure pas à pas : ajout d’une règle à la stratégie](../core/walkthrough-adding-a-rule-to-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.  
  
## <a name="overview-of-this-walkthrough"></a>Vue d’ensemble de cette procédure pas à pas  
 Cette procédure pas à pas regroupe trois procédures, comme indiqué dans le tableau ci-dessous.  
  
|Titre de la procédure|Description de la procédure|  
|---------------------|---------------------------|  
|Pour modifier le vocabulaire POVocabulary|Fournit des instructions détaillées pour la création d’une nouvelle version de vocabulaire pour modifier la valeur de **nombre maximal d’éléments autorisés** de **500** à **1000**.|  
|Pour modifier la stratégie ProcessPurchaseOrder afin d'utiliser le vocabulaire mis à jour|Fournit des instructions détaillées pour la création d’une nouvelle version de la **ProcessPurchaseOrder** stratégie à utiliser la nouvelle version de **POVocabulary**.|  
|Pour tester la solution|Fournit des instructions détaillées sur le test de la solution et la vérification de l'application de la nouvelle stratégie.|  
  
### <a name="to-modify-the-povocabulary-vocabulary"></a>Pour modifier le vocabulaire POVocabulary  
  
1.  Sur le **Démarrer** menu, ouvrir **Éditeur des règles d’entreprise**. Si vous avez Éditeur des règles d’entreprise déjà ouvrir, appuyez sur F5 ou cliquez sur **recharger** sur la **fichier** menu pour l’actualiser.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans la fenêtre Explorateur de faits, développez **vocabulaires**, puis développez **POVocabulary**.  
  
3.  Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **copie**.  
  
4.  Avec le bouton droit **POVocabulary**, puis cliquez sur **coller une Version de vocabulaire**.  
  
5.  Double-cliquez sur **nombre maximal d’éléments autorisés** dans **Version 1.1 (non enregistrée)** pour démarrer l’Assistant Définition de vocabulaire.  
  
6.  Cliquez sur **Suivant**.  
  
7.  Cliquez sur **Suivant**.  
  
8.  Remplacez la valeur de **500** à **1000**.  
  
9. Cliquez sur **Terminer**.  
  
10. Avec le bouton droit **Version 1.1 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
11. Avec le bouton droit **Version 1.1**, puis cliquez sur **publier**.  
  
### <a name="to-modify-the-processpurchaseorder-policy-to-use-the-updated-vocabulary"></a>Pour modifier la stratégie ProcessPurchaseOrder afin d'utiliser le vocabulaire mis à jour  
  
1.  Dans l’Explorateur de stratégies, développez **stratégies**, puis développez **ProcessPurchaseOrder**.  
  
2.  Avec le bouton droit **Version 1.2**, puis cliquez sur **copie**.  
  
3.  Avec le bouton droit **ProcessPurchaseOrder**, puis cliquez sur **PastePolicyVersion**.  
  
4.  Cliquez sur **ApprovalRule** dans **Version 1.3 (non enregistrée)**.  
  
5.  Dans l’Explorateur de faits, développez **vocabulaires**, développez **POVocabulary**, puis développez **Version 1.1 publiée**.  
  
6.  Faites glisser **nombre maximal d’éléments autorisés** dans **Version 1.1 publiée** remplacer **nombre maximal d’éléments autorisés** de la version 1.0, dans le volet IF.  
  
7.  Répétez les étapes 4 à 6 avec **DeniedRule**.  
  
8.  Avec le bouton droit **Version 1.3 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
9. Avec le bouton droit **Version 1.3**, puis cliquez sur **publier**.  
  
10. Avec le bouton droit **Version 1.3**, puis cliquez sur **déployer**.  
  
### <a name="to-test-the-solution"></a>Pour tester la solution  
  
1.  Cliquez sur **Démarrer**, ouvrez **Administration de BizTalk Server**. Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.  
  
2.  Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**. Si **Démarrer** est désactivée, l’application est déjà en cours d’exécution et vous pouvez ignorer l’étape suivante.  
  
3.  Cliquez sur **Démarrer**.  
  
4.  Copie le **SamplePO2.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.  
  
5.  Un fichier de sortie doit s'afficher dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output. Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.  
  
    > [!NOTE]
    >  La valeur de la **quantité** champ dans SamplePO2.xml est 700. La version 1.3 de la **ProcessPurchaseOrder** stratégie compare cette valeur à 1 000 au lieu de comparer avec 500 comme le faisait la version 1.2.  
  
## <a name="comments"></a>Commentaires  
  
-   Une stratégie publiée n'est pas modifiable. Vous devez créer une nouvelle version de la stratégie pour pouvoir la modifier. De même, un vocabulaire publié n'est pas modifiable. Vous devez créer une nouvelle version du vocabulaire pour pouvoir le modifier.  
  
-   L’orchestration d’appel d’une stratégie à l’aide de la **appeler règles** forme utilise la dernière version déployée de la stratégie. Par exemple, si vous disposez des versions 1.0, 1.1, 1.2 et 1.3 de la stratégie déployée, l'orchestration utilise la version 1.3. Si celle-ci n'est pas déployée et que la version 1.2 l'est, l'orchestration utilise la version 1.2. Par conséquent, si vous souhaitez utiliser la version 1.2, il vous suffit d'annuler le déploiement de la version 1.3, et de vous assurer que la version 1.2 est déployée.  
  
-   Pour utiliser une version spécifique d’une stratégie à partir d’une orchestration, vous devez utiliser un **Expression** mettre en forme et appeler le moteur de règles pour la stratégie d’exécution par programme à l’aide de la **Policy.Execute** (méthode).  
  
-   Notez que la version 1.3 de la stratégie utilise les définitions de vocabulaire des versions 1.0 et 1.1 de POVocabulary. Si vous exportez la version 1.3 de la stratégie vers un fichier XML, et l'importez afin de créer la stratégie sur un autre ordinateur, le processus d'importation recherche les deux versions du vocabulaire. Vous devez donc exporter les versions 1.0 et 1.1 du vocabulaire et les importer avant d'importer la version 1.3 de la stratégie.  
  
-   Après avoir déployé une version plus récente de la stratégie, vous devez patienter environ 60 secondes avant de tester la solution. Le service de mise à jour du moteur des règles recherche les mises à jour d'une stratégie toutes les 60 secondes (1 minute) par défaut. En cas de mises à jour, il actualise le cache avec les informations mises à jour.  
  
## <a name="next-steps"></a>Étapes suivantes  
  
-   Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : exécution de la stratégie de suivi](../core/walkthrough-tracking-policy-execution.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour le suivi des détails de la stratégie d’exécution.