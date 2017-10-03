---
title: "Génération d’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14060dca-5e14-474a-bf2c-4e8bc56e3c61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46bd3d2bc6852ec0c73fbbe4ffc55924a8012ce5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-generation"></a>Génération d’instance
L’Éditeur BizTalk appelle la **IInstanceGenerator.GenerateInstance** méthode d’extension lorsque les conditions suivantes sont remplies :  
  
-   L’extension est définie comme norme à l’aide de la **Standard** propriété de la **schéma** nœud.  
  
-   Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **Type sortie générer l’Instance** est définie sur **natif.**  
  
-   Sur le **Pages de propriétés** boîte de dialogue associé au schéma, le **nom de fichier de sortie Instance** est définie sur le nom du fichier qui sera enregistré dans l’instance de sortie.  
  
> [!NOTE]
>  Si le **nom de fichier de sortie Instance** propriété n’est pas définie, un nom de fichier par défaut dans un dossier temporaire est utilisé pour le message d’instance généré et un lien vers celle-ci est fourni dans la fenêtre Sortie.  
  
 Avant du **IInstanceValidator.ValidateInstance** méthode est appelée, l’Éditeur BizTalk génère un message d’instance XML exemple et elle passe ensuite et le fichier spécifié dans le **nom de fichier de sortie Instance** propriété ou un nom de fichier par défaut à cette méthode.  
  
 En cas d’erreurs, les messages d’erreur sont retournées sous forme de tableau de **IValidationInfo** objets et s’affichent dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre liste des tâches.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension de l’Éditeur BizTalk](../core/extending-biztalk-editor.md)