---
title: "L’enregistrement, renommage et fermeture des schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65e15d9e-40ae-4850-9c13-88033cb3b3bb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a4ad59760d6efddcfe946c0ee13c26ee0f8ca1d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-save-rename-and-close-schemas"></a>Enregistrement, renommage et fermeture des schémas
Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les schémas sont des fichiers de langage XSD (XML Schema Definition). Ils résident sur le système de fichiers avec l'extension .xsd. Lorsque vous utilisez l'Éditeur BizTalk pour développer des schémas, vous devez systématiquement enregistrer et fermer les fichiers de schéma et devez parfois les renommer. Cette rubrique indique les étapes requises pour effectuer ces opérations de base.  
  
### <a name="to-save-a-schema"></a>Pour enregistrer un schéma  
  
1.  Si nécessaire, activez l'Éditeur BizTalk pour le schéma à enregistrer en cliquant sur l'onglet approprié en haut de la fenêtre d'édition principale dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Sur le **fichier** menu, cliquez sur **enregistrer  *\<nom de schéma >***.  
  
     Si le schéma comportait des modifications non enregistrées, son nom tel qu'il s'affiche dans l'onglet en haut de la fenêtre d'édition principale ne se terminera plus par un astérisque (*). L'astérisque est en effet utilisé pour attirer l'attention sur des modifications non enregistrées.  
  
> [!NOTE]
>  Vous pouvez enregistrer le schéma sous un nouveau nom en cliquant sur **enregistrer  *\<nom de schéma >* en tant que** sur la **fichier** menu.  
  
> [!NOTE]
>  Vous pouvez enregistrer le schéma en tant que partie de l’enregistrement de tous les éléments modifiés dans le projet en cliquant sur **Enregistrer tout** sur la **fichier** menu.  
  
#### <a name="to-rename-a-schema"></a>Pour renommer un schéma  
  
1.  Dans l’Explorateur de solutions, cliquez sur le schéma que vous souhaitez renommer, puis cliquez sur **renommer**.  
  
2.  Dans la zone d'édition qui apparaît à l'emplacement du schéma dans l'Explorateur de solutions, tapez le nouveau nom du schéma ou modifiez son nom actuel, puis appuyez sur ENTRÉE.  
  
> [!NOTE]
>  Vous pouvez également modifier le **nom de Type** du schéma lorsque vous renommez. Vous modifiez le **nom de Type** en sélectionnant le **schéma** dans l’Explorateur de solutions et entrer le nouveau nom dans la **nom de Type** dans la fenêtre Propriétés.  
  
> [!IMPORTANT]
>  Ne renommez pas un schéma utilisé par un autre schéma. Cela concerne les schémas inclus, importés ou redéfinis par d'autres schémas, ainsi que les schémas de propriété pour lesquels des promotions ont déjà été établies. Si vous ne respectez pas cette règle, le schéma utilisé ne pourra pas retrouver le schéma renommé, car le nom qu'il contient ne sera plus exact.  
  
> [!NOTE]
>  Certains noms de fichiers de membre de projet tels que les fichiers de schéma peuvent provoquer des erreurs de compilation ultérieures en raison de conflits avec des noms réservés C#  et des noms de type et d'espace de noms .NET Framework (« Système » par exemple). schema.xsd, XmlContent et RootNodes sont des exemples de schémas. C’est parce que le **nom de Type** propriété valeur par défaut est la partie de base (sans extension) de la **nom de fichier** propriété. Vous pouvez contourner ce type d’erreur de compilation en donnant explicitement la valeur de la **nom de Type** propriété à un élément qui n’est pas en conflit.  
  
#### <a name="to-close-a-schema"></a>Pour fermer un schéma  
  
1.  Si nécessaire, activez l'Éditeur BizTalk pour le schéma à fermer en cliquant sur l'onglet approprié en haut de la fenêtre d'édition principale dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
2.  Dans le menu **Fichier** , cliquez sur **Fermer**.  
  
     L'Éditeur BizTalk se ferme pour le schéma qui a été fermé.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des schémas dans des projets](../core/managing-schemas-within-projects.md)