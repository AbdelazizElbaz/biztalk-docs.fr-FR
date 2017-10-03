---
title: "Comment définir les propriétés d’un nœud | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0c79eac-d9ba-45e2-a6e9-770b2bcb2067
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13dc0f13814808a69c4c4b9c3976e9047acde5b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-node-properties"></a>Comment définir les propriétés de nœud
Après avoir inséré un nœud dans un schéma BizTalk, vous devrez souvent modifier ses propriétés par rapport à leurs valeurs par défaut. Chaque type de nœud possède un ensemble distinct de propriétés. Dans chacun de ces ensembles, les paramètres d'une propriété peuvent affecter la disponibilité des autres propriétés. Par exemple, avant de définir la **Default Wrap Character** propriété de la **schéma** nœud, vous devez définir le **Default Wrap Character Type** propriété soit **Caractère** ou **hexadécimal**, ce qui permet l’établissement le format dans lequel vous avez l’intention de représenter la propriété précédente. En outre, ces propriétés n’est disponible, ni l’ensemble de **analyser** catégorie de propriété à laquelle ils appartiennent, sauf si **Extension de fichier plat** est activé à l’aide de la **l’éditeur de schéma Extensions** propriété.  

 Les propriétés de nœud sont nombreuses et peuvent être complexes, comme l'est le langage XSD (XML Schema Definition) qu'elles prennent en charge. Cette rubrique se borne à décrire brièvement les étapes générales nécessaires à l'examen et à la définition de propriétés de nœud. Pour plus d’informations sur ces propriétés, y compris, par exemple, pour plus d’informations sur leur valeur par défaut et les valeurs autorisées, consultez la **référence du schéma de propriété**. Pour encore plus d’informations sur les concepts XSD et les éléments qui sous-tendent la plupart de ces propriétés, reportez-vous directement aux informations sur les [XSD sur le Web](../core/xsd-resources-on-the-web.md).  

Plus d’informations sur ces propriétés et la référence du schéma de propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].

  
## <a name="examine-a-node-property-value"></a>Examiner une valeur de propriété de nœud  
  
1.  Dans l'Éditeur BizTalk, ouvrez le schéma qui contient la propriété que vous voulez examiner et sélectionnez le nœud qui contient cette propriété.  
  
2.  Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
3.  Si nécessaire, faites défiler la fenêtre Propriétés pour rechercher la propriété qui vous intéresse et notez sa valeur.  
  
     Les boutons du haut de la fenêtre Propriétés permettent de modifier le mode de tri des propriétés : alphabétique dans chacune de leurs catégories ou alphabétique sans tenir compte (ou sans affichage) de leurs catégories.  
  
## <a name="set-a-node-property-value"></a>Valeur de propriété de nœud  
  
1.  Dans l'Éditeur BizTalk, ouvrez le schéma qui contient la propriété que vous voulez définir et sélectionnez le nœud qui contient cette propriété.  
  
2.  Si nécessaire, appuyez sur F4 pour ouvrir la fenêtre Propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
3.  Si nécessaire, faites défiler la fenêtre Propriétés pour rechercher la propriété qui vous intéresse.  
  
     Les boutons du haut de la fenêtre Propriétés permettent de modifier le mode de tri des propriétés : alphabétique dans chacune de leurs catégories ou alphabétique sans tenir compte (ou sans affichage) de leurs catégories.  
  
4.  Définissez la valeur de la propriété dans le champ de valeur situé à droite du nom de la propriété. Selon le type de cette dernière, vous pouvez taper une valeur ou en choisir une dans la liste déroulante qui s'affiche lorsque le champ de valeur est sélectionné. Certaines propriétés permettent de procéder d'une manière ou d'une autre. Certaines propriétés affichent les points de suspension (**...** ) bouton cliquer pour ouvrir une boîte de dialogue dans laquelle des valeurs, telles que des collections plus compliquées peut être définie.  
  
5.  Si vous avez tapé une nouvelle valeur pour la propriété, terminez en appuyant sur ENTRÉE.  
  
##  <a name="clear-a-node-property-value"></a>Effacer une valeur de propriété de nœud  
  
1.  Sélectionnez le nœud contenant la propriété qui vous intéresse.  
  
2.  Dans la fenêtre Propriétés, double-cliquez sur la valeur de propriété que vous souhaitez effacer, avec le bouton droit de la valeur de propriété, puis cliquez sur **supprimer**.  
  
## <a name="restore-a-node-property-to-its-default-value"></a>Restauration d’une propriété de nœud à sa valeur par défaut  
  
1.  Sélectionnez le nœud contenant la propriété qui vous intéresse.  
  
2.  Dans la fenêtre Propriétés, cliquez sur le nom de propriété que vous souhaitez rétablir la valeur par défaut, puis cliquez sur **réinitialiser**.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des nœuds existants](../core/working-with-existing-nodes.md)