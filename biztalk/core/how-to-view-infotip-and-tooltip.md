---
title: Comment afficher des info-bulles | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5621bd0a-7028-43fc-b6e8-74a528129285
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06aba645f94b87e0a7951d9c8264056262a12a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-view-infotip-and-tooltip"></a>Affichage des info-bulles
Lorsque vous déplacez le curseur sur un élément de mappage sans cliquer dessus, une info-bulle comportant des informations utiles sur cet élément s'affiche.  
  
 Le Mappeur BizTalk utilise deux types d'info-bulles.  
  
-   **Info-bulles** sont affichés pour les fonctoids ou des liens. Lorsque vous configurez des étiquettes ou des commentaires pour des fonctoids ou des liens, ceux-ci apparaissent dans des info-bulles dans la page de la grille. En outre, lorsque la valeur de texte pour les propriétés dépasse l’affichage de la **grille des propriétés**, l’info-bulle s’affiche.  
  
-   **Info-bulles** sont affichées pour les nœuds de schéma partiellement/intégralement masqués à partir de l’alignement actuel dans la vue grille.  
  
 Pour les étiquettes de lien, seuls les 256 premiers caractères sont conservés. L'info-bulle affiche l'intégralité de l'étiquette. Pour les fonctoids, l'étiquette peut contenir jusqu'à 256 caractères et les commentaires sont limités à 1 024 caractères. Le texte des commentaires est tronqué de façon à n'afficher que les 256 premiers caractères du commentaire.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour afficher les info-bulles, vérifiez que le Mappeur BizTalk est en cours d'exécution.  
  
## <a name="to-view-the-infotip"></a>Pour afficher l'info-bulle  
 Lorsque vous déplacez le curseur sur un fonctoid, l'info-bulle affiche des informations sur le nom, l'étiquette et les commentaires du fonctoid, ainsi que sur les paramètres d'entrée (le cas échéant). Pour un **script** fonctoid, l’info-bulle affiche les premières lignes de code.  
  
 L'info-bulle d'un lien affiche les informations suivantes :  
  
-   étiquette du lien, si celle-ci est définie ;  
  
-   **À partir de : connexion à la source**. Si la connexion source est un élément de schéma, l'info-bulle indique le nom de l'élément. S'il s'agit d'un fonctoid, elle indique le nom du fonctoid ;  
  
-   **À : connexion de destination**. Si la connexion de destination est un élément de schéma, l'info-bulle indique le nom de l'élément. S'il s'agit d'un fonctoid, l'info-bulle indique le nom du fonctoid.  
  
 Si les champs dans le **grille des propriétés** contiennent du texte qui dépasse la zone d’affichage, déplacez la souris sur le champ. L'info-bulle affiche alors l'intégralité du texte.  
  
 L’illustration suivante montre les info-bulles d’un fonctoid, lien et la **grille des propriétés**.  
  
 ![Info-bulle pour le fonctoid, lien et étiquette](../core/media/viewing-infotips.gif "Viewing_infotips")  
  
## <a name="to-view-the-tooltip"></a>Pour afficher l’info-bulle  
 Lorsque vos schémas sources et/ou de destination sont trop grands, votre mappage peut s'étendre verticalement. Certains nœuds du schéma peuvent alors être partiellement masqués. Dans ce cas, vous pouvez afficher des info-bulles en déplaçant le curseur sur ces nœuds.  
  
 La figure suivante montre l'info-bulle d'un nœud de schéma cible partiellement masqué.  
  
 ![Info-bulle à un nœud de schéma](../core/media/viewing-tooltips.gif "Viewing_tooltips")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)