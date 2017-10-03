---
title: "Comment générer des Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff74c67a-7e73-4153-9ec4-e6e50464ee92
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a911e4b0f1167e8ec200dad65b8dacb94bb08be3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-generate-instance-messages"></a>Comment générer des Messages d’Instance
Une fois que vous avez construit un schéma, une manière de vérifier votre travail consiste à générer un exemple de message d'instance à partir de ce schéma. À bien des égards, il est bien plus facile d'examiner un message d'instance plutôt que l'arborescence de schéma ou la représentation de langage XSD (XML Schema Definition) du schéma. En effet, un schéma doit représenter toutes les variations possibles des messages d'instance correspondants tandis qu'un message d'instance spécifique se borne à fournir certaines données à l'aide du format spécifié par le schéma. Le message d'instance généré est un exemple et est susceptible de ne pas contenir toutes les structures définies par le schéma correspondant.  
  
### <a name="to-explicitly-specify-a-file-to-contain-the-generated-instance-message"></a>Pour imposer explicitement à un fichier de contenir le message d'instance généré  
  
1.  Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **propriétés**.  
  
2.  Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.  
  
3.  Dans le **nom de fichier de sortie Instance** champ de valeur de propriété, tapez le nom d’un fichier ou utilisez le bouton de sélection (**...** ) situé à l’extrémité droite du champ de valeur à rechercher un fichier dans lequel seront placés les messages d’instance généré, puis cliquez **enregistrer**.  
  
### <a name="to-specify-the-type-of-the-generated-instance-message"></a>Pour spécifier le type du message d'instance généré  
  
1.  Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **propriétés**.  
  
2.  Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.  
  
3.  Dans le **Type sortie générer l’Instance** champ de valeur de propriété, utilisez la liste déroulante de liste pour sélectionner **XML** ou **natif** en tant que le type du message d’instance à générer.  
  
     **XML** est la valeur par défaut.  
  
### <a name="to-generate-a-sample-instance-message-for-a-schema"></a>Pour générer un exemple de message d'instance pour un schéma  
  
1.  Dans l’Explorateur de solutions, cliquez sur le schéma pour lequel vous souhaitez générer un message d’instance, puis cliquez sur **générer l’Instance**.  
  
2.  Dans la fenêtre Sortie, affichez les résultats. Les messages de réussite et d'erreur sont affichés dans cette fenêtre.  
  
> [!NOTE]
>  Si la fenêtre Sortie et/ou la fenêtre Liste des tâches ne se sont pas ouvertes pour indiquer si la génération de l'instance a réussi ou échoué, vous pouvez les ouvrir manuellement. Pour plus d’informations sur la gestion de ces fenêtres, consultez [la gestion des autres fenêtres Visual Studio](../core/how-to-manage-other-visual-studio-windows.md).  
  
> [!NOTE]
>  Si vous ne spécifiez pas une valeur pour le **référence de racine** propriété, l’Éditeur BizTalk génère un exemple de message d’instance pour le premier nœud racine dans le schéma. Si vous spécifiez une valeur pour le **référence de racine** propriété, l’Éditeur BizTalk génère un exemple de message d’instance pour cette racine.  
  
> [!NOTE]
>  Dans certains cas, les messages d'instance générés à partir d'un schéma particulier ne peuvent être validés en fonction de ce même schéma. Pour plus d’informations sur ces cas, consultez [problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md). En règle générale, vous souhaitez modifier un message d’instance généré et modifier les données qu’il contient afin qu’il représente de façon plus réaliste votre scénario. Utilisez ensuite ce message d'instance modifié pour valider votre schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Test de schémas](../core/testing-schemas.md)   
 [Validation de schéma](../core/schema-validation1.md)   
 [Validation et génération de Message d’instance](../core/instance-message-generation-and-validation.md)