---
title: Message Inspector Pipeline Component | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipelines, custom pipelines
- pipelines, Message Inspector Pipeline Component
- Message Inspector Pipeline Component
- pipelines, creating
ms.assetid: d9c00718-c8cd-4289-8f58-e4edc61b9a05
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d146dbeaa94d47799794de7fa6f9e6b9082f9fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-inspector-pipeline-component"></a>Message Inspector Pipeline Component
Ce composant de pipeline vous permet d'examiner les différentes parties et le contexte d'un message à parties multiples pour déterminer si un problème existe au niveau du message. Ce composant est utilisé à des fins de dépannage.  
  
 Le composant de pipeline dépose les fichiers XML dans un répertoire que vous désignez. Chacun de ces fichiers contient l'une des quatre parties d'un message RNIFv2.0 (en-tête de préambule, en-tête de livraison, en-tête de service et contenu du service) ou l'une des trois parties d'un message RNIFv1.1 (en-tête de préambule, en-tête de service et contenu du service). Un autre fichier XML contient le contexte du message.  
  
 Ce composant est généré dans un pipeline personnalisé et attaché à un port d'envoi. Vous créez un filtre dans le port d'envoi pour vous abonner aux messages à surveiller. Cette procédure de dépannage vient compléter le traitement qui standard [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] exécute déjà.  
  
## <a name="building-a-custom-pipeline-using-the-message-inspector-pipeline-component"></a>Génération d'un pipeline personnalisé à l'aide de Message Inspector Pipeline Component  
 Pour utiliser Message Inspector Pipeline Component, vous devez générer et déployer un pipeline personnalisé qui inclut le composant. Pour plus d’informations, consultez « Création de Pipelines avec le Concepteur de Pipeline » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
#### <a name="to-deploy-the-message-inspector-pipeline-component"></a>Pour déployer le composant de pipeline Message Inspector  
  
1.  Démarrez [!INCLUDE[vs2012](../../includes/vs2012-md.md)].  
  
2.  Dans le menu **Fichier** , pointez sur **Ouvrir**, puis cliquez sur **Projet**.  
  
3.  Passez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component, sélectionnez **MessageInspector.csproj**, puis cliquez sur **Ouvrir**.  
  
4.  Ouvrez le [!INCLUDE[vs2012](../../includes/vs2012-md.md)] invite de commandes.  
  
5.  À l'invite de commandes, passez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug.  
  
6.  À l'invite de commandes, tapez **"sn -k MessageInspector.snk"** pour créer une clé, puis appuyez sur Entrée.  
  
7.  Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur **MessageInspector**, puis cliquez sur **propriétés**.  
  
8.  Dans la page **Propriété de MessageInspector**  , cliquez sur l'onglet **Signature** , puis cochez la case **Signer l'assembly** .  
  
9. Dans la liste déroulante **Choisir un fichier de clé de nom fort** , accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug et sélectionnez **MessageInspector.snk** , puis cliquez sur **Ouvrir**.  
  
10. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur **MessageInspector**, puis cliquez sur **Générer**. Dans le volet de sortie, vérifiez que la génération a réussi.  
  
11. Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Accessoires**, puis cliquez sur **Explorateur Windows**.  
  
12. Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] avec le bouton droit de l’Explorateur de solutions, le déplacement à C:\Program Files\Microsoft BizTalk 2013 Accelerator RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug **Microsoft.Solutions.BTARN.SDK.MessageInspector.dll**, puis cliquez sur **copie**.  
  
13. Passez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\Pipeline Components, cliquez avec le bouton droit sur **Composants de Pipeline**, puis cliquez sur **Coller**.  
  
14. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.  
  
15. Dans le volet Modèles de la boîte de dialogue **Nouveau projet** , sélectionnez **Projet BizTalk Server vide**, puis nommez le projet dans la zone **Nom** . Dans la zone **Emplacement** , accédez au dossier dans lequel vous souhaitez enregistrer le projet, puis cliquez sur **OK**.  
  
16. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, pointez sur **Ajouter**, puis cliquez sur **Ajouter un nouvel élément**.  
  
17. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Pipeline d'envoi**, nommez le fichier de pipeline personnalisé dans la zone **Nom** , puis cliquez sur **Ouvrir**.  
  
    > [!NOTE]
    >  Ajoutez uniquement Message Inspector Pipeline Component à des ports d'envoi, et non à des ports de réception.  
  
18. Cliquez avec le bouton droit dans le volet Composants de pipeline BizTalk du volet Boîte à outils, puis cliquez sur **Ajouter/supprimer des éléments**.  
  
19. Dans la boîte de dialogue **Personnaliser la boîte à outils** , sous l'onglet **Composants de pipeline BizTalk** , sélectionnez **BTARN Message Inspector Component**, puis cliquez sur **OK**.  
  
20. Dans le volet Composants de pipeline BizTalk du volet Boîte à outils, cliquez avec le bouton gauche sur **BTARN Message Inspector Component**et maintenez-le enfoncé, puis faites glisser le composant sur une zone **Déposer ici** .  
  
21. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur le nom du projet de pipeline, puis cliquez sur **propriétés**.  
  
22. Dans la boîte de dialogue **Pages de propriétés** , cliquez sur **Propriétés communes**, puis cliquez sur **Assembly**.  
  
23. Dans la zone de texte associée à **Fichier de clé de l'assembly**du volet droit, cliquez sur les points de suspension, accédez à C:\Program Files\Microsoft BizTalk 2013 Accelerator for RosettaNet\SDK\Message Inspector Pipeline Component\obj\debug, sélectionnez **MessageInspector.snk**, puis cliquez sur **OK**.  
  
24. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] le Concepteur de Pipeline, sélectionnez le **BTARN Message Inspector Component** forme.  
  
25. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, dans le **répertoire** , tapez le nom du répertoire dans lequel vous souhaitez supprimer les fichiers XML.  
  
26. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Générer**. Vérifiez que la génération aboutit.  
  
27. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le nom du projet, puis cliquez sur **Déployer**. Vérifiez que le déploiement aboutit.  
  
28. Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **vue** menu, cliquez sur **l’Explorateur BizTalk**.  
  
29. Cliquez avec le bouton droit sur **Ports d'envoi**, puis cliquez sur **Ajouter un port d'envoi**.  
  
30. Dans la boîte de dialogue **Créer un port d'envoi** , cliquez sur **OK**.  
  
31. Dans la boîte de dialogue **Propriétés de port d'envoi** , dans la zone **Nom** , nommez le port d'envoi. Sélectionnez ensuite **Principal** dans le volet gauche, cliquez sur **Type de transport** dans le volet droit, puis sélectionnez **Fichier**.  
  
32. Dans la boîte de dialogue **Propriétés de port d'envoi** , dans la zone **Adresse (URI)** , cliquez sur le bouton de sélection (**...**).  
  
33. Dans la boîte de dialogue **Propriétés du transport de fichier** , tapez le nom du dossier **Destination** , puis cliquez sur **Envoyer** dans le volet gauche. Sélectionnez ensuite le pipeline personnalisé que vous venez de créer comme **Pipeline d'envoi** dans le volet droit.  
  
34. Cliquez sur **filtres & mappages** dans le volet gauche, puis cliquez sur **filtres**.  
  
35. Entrez une expression de filtre dans le volet droit pour désigner le type de fichiers pour lesquels vous souhaitez le pipeline dépose des fichiers XML. Par exemple, si vous souhaitez déposer des fichiers pour tous les messages RNIF v1.1, sélectionnez Microsoft.Solutions.BTARN.Schemas.RNIFv11.GlobalBusinessAction en tant que **Propriété** et « Existe » en tant qu' **Opérateur** , puis cliquez sur **OK**.  
  
36. Dans l'Explorateur BizTalk, cliquez avec le bouton droit sur le port d'envoi que vous venez de créer, cliquez sur **Inscrire**, cliquez à nouveau avec le bouton droit sur le port d'envoi, puis cliquez sur **Démarrer**.  
  
## <a name="remarks"></a>Notes  
 Dans le cadre d'un traitement standard, vous pouvez examiner une seule partie du message à la fois (la partie que vous avez désignée comme le corps du message dans l'orchestration). Vous pouvez donc examiner une seule partie dans la console Administration de BizTalk, et votre capacité à résoudre les problèmes est limitée. Message Inspector Pipeline Component vous aide à contourner cet obstacle.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)