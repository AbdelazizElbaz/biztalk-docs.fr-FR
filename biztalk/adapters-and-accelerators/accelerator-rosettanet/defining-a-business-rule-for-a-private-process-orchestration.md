---
title: "Définition d’une règle d’entreprise pour une Orchestration de processus de privé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, policies
- vocabularies, saving
- private processes, orchestrations
- business rules, private processes
- creating, vocabularies
- vocabularies, business rules
- business rules, vocabularies
- policies, deploying
- vocabularies, creating
- orchestrations, private-process orchestrations
- private processes, customizing
- policies, publishing
- business rules, Set elements
- creating, policies
- customizing private processes
- Set elements
- business rules, orchestrations
- publishing, vocabularies
- vocabularies, publishing
- creating, rules
- business rules, Get elements
- policies, saving
- publishing, policies
- Get elements
- orchestrations, business rules
- rules
- private processes, business rules
- policies, creating
ms.assetid: 5d2b0257-1b15-482b-a562-798b808e9a2d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c668b3123483de1d53afa8ca74cf9d7d2376ecea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-a-business-rule-for-a-private-process-orchestration"></a>Définition d’une règle d’entreprise pour une Orchestration de processus de privé
Vous pouvez définir une règle d’entreprise pour une utilisation dans un processus privé d’accusé de réception. Vous pouvez ainsi modifier la règle d’entreprise dynamiquement sans arrêter l’orchestration de processus privé. Ce processus utilise le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] moteur des règles d’entreprise. Ce processus implique les étapes suivantes :  
  
1.  Ajout d’un vocabulaire. Cela implique la définition de valeur de constante d’au moins un vocabulaire. Cela définit un seuil de la règle d’entreprise. Il implique également la définition de document XML `Get` et `Set` éléments. Ceci établit la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] utilise le seuil.  
  
2.  Ajout d’une nouvelle stratégie. Cela implique la création d’une stratégie, création d’un ensemble de règles, puis l’enregistrement, publication et déploiement de la stratégie.  
  
3.  Appel de la règle d’entreprise à partir de l’orchestration de processus privé. Cela implique l’ajout d’un **appeler règles** forme à l’orchestration.  
  
 Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK comprend un exemple [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stratégie commerciale, samplebtarnpolicy.xml, dans \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\ SDK\PipAutomation\3A4. Pour plus d’informations, consultez [stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).  
  
 L’orchestration PIP3A4PrivateResponder.odx est un exemple d’orchestration de processus privé qui montre comment implémenter un processus PIP (Partner Interface)-processus privé de répondeur spécifiques incorporant une règle d’entreprise. Pour plus d’informations sur cet exemple, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
 Pour plus d’informations sur les vocabulaires et des stratégies, consultez la rubrique « Développement avec des règles d’entreprise » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].  
  
### <a name="to-add-a-new-vocabulary"></a>Pour ajouter un nouveau vocabulaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
2.  Si le **ouvrir le magasin de règles** boîte de dialogue s’ouvre, sélectionnez le **moteur de règles BizTalk** base de données que vous configurez sur le serveur actuel, puis cliquez sur **OK**.  
  
3.  Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Éditeur des règles d’entreprise, dans le volet Explorateur de faits, cliquez sur **vocabulaires**, puis cliquez sur **ajouter un nouveau vocabulaire**.  
  
4.  Dans le volet des propriétés (partie inférieure gauche), définissez la **nom** nom à la propriété de vocabulaire approprié, puis appuyez sur **entrée**.  
  
5.  Développez le dossier de vocabulaire que vous venez de créer, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.  
  
6.  Dans la page **Assistant Définition de vocabulaire** , sélectionnez **Valeur constante, plage de valeurs ou ensemble de valeurs**, puis cliquez sur **Suivant**.  
  
7.  Sur le **valeur constante, plage de valeurs ou ensemble de valeurs** page, dans le **nom de la définition** , tapez le nom de la valeur de constante de vocabulaire approprié, tel que **quantité maximale autorisée** , puis cliquez sur **suivant**.  
  
8.  Sur le **définir une valeur constante** page, dans le **champ de valeur** zone, tapez le seuil, puis cliquez sur **Terminer**.  
  
### <a name="to-define-get-and-set-elements"></a>Pour définir les obtenir et définir les éléments  
  
1.  Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de faits, sous le dossier du vocabulaire créé dans « pour ajouter une nouvelle procédure vocabulaire », cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle définition**.  
  
2.  Sur le **Assistant Définition de vocabulaire** page, sélectionnez **Document élément ou attribut XML**, puis cliquez sur **suivant**.  
  
3.  Sur le **Document élément ou attribut XML** page, dans la zone de texte Nom de la définition, tapez un nom pour un **obtenir** élément.  
  
4.  Cliquez sur **Parcourir**, accédez à l’emplacement du schéma que vous souhaitez utiliser, sélectionnez le fichier de schéma, puis cliquez sur **ouvrir**.  
  
5.  Si le **sélectionner un nœud racine** s’ouvre, sélectionnez le nœud racine à rechercher.  
  
6.  Sur le **sélectionnez une liaison** page, de passer au champ pour lequel vous souhaitez définir le seuil, puis cliquez sur **OK**.  
  
7.  Dans le **Type de Document** , tapez le nom du document.  
  
8.  Dans le **Type d’opération** section, sélectionnez **effectuer une opération « Get »**.  
  
9. Cliquez sur **Terminer**.  
  
10. Répétez ces étapes pour définir une ou plusieurs `Set` opérations, sélectionnez **effectuer une opération « Set »** pour le **Type d’opération**.  
  
### <a name="to-save-and-publish-the-vocabulary"></a>Pour enregistrer et publier le vocabulaire  
  
1.  Dans l’éditeur des règles d’entreprise, dans le volet de l’Explorateur de faits, sous le dossier du vocabulaire que vous avez créé, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
2.  Dans le volet Explorateur de faits, sous le dossier 3A4PurchaseOrderVocabulary, avec le bouton droit **Version 1.0**, puis sélectionnez **publier**.  
  
### <a name="to-add-a-new-policy-and-rules"></a>Pour ajouter une nouvelle stratégie et les règles  
  
1.  Dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.  
  
2.  Cliquez sur **Policy1**.  
  
3.  Dans le volet Propriétés, définissez la **nom** propriété le nom de la stratégie appropriée.  
  
4.  Dans le volet Explorateur de stratégies, sous le dossier pour la nouvelle stratégie, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **ajouter une nouvelle règle**.  
  
5.  Cliquez sur **règle1**.  
  
6.  Dans le volet Propriétés, définissez la **nom** propriété le nom de la règle votre choix, puis appuyez sur **entrée**.  
  
7.  Dans l’éditeur des règles, sous la **IF** volet, avec le bouton droit **Conditions**, puis sélectionnez une condition logique, le cas échéant.  
  
8.  Dans le volet Explorateur de faits, sous **vocabulaires**, développez **prédicats**, développez **Version 1.0 - publiée**, sélectionnez le prédicat voulu, faites-le glisser vers l’éditeur, puis déposez-le sur **Conditions** ou l’opérateur logique.  
  
9. Dans le volet Explorateur de faits, sous le dossier vocabulaires, développez successivement le vocabulaire que vous avez créé, **Version 1.0 - publiée**, sélectionnez un `Get` ou `Set` élément, faites-le glisser vers l’éditeur et déposez-le sur **argument1**.  
  
10. Sous le dossier du vocabulaire, sélectionnez un `Get` ou `Set` élément, faites-le glisser vers l’éditeur et déposez-le sur **argument2**.  
  
11. Sous le dossier du vocabulaire, sélectionnez un `Set` élément, faites-le glisser vers l’éditeur et déposez-le dans la **Actions** zone dans le volet THEN.  
  
12. Si une variable est associée à la `Set` élément, cliquez sur la variable, apportez les modifications appropriées, puis appuyez sur **entrée**. Le cas échéant, répétez avec d’autres `Set` éléments.  
  
### <a name="to-save-publish-and-deploy-the-policy"></a>Pour enregistrer, publier et déployer la stratégie  
  
1.  Lorsque vous avez terminé de définir les règles, dans l’éditeur des règles d’entreprise, dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0 (non enregistrée)**, puis cliquez sur **enregistrer**.  
  
2.  Dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0**, puis cliquez sur **publier**.  
  
3.  Dans le volet Explorateur de stratégies, sous le dossier de stratégie que vous avez créé, cliquez sur **Version 1.0**, puis cliquez sur **déployer**.  
  
### <a name="to-call-the-business-rule-from-the-orchestration"></a>Pour appeler la règle d’entreprise à partir de l’orchestration  
  
1.  Démarrez **Microsoft Visual Studio 2012**.  
  
2.  Sur le **fichier** menu, pointez sur Ouvrir, puis cliquez sur **projet/Solution**.  
  
3.  Recherchez la solution qui contient l’orchestration que vous devez appeler à partir de la règle d’entreprise, puis cliquez sur **ouvrir**.  
  
4.  Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
5.  Développez **Variables**. Assurez-vous que la liste de variables d’orchestration contient une variable qui correspond à chaque paramètre dans la stratégie d’entreprise que vous appelez à partir de l’orchestration. Assurez-vous que la variable a le même type que le paramètre de stratégie. Si la liste ne contient pas une variable d’orchestration pour chaque paramètre de stratégie, cliquez sur **Variables**, puis cliquez sur **nouvelle Variable**. Dans Vue Orchestration, tapez un nom de variable, puis, dans la fenêtre Propriétés, entrez le type du paramètre.  
  
6.  À partir de la **boîte à outils**, faites glisser un **appeler règles** forme sur l’aire de conception d’orchestration et déposez-le sous le **réception** forme.  
  
7.  Double-cliquez sur le **appeler règles** forme.  
  
8.  Dans le **sélectionnez la stratégie commerciale que vous souhaitez appeler** , sélectionnez la stratégie d’entreprise à partir de la liste déroulante.  
  
9. Pour le premier paramètre, pour **nom de paramètre**, sélectionnez un nom dans la liste déroulante.  
  
    > [!NOTE]
    >  BTARN remplit la **paramètre de stratégie** liste avec tous les paramètres dans la stratégie d’entreprise. Pour chaque paramètre dans la liste, BTARN entre une valeur dans **Type de paramètre** à partir de la stratégie d’entreprise. Dans la liste déroulante associée **nom de paramètre**, BTARN entre les noms de toutes les variables à partir de la liste des variables de l’orchestration qui a le même type que les paramètres de stratégie. En sélectionnant une variable d’orchestration, vous associez cette variable avec le paramètre de stratégie. Vous pouvez afficher les variables d’orchestration dans Vue Orchestration.  
  
10. Répétez l’étape 9 pour tous les autres paramètres.  
  
11. Dans la fenêtre de conception de l’Orchestration, entrez toutes les formes supplémentaires requis pour le traitement de la stratégie d’entreprise, y compris l’ajout un **décision** sous la forme la **appeler règles** forme.  
  
    > [!NOTE]
    >  Pour obtenir un exemple montrant comment utiliser un **appeler règles** forme dans une orchestration, reportez-vous à l’orchestration PIP3A4PrivateResponder.odx incluse dans le SDK de BTARN. Il se trouve à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\PipAutomation\3A4\PR. Pour plus d’informations, consultez [3 a 4 privé répondeur Orchestration à l’aide une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md).  
  
12. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)   
 [Stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)