---
title: "Comment valider les Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f6302c6-b56b-4572-aa76-0f4c4599672a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0baa898f801c924cffc5a446aa1a22d063a8fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-validate-instance-messages"></a>Comment valider les Messages d’Instance
Après avoir construit un schéma, vous pouvez vérifier votre travail en validant, en fonction de ce schéma, un message d'instance préexistant constituant de source sûre un bon exemple des messages d'instance de ce type.  
  
 Cette rubrique contient des instructions détaillées concernant cette tâche de validation.  
  
### <a name="to-validate-an-instance-message-against-a-schema"></a>Pour valider un message d'instance en fonction d'un schéma  
  
1.  Dans l’Explorateur de solutions, cliquez sur le schéma, puis cliquez sur **propriétés**.  
  
2.  Si nécessaire, dans la fenêtre Propriétés, développez le **général** section de la **général** en cliquant sur son signe plus (+) icône.  
  
3.  Dans le **nom d’Instance d’entrée** champ de valeur de propriété, tapez le nom d’un fichier ou utilisez le bouton de sélection (**...** ) situé à l’extrémité droite du champ de valeur pour accéder à un fichier qui contient le message d’instance à valider par rapport au schéma, puis cliquez sur **ouvrir**.  
  
4.  Dans **l’Explorateur de solutions**, cliquez sur le nom de schéma, puis cliquez sur **valider l’Instance**.  
  
5.  Dans la fenêtre Sortie, affichez les résultats. Les messages de réussite et d'erreur sont affichés dans cette fenêtre.  
  
> [!NOTE]
>  Dans certains cas, les messages d'instance générés à partir d'un schéma particulier ne peuvent être validés en fonction de ce même schéma. Pour plus d’informations sur ces cas, consultez [problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md). Généralement, vous souhaiterez modifier un message d'instance généré et modifier les données qu'il contient de sorte qu'il représente votre scénario de façon plus réaliste. Utilisez ensuite ce message d'instance modifié pour valider votre schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Test de schémas](../core/testing-schemas.md)   
 [Validation de schéma](../core/schema-validation1.md)   
 [Validation et génération de Message d’instance](../core/instance-message-generation-and-validation.md)