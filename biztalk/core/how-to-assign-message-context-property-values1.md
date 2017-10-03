---
title: "Comment attribuer des Values1 de propriété de contexte de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e76c62-3110-482c-8083-84d411e6f475
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39bb2a4c6520c1ff3a21889e7508bb2cf417b817
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-assign-message-context-property-values"></a>Affectation de valeurs aux propriétés de contexte d'un message
Pour gérer la session de connexion de l'adaptateur JD Edwards OneWorld à partir d'une orchestration BizTalk, vous devez ajouter la référence à Microsoft.BizTalk.Adapters.JDEProperties.dll dans votre projet. Cet assembly se trouve dans le répertoire %SystemDrive%\Program Files\Common Files\Microsoft BizTalk Adapters for Enterprise Applications\bin.  
  
 Une fois ce schéma de propriété référencé, d'autres propriétés de contexte sont accessibles à divers outils de développement BizTalk (par exemple, forme Assignation du message au sein du Concepteur d'orchestration).  
  
 Pour accéder à une propriété de contexte, vous devez spécifier une des propriétés de contexte disponibles dans l'espace de noms JD Edwards EnterpriseOne. Pour lire la propriété de contexte d'un message reçu d'un port lié à l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, vous devez utiliser la syntaxe Message(JDE.Property) dans une expression. Consultez la gestion de session de l'adaptateur JD Edwards EnterpriseOne pour obtenir la liste des propriétés.  
  
 Dans BizTalk, les messages sont immuables.  
  
### <a name="to-assign-context-property-value"></a>Pour affecter une valeur de propriété de contexte  
  
1.  Créez un message.  
  
2.  Définissez-en le contenu (par exemple, en assignant un message existant).  
  
3.  Définissez les propriétés.  
  
 Pour affecter les propriétés de contexte à un message destiné à un port d'envoi lié à l'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne, utilisez l'opérateur d'assignation de message. Spécifiez ensuite une des propriétés de contexte disponibles dans l'espace de noms JD Edwards EnterpriseOne.  
  
 La syntaxe est la suivante :`Message(JDE.Property) = value;`  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des propriétés de contexte de Message](../core/using-message-context-properties1.md)   
 [Sur la gestion de Session](../core/about-session-management2.md)   
 [Didacticiel : Utilisation de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-enterpriseone.md)