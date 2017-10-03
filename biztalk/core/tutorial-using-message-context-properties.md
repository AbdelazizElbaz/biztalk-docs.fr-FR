---
title: "Didacticiel : Utilisation des propriétés de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, changing priority
- message context properties, tutorial
ms.assetid: 6e52593b-5001-4740-89fb-e003e12d8e69
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f122215baa5660294e159e4f1d6967a2df5ba9b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tutorial-using-message-context-properties"></a>Didacticiel : Utilisation des propriétés de contexte de Message
Ce didacticiel présente l'utilisation des propriétés de contexte de BizTalk Server pour définir les champs du descripteur de message de TIBCO Enterprise Message Service (EMS) dans votre orchestration. Ce didacticiel suppose que vous disposez d'une orchestration qui reçoit un message en provenance d'un port de réception et qui l'envoie vers un port d'envoi lié à l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service.  
  
 La procédure suivante décrit la manière de modifier la priorité du message TIBCO EMS en modifiant la valeur de la propriété de contexte TibcoEMS.Priority. Dans BizTalk Server, les messages sont immuables. Par conséquent, pour modifier une valeur de propriété, vous devez créer et modifier un nouveau message. Pour ce faire, insérez une forme Assignation de message entre les formes Réception et Envoi. Toutefois, vous devez commencer par référencer le fichier DLL du schéma pour accéder aux propriétés TIBCO EMS.  
  
### <a name="to-reference-the-schema-dll"></a>Pour référencer le fichier DLL du schéma  
  
1.  Ouvrez **l’Explorateur de solutions** dans Visual Studio.  
  
2.  Avec le bouton droit **références**, puis sélectionnez **ajouter une référence**.  
  
     La boîte de dialogue **Ajouter une référence** s’affiche.  
  
3.  Cliquez sur le **Parcourir** onglet.  
  
     Le **sélectionner le composant** boîte de dialogue s’affiche.  
  
4.  Recherchez  **\<TIBCO EMS_Adapter_installation_directory > \bin**, puis sélectionnez **Microsoft.Adapters.TibcoEMSProperties.dll**.  
  
5.  Cliquez sur **Ouvrir**.  
  
     Le fichier DLL apparaît dans le **composants sélectionnés** dans les **ajouter une référence** boîte de dialogue.  
  
6.  Cliquez sur **OK** , puis double-cliquez sur votre orchestration pour accéder au Concepteur d’Orchestration.  
  
7.  Sur le **vue** menu, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
8.  Dans la vue Orchestration, cliquez sur **Messages** et sélectionnez **nouveau Message**.  
  
9. Modifier les propriétés de votre nouveau message et attribuer un **Type de Message**.  
  
     Vous allez affecter Message_1 à Message_2. Vous devez donc attribuer le même type de message aux deux messages.  
  
10. Dans le menu **Affichage** , cliquez sur **Boîte à outils**.  
  
11. Faites glisser un **assignation du Message** forme sur votre orchestration où vous souhaitez créer un nouveau message.  
  
12. Modifier la forme externe ConstructMessage_1 et sélectionnez votre nouveau message, Message_2, dans le **Messages construits** propriété.  
  
13. Double-cliquez sur la forme interne MessageAssignment_1.  
  
     L'Éditeur d'expression BizTalk s'affiche.  
  
14. Dans l'Éditeur d'expression BizTalk, tapez votre code.  
  
15. Copiez d'abord un message existant puis affectez des valeurs aux propriétés de contexte.  
  
     La syntaxe est `Message(property) = value;`. Exemple :  
  
    ```  
    Message_2 = Message_1;  
    Message_2( TibcoEMS.Priority) = 6;  
    ```  
  
     Pour obtenir une liste des propriétés prises en charge que vous pouvez utiliser dans vos messages personnalisés, consultez TIBCO EMS.  
  
16. Cliquez sur **OK** pour fermer l’éditeur d’Expression BizTalk et enregistrer votre code.  
  
17. Cliquez sur la forme envoi et affectez le **Message** être **Message_2**.  
  
18. Vérifiez que les formes dans le reste du flux de messages fonctionnent sur le message approprié.  
  
19. Avec le bouton droit de votre projet dans l’Explorateur de solutions, puis sélectionnez **Build**.  
  
20. Avec le bouton droit de votre projet et sélectionnez **déployer**.  
  
21. Sélectionnez **lier**, **Enlist**, et **Démarrer** dans l’Explorateur BizTalk pour tester votre orchestration.  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de contexte de message](../core/message-context-properties2.md)