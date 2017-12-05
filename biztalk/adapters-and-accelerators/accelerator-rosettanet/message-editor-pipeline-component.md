---
title: Composant de Pipeline message Editor | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, Message Editor Pipeline Component
- Message Editor Pipeline Component
- messages, editing
- pipelines, Message Editor Pipeline Component
ms.assetid: f2b22dea-54e8-410b-868f-2978139f438b
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f5877fe04a87a8387340c8e4b004300f41e609e
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="message-editor-pipeline-component"></a>Composant de pipeline Message Editor
Ce composant vous permet de modifier automatiquement une partie d'un message en plusieurs parties dans un pipeline d'envoi ou de réception. Vous ajoutez ce composant à un pipeline existant pour configurer le remplacement dans le cadre du traitement par défaut.  
  
## <a name="building-the-message-editor-pipeline-component-into-an-existing-pipeline"></a>Génération du composant de pipeline Message Editor dans un pipeline existant  
 Pour utiliser le composant de pipeline Message Editor, vous devez l'ajouter à un pipeline existant. Pour plus d’informations, consultez « Création de Pipelines avec le Concepteur de Pipeline » dans l’aide de BizTalk Server.  
  
#### <a name="to-add-the-message-editor-pipeline-component-to-an-existing-pipeline"></a>Pour ajouter le composant de pipeline Message Editor à un pipeline existant  
  
1.  Démarrez Visual Studio.  
  
2.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
3.  Accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component, sélectionnez **MessageEditor.csproj**, puis cliquez sur **Ouvrir**.  
  
4.  Démarrez l’invite de commandes de Visual Studio.  
  
5.  À l'invite de commandes, accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug.  
  
6.  À l'invite de commandes, tapez **sn -k MessageEditor.snk** pour créer une clé, puis appuyez sur Entrée.  
  
7.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **MessageEditor**, puis cliquez sur **propriétés**.  
  
8.  Dans la page **Propriété de MessageEditor** , cliquez sur l'onglet **Signature** , puis cochez la case **Signer l'assembly** .  
  
9. Dans la liste déroulante **Choisir un fichier de clé de nom fort** , accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Editor Pipeline Component\obj\debug et sélectionnez **MessageEditor.snk** , puis cliquez sur **Ouvrir**.  
  
10. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **MessageEditor**, puis cliquez sur **Générer**. Dans le volet de sortie, vérifiez que la génération a réussi.  
  
11. Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
12. Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] avec le bouton droit de l’Explorateur de solutions, le déplacement à C:\Program Files\Microsoft BizTalk 2013 Accelerator RosettaNet\SDK\Message éditeur Pipeline Component\obj\debug, **Microsoft.Solutions.BTARN.SDK.MessageEditor.dll**, puis cliquez sur **copie**.  
  
13. Accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline Components, cliquez avec le bouton droit sur **Composants de pipeline**, puis cliquez sur **Coller**.  
  
14. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet**.  
  
15. Ouvrez le projet contenant le pipeline auquel vous voulez ajouter l'éditeur.  
  
16. Dans l'Explorateur de solutions, double-cliquez sur le nom du pipeline pour l'ouvrir dans le Concepteur de pipeline.  
  
17. Cliquez avec le bouton droit dans le volet Composants de pipeline BizTalk du volet Boîte à outils, puis cliquez sur **Ajouter/supprimer des éléments**.  
  
18. Dans la boîte de dialogue **Personnaliser la boîte à outils** , sous l'onglet **Composants de pipeline BizTalk** , sélectionnez **BTARN Message Editor Component**, puis cliquez sur **OK**.  
  
19. Dans le volet Composants de pipeline BizTalk du volet Boîte à outils, cliquez en maintenant le bouton enfoncé sur **BTARN Message Editor Component**, puis faites glisser le composant à l'emplacement souhaité dans le pipeline.  
  
20. Dans le volet Composants de pipeline BizTalk du volet Boîte à outils, cliquez en maintenant le bouton enfoncé sur **BTARN Message Editor Component**, puis faites glisser le composant à l'emplacement souhaité dans le pipeline.  
  
    > [!NOTE]
    >  Il est recommandé d'ajouter le composant de pipeline Message Editor après la phase de désassemblage dans le composant de pipeline de réception ou pendant la phase de préassemblage du composant de pipeline d'envoi.  
  
21. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le Concepteur de Pipeline, sélectionnez le **BTARN Message Editor Component** forme.  
  
22. Dans le volet Propriétés, dans la zone de texte associée à **Requête XPath**, tapez le nom de l'élément XPath dont vous voulez modifier la valeur.  
  
23. Dans la zone de texte associée à **Valeur XPath**, tapez la valeur avec laquelle vous voulez définir l'élément XPath.  
  
24. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**. Vérifiez que la génération aboutit.  
  
25. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**. Vérifiez que le déploiement aboutit.  
  
## <a name="example"></a>Exemple  
 Pour modifier la valeur de l'élément `ProprietaryDocumentIdentifier` dans le schéma PIP 0C1, ajoutez la requête XPath indiquée dans la section de code suivante à la propriété de la requête XPath du composant de pipeline Message Editor.  
  
```  
/*[local-name()='Pip0C1AsynchronousTestNotification' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='thisDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']/*[local-name()='ProprietaryDocumentIdentifier' and namespace-uri()='http://schemas.microsoft.com/biztalk/btarn/2004/0C1_MS_R01_02_AsynchronousTestNotification.dtd']  
```  
  
 Pour obtenir une requête XPath complète, ouvrez le schéma dans l'Éditeur BizTalk, puis copier le Xpath de la propriété `Instance XPath` sous la fenêtre Propriétés. La requête XPath que vous fournissez doit contenir toutes les références d'espace de noms.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)