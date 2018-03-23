---
title: À l’aide des commandes de l’Éditeur BizTalk | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e216ae5d-5bad-48ef-87d1-8aa8ee20179b
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1ae30305f5e23e99b5a0bc76cba9bfc7f451b03
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="use-biztalk-editor-commands"></a>Utilisez les commandes de l’Éditeur BizTalk

## <a name="overview"></a>Vue d'ensemble
Lorsque l’Éditeur BizTalk devient actif, il ajoute un menu appelé **BizTalk** à la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] shell. Ce menu donne l'accès aux options de l'Éditeur BizTalk et à leur fonctionnalité. Lorsque l’Éditeur BizTalk est actif, le **BizTalk** menu propose des options qui sont spécifiques à l’édition des schémas BizTalk.  
  
 De plus, lorsque cela est possible, l'Éditeur BizTalk utilise les options de menu [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] existantes pour les options présentant des parallèles évidents avec des fonctionnalités d'application standard. Par exemple, lorsque l’Éditeur BizTalk est actif, le **enregistrer** commande sur le **fichier** menu enregistre les modifications dans le schéma est en cours de modification.  
  
## <a name="commands-list"></a>Liste de commandes
 Le tableau suivant décrit les options comprises dans l'Éditeur BizTalk qui peuvent être utilisées dans le processus de développement des schémas.  
  
|Command<br /><br /> (emplacements de menu)| Description|  
|------------------------------------|-----------------|  
|**Ouvrir le schéma**<br /><br /> (Fichier &#124; ouvrir &#124; fichier...)|Ouvre un schéma BizTalk pour édition dans l'Éditeur BizTalk.<br /><br /> Également disponible à partir du menu contextuel dans l'Explorateur de solutions lorsqu'un schéma est sélectionné, ou en double-cliquant sur un schéma dans l'Explorateur de solutions.|  
|**Fermer le schéma**<br /><br /> (Fichier &#124; fermer)|Ferme l'Éditeur BizTalk pour le schéma actuel, vous invitant à enregistrer les éventuelles modifications non enregistrées.<br /><br /> Également disponible à l'aide du bouton de fermeture standard situé dans l'angle supérieur droit de la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|**Nouveau schéma**<br /><br /> (Projet &#124; ajouter un nouvel élément... &#124; Schéma)|Crée un schéma BizTalk pour édition et ouvre l'Éditeur BizTalk.<br /><br /> Également disponible dans le menu contextuel associé au projet BizTalk dans l’Explorateur de solutions (ajouter &#124; un nouvel élément).|  
|**Enregistrer le schéma**<br /><br /> (Fichier &#124; enregistrer schema.xsd)<br /><br /> (Fichier &#124; enregistrer schema.xsd sous...)<br /><br /> (Fichier &#124; Enregistrer tout)|Enregistre le schéma BizTalk en cours d’édition sous son propre nom, sous un nouveau nom, ou dans le cadre de l'enregistrement de modifications non sauvegardées, respectivement.|  
|**Couper, copier et coller le nœud**<br /><br /> (Modifier &#124; couper, Edition &#124; copier, modifier &#124; coller)|Permet de **schéma** arborescence de nœuds à être déplacés et dupliqués dans le schéma.<br /><br /> Le cas échéant, ces commandes sont également disponibles dans le menu contextuel du nœud sélectionné, à l’aide de la norme couper, copier et coller des touches de raccourci : CTRL + X, CTRL + C et CTRL + V.|  
|**Supprimer un nœud**<br /><br /> (Modifier &#124; supprimer)<br /><br /> (BizTalk &#124; supprimer)|Supprime le nœud actuellement sélectionné dans l'arborescence de schéma, après l'affichage d'un message vous invitant à confirmer la suppression.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Trouver le nœud**<br /><br /> (Modifier &#124; rechercher et remplacer &#124; recherche rapide)|Offre une fonction de recherche des noms de nœud dans la vue d'arborescence de schéma, particulièrement utile pour les grands schémas.|  
|**Propriétés**<br /><br /> (Vue &#124; fenêtre Propriétés)<br /><br /> (BizTalk &#124; propriétés)|Donne accès aux propriétés des nœuds de vue d'arborescence de schéma et aux objets de niveau supérieur tels que les schémas eux-mêmes.<br /><br /> Également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Insérer des nœuds de schéma**<br /><br /> (BizTalk &#124; Insert Schema Node &#124; *)|Offre un moyen d'insérer différents types de nœuds dans la vue d'arborescence de schéma. Pour plus d’informations sur les types de nœuds qui peuvent être ajoutées, consultez [représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md).<br /><br /> Le cas échéant, ces options sont également disponibles dans le menu contextuel associé au nœud sélectionné.|  
|**Promote**<br /><br /> (BizTalk &#124; promouvoir &#124; *)|Offre divers moyens de promouvoir des propriétés.<br /><br /> Également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Développez le nœud de schéma**<br /><br /> (BizTalk &#124; développez le nœud de schéma)|Développe complètement le nœud actuellement sélectionné (et au moins partiellement réduit) dans la vue d'arborescence de schéma.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Réduire le nœud de schéma**<br /><br /> (BizTalk &#124; réduire le nœud de schéma)|Réduit complètement le nœud actuellement sélectionné (et au moins partiellement développé) dans la vue d'arborescence de schéma.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Actualiser XSD**<br /><br /> (BizTalk &#124; actualiser XSD)|Actualise la vue XSD, qui peut être définie pour ne pas actualiser automatiquement en sélectionnant le **désactiver l’actualisation automatique** case à cocher sous la vue XSD.<br /><br /> Cette commande est également disponible dans le menu contextuel du nœud sélectionné et en cliquant sur **Actualiser** sous la vue XSD.|  
|**Rename**<br /><br /> (BizTalk &#124; renommer)|Permet de **enregistrement**, **attribut de champ**, et **élément de champ** nœuds doit être renommé en place, au sein de l’arborescence du schéma.<br /><br /> Cette commande revient à modifier le **nom de nœud** propriété du nœud sélectionné.<br /><br /> Le cas échéant, cette option est également disponible dans le menu contextuel associé au nœud sélectionné.|  
|**Options de l’Éditeur BizTalk**<br /><br /> (Outils &#124; Options &#124; l’Éditeur BizTalk)|Permet la configuration de boîtes de dialogue de confirmation (activées ou désactivées) ainsi que l'ajustement de la couleur d'arrière-plan et de la police.|  
  
 Le tableau suivant décrit des options de schéma supplémentaires disponibles dans le menu contextuel associé au schéma sélectionné dans l'Explorateur de solutions.  
  
|Option de schéma| Description|  
|--------------------|-----------------|  
|**Ouvrir**|Ouvre le schéma sélectionné dans l'Éditeur BizTalk.|  
|**Ouvrir avec**|Permet d'ouvrir le schéma sélectionné dans divers éditeurs XSD, y compris l'Éditeur BizTalk.|  
|**Valider le schéma**|Valide le schéma sélectionné.|  
|**Valider l’Instance**|Valide l’instance spécifiée par le **nom d’Instance d’entrée** propriété dans Visual Studio **propriétés** fenêtre par rapport au schéma sélectionné.|  
|**Générer l’Instance**|Génère une instance du schéma sélectionné en utilisant le nom de fichier spécifié par le **nom de fichier de sortie Instance** propriété dans Visual Studio **propriétés** fenêtre.<br /><br /> Si aucun nom n'est spécifié pour l'instance de sortie générée, un nom de fichier par défaut sera utilisé. Ce nom est celui que vous obtenez en faisant précéder la chaîne « _output.xml » par le nom du fichier de schéma dans le dossier _SchemaData d'un dossier temporaire de votre dossier Documents and Settings.|  
|**Afficher le Code**|Affiche le schéma XSD sous-jacent.|  
|**Concepteur de vue**|Ouvre le schéma dans le Concepteur de schémas XML [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].|  
|**Exclure du projet**|Retire le schéma actuellement sélectionné du projet BizTalk actuel.<br /><br /> Utilisez le **ajouter un élément existant** commande pour ajouter de nouveau un schéma précédemment exclu du projet BizTalk actuel.|  
|**Cut, Copy, Paste**|Ces options vous permettent d’effectuer les opérations standard de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], telles que couper, copier et coller, sur l'ensemble des schémas figurant dans un projet BizTalk.|  
|**Delete**|Supprime de façon définitive le schéma sélectionné, après un message vous invitant à confirmer la suppression.|  
|**Rename**|Permet de renommer directement le schéma sélectionné.|  
|**Propriétés**|Ouvre le Visual Studio **propriétés** fenêtre pour le schéma actuellement sélectionné, dans lequel certaines des propriétés du schéma peuvent être examinées et définies. <br/><br/>**Remarque :** autres propriétés du schéma sont examinées et définies le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés lorsque le schéma est sélectionné. Propriétés qui sont définies dans le **propriétés** sont celles pour lesquelles des valeurs différentes peuvent être pertinentes pour le même schéma lorsqu’il est utilisé dans plusieurs projets BizTalk. <br /><br /> Pour plus d’informations sur la définition des propriétés de schéma et les propriétés de schéma, consultez [fichier de schéma de paramètres et les propriétés d’élément de schéma](../core/how-to-set-schema-file-and-schema-item-properties.md) et **propriétés d’un fichier de schéma** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)