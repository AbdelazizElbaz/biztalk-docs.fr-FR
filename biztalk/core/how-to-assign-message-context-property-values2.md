---
title: "Comment attribuer des Values2 de propriété de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 137f82ab-f301-465d-be78-a6e67971dd3b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f0e19a425a4842e3bfac150d1cac851e4686f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-message-context-property-values"></a>Affectation de valeurs aux propriétés de contexte d'un message
Pour gérer la session de connexion JD Edwards OneWorld à partir d'une orchestration BizTalk, vous devez ajouter la référence à Microsoft.BizTalk.Adapters.JDEProperties.dll dans votre projet. Cet assembly se trouve dans le répertoire %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
 Une fois ce schéma de propriété référencé, d'autres propriétés de contexte sont accessibles à divers outils de développement BizTalk (par exemple, forme Assignation du message au sein du Concepteur d'orchestration).  
  
 Pour accéder à une propriété de contexte, vous devez spécifier une des propriétés de contexte disponibles dans l'espace de noms JD Edwards OneWorld. Pour lire la propriété de contexte d'un message reçu d'un port lié à l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld, vous devez utiliser la syntaxe Message(JDE.Property) dans une expression. Consultez la gestion de session JD Edwards OneWorld pour obtenir la liste des propriétés.  
  
 Dans BizTalk, les messages sont immuables.  
  
### <a name="to-assign-a-message-context-property-value"></a>Pour affecter une valeur de propriété de contexte à un message  
  
1.  Créez un message.  
  
2.  Définissez-en le contenu (par exemple, en assignant un message existant).  
  
3.  Définissez les propriétés.  
  
 Pour affecter les propriétés de contexte à un message destiné à un port d'envoi lié à l'adaptateur Microsoft BizTalk pour JD Edwards OneWorld, utilisez l'opérateur d'assignation de message. Spécifiez ensuite une des propriétés de contexte disponibles dans l'espace de noms JD Edwards OneWorld.  
  
 La syntaxe est la suivante :`Message(JDE.Property) = value;`  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de contexte de Message](../core/using-message-context-properties2.md)   
 [Sur la gestion de Session](../core/about-session-management1.md)   
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)