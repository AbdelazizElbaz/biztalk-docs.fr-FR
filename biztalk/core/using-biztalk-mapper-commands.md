---
title: À l’aide des commandes du Mappeur BizTalk | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 34fea0fb-0609-4571-be49-6ee3f03afe2a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5fd32d865bd08fe1b8b8e7929f313626be3e662
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="using-biztalk-mapper-commands"></a>Utilisation des commandes du Mappeur BizTalk
Lorsque le Mappeur BizTalk devient actif, il ajoute un menu appelé **BizTalk** Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell. Ce menu donne l'accès aux options du Mappeur BizTalk et à leur fonctionnalité. Lorsque le Mappeur BizTalk est actif, le **BizTalk** menu propose des options qui sont spécifiques à l’édition des mappages BizTalk.  
  
 Lorsque c’est possible, le Mappeur BizTalk utilise les options de menu [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] existantes pour les commandes présentant des parallèles évidents avec des fonctionnalités d’application standard. Par exemple, lorsque le Mappeur BizTalk est actif, le **enregistrer** commande sur le **fichier** menu enregistre les modifications apportées à la carte est en cours de modification.  
  
 Le tableau suivant décrit les options comprises dans le Mappeur BizTalk pouvant être utilisées dans le processus de développement des mappages.  
  
|Command<br /><br /> (emplacements de menu, le cas échéant)| Description|  
|--------------------------------------------|-----------------|  
|**Ouvrir un mappage**<br /><br /> (Fichier &#124; ouvrir &#124; fichier...)|Ouvre un mappage BizTalk pour édition dans le Mappeur BizTalk.<br /><br /> Également disponible à partir du menu contextuel dans l'Explorateur de solutions lorsqu'un mappage est sélectionné, ou en double-cliquant sur un mappage dans l'Explorateur de solutions.|  
|**Fermer un mappage**<br /><br /> (Fichier &#124; fermer)|Ferme le Mappeur BizTalk pour le mappage actuel, vous invitant à enregistrer les éventuelles modifications non enregistrées.<br /><br /> Également disponible à l’aide de la fermeture standard ([**X**]) situé dans l’angle supérieur droit de la fenêtre d’édition principale dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|**Nouveau mappage**<br /><br /> (Projet &#124; ajouter &#124; un nouvel élément... &#124; Mappage)|Crée un mappage BizTalk pour le modifier et ouvre le Mappeur BizTalk.<br /><br /> Sélectionnez le modèle de mappage dans le **ajouter un nouvel élément** boîte de dialogue.<br /><br /> Également disponible dans le menu contextuel associé au projet BizTalk dans l’Explorateur de solutions (ajouter &#124; un nouvel élément &#124; carte).|  
|**Ouvrir le schéma Source**<br /><br /> (*dans la vue de l’arborescence du schéma du nouveau mappage uniquement source*)|Permet la sélection du schéma source dans les nouveaux mappages à l’aide de la **sélecteur de Type BizTalk** boîte de dialogue.|  
|**Schéma de Destination ouverte**<br /><br /> (*dans la vue de l’arborescence du schéma du nouveau mappage uniquement destination*)|Permet de sélectionner le schéma de destination dans nouveaux mappages à l’aide de la **sélecteur de Type BizTalk** boîte de dialogue.|  
|**Enregistrer le mappage**<br /><br /> (File &#124; Save map.btm)<br /><br /> (Fichier &#124; enregistrer mappage.btm sous...)<br /><br /> (Fichier &#124; Enregistrer tout)|Enregistre le mappage BizTalk en cours d’édition sous son propre nom, sous un nouveau nom, ou dans le cadre de l'enregistrement de modifications non sauvegardées, respectivement.|  
|**Créer le lien**<br /><br /> *(glisser-déposer uniquement)*|Crée un lien entre des nœuds de schéma dans les vues d’arborescence de schémas source et de destination, ou entre les fonctoids d’une page de grille.<br /><br /> Pour créer un lien :<br /><br /> -En faisant glisser un nœud de schéma vers un autre nœud de schéma dans l’autre arborescence de schéma ou un fonctoid.<br />-En faisant glisser un fonctoid à un nœud de schéma ou à un autre fonctoid.<br /><br /> Vous pouvez créer des liens en faisant glisser des éléments dans les deux directions ; en d'autres termes, vous pouvez démarrer à la source (extrémité gauche) ou à la destination (extrémité droite) d'un lien.<br /><br /> Vous pouvez remplacer une liaison en déplaçant l'un de ses points de terminaison d'un nœud ou fonctoid vers un autre nœud ou fonctoid. Pour plus d’informations, consultez [comment créer des liens](../core/how-to-create-links.md).|  
|**Ajouter le fonctoid**<br /><br /> *(glisser-déposer uniquement)*|Ajoute un fonctoid à la page de grille affichée.<br /><br /> Vous pouvez ajouter un fonctoid à une page de grille en faisant glisser le fonctoid à partir de l'onglet de la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] qui correspond à la catégorie du fonctoid.|  
|**Suppression d’un lien** et **supprimer fonctoid**<br /><br /> (Modifier &#124; supprimer)<br /><br /> (BizTalk &#124; supprimer)|Supprime les liens ou les fonctoids actuellement sélectionnés dans la page de grille affichée, après un message vous invitant à confirmer la suppression.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé aux liens ou aux fonctoids sélectionnés.|  
|**Rechercher un nœud de schéma**<br /><br /> (Modifier &#124; rechercher et remplacer &#124; Rechercher)|Offre une fonction de recherche des noms de nœud dans les vues d'arborescence de schéma, particulièrement utile pour les grands schémas.|  
|**Propriétés**<br /><br /> (Vue &#124; fenêtre Propriétés)<br /><br /> (BizTalk &#124; propriétés)|Donne accès aux propriétés de liens, fonctoids, nœuds de vue d’arborescence de schémas source et de destination, et d’objets de niveau supérieur, tels que les mappages eux-mêmes.<br /><br /> Également disponible dans le menu contextuel associé au lien ou au fonctoid sélectionné, mais pas pour les nœuds des arborescences de schéma. Il est également possible d’afficher la fenêtre Propriétés en appuyant sur la touche F4.|  
|**Ajouter une Page**<br /><br /> (BizTalk &#124; ajouter une Page)|Ajoute une nouvelle page de grille (« couche ») à la vue Grille.<br /><br /> Également disponible dans le menu contextuel associé aux onglets de la page de grille.|  
|**Supprimer la Page**<br /><br /> (BizTalk &#124; supprimer la Page)|Supprime la page de grille affichée, également appelée couche, après un message vous invitant à confirmer la suppression.<br /><br /> Également disponible dans le menu contextuel associé aux onglets de la page de grille.|  
* Réorganiser les Pages **<br /><br /> (BizTalk &#124; réorganiser les Pages)|Permet de réorganiser les pages de grille, également appelées couches, à l’aide de la **réorganiser les Pages** boîte de dialogue.<br /><br /> Également disponible dans le menu contextuel associé aux onglets de la page de grille.|  
|**Renommer la Page**<br /><br /> (BizTalk &#124; renommer la Page)|Permet de renommer la page de grille affichée, également appelée couche.<br /><br /> Également disponible dans le menu contextuel associé aux onglets de la page de grille.|  
|**Développez le nœud d’arborescence**<br /><br /> (BizTalk &#124; développez le nœud d’arborescence)|Développe complètement l’actuellement sélectionné (et au moins partiellement réduit) **schéma**, **groupe**, ou **enregistrement** nœud dans la source ou la vue de l’arborescence du schéma de destination.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné. **Remarque :** dans un grand schéma complexe, lorsque vous cliquez sur **développer le nœud d’arborescence** sur un nœud qui contient les types complexes, certains nœuds du schéma peuvent rester dans l’état réduit. Cela est dû au fait que le processus récurrent ne développe que la première occurrence d'un type complexe donné. Vous devrez développer les autres occurrences manuellement. Ce comportement permet d'optimiser les performances lors du développement de nœuds de grands schémas complexes.|  
|**Réduire le nœud d’arborescence**<br /><br /> (BizTalk &#124; réduire le nœud d’arborescence)|Réduit l’actuellement sélectionné (et au moins partiellement développé) **schéma**, **groupe**, ou **enregistrement** nœud dans la source ou la vue de l’arborescence du schéma de destination.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Aperçu de la grille**<br /><br /> (BizTalk &#124; aperçu de la grille)|Permet de rapide et précise le défilement dans la page de grille affichée à l’aide de la **aperçu de la grille** boîte de dialogue.<br /><br /> Cette option est également disponible dans le menu contextuel associé aux pages de grille.|  
|**Remplacer le schéma**<br /><br /> (BizTalk &#124; remplacer le schéma)|Permet de remplacer la source ou le schéma de destination à l’aide du **sélecteur de Type BizTalk** boîte de dialogue.<br /><br /> Également disponible dans le menu contextuel associé aux vues d’arborescence de schémas source et de destination.|  
|**Options du Mappeur BizTalk**<br /><br /> (Outils &#124; Options &#124; le Mappeur BizTalk)|Permet de configurer différentes couleurs dans la vue Grille, pour la sélection, les liens, la grille et l’arrière-plan. Vous pouvez également modifier la police utilisée dans l'affichage du nœud de schéma avec cette option.|  
  
 Le tableau suivant décrit des options de mappage supplémentaires disponibles dans le menu contextuel associé au mappage sélectionné dans l'Explorateur de solutions.  
  
|Option de schéma| Description|  
|--------------------|-----------------|  
|**Ouvrir**|Ouvre le mappage sélectionné dans le Mappeur BizTalk.<br /><br /> Vous pouvez également double-cliquer sur un mappage pour l’ouvrir dans le Mappeur BizTalk.|  
|**Ouvrir avec**|Permet d’ouvrir le mappage sélectionné dans divers éditeurs XML, y compris le Mappeur BizTalk.|  
|**Tester le mappage**|Teste le mappage sélectionné.|  
|**Valider le mappage**|Valide le mappage.|  
|**Déboguer le mappage**|Si le mappage est compilé sans erreur, Déboguer le mappage lance le débogueur XSLT. Celui-ci vous permet de parcourir le XSLT, comme tout autre débogueur Visual Studio.|  
|**Exclure du projet**|Retire le mappage actuellement sélectionné du projet BizTalk actuel.<br /><br /> Utilisez le **ajouter &#124; élément existant** commande pour ajouter de nouveau un mappage précédemment exclu du projet BizTalk actuel.|  
|**Cut, Copy, Paste**|Ces options vous permettent d’effectuer les opérations standard de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], telles que couper, copier et coller, sur l'ensemble des mappages figurant dans un projet BizTalk.<br /><br /> Vous pouvez également couper, copier et coller des éléments de mappage tels que des liens et/ou des fonctoids. Pour plus d’informations, consultez [comment copier, couper et coller un fonctoid](../core/how-to-copy-cut-and-paste-a-functoid.md) et [comment copier, couper et collage de liens et fonctoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).|  
|**Delete**|Supprime de façon définitive le mappage sélectionné, après un message vous invitant à confirmer la suppression.|  
|**Rename**|Permet de renommer le mappage sélectionné.|  
|**Propriétés**|Affiche les propriétés du mappage sélectionné dans la fenêtre Propriétés.|  
  
## <a name="see-also"></a>Voir aussi  
 [Raccourcis clavier du Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md)