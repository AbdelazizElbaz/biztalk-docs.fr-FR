---
title: "Création de mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc9f8ad1-4aad-4866-8aa4-4877fdc5e5f9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00121334b076ed4c705e7b440c75c1347e4208c9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-maps"></a>Création de mappages
L’interface utilisateur principale du Mappeur BizTalk s’affiche sous un onglet dans le [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition. Cet affichage se compose de trois volets. Le volet gauche affiche le schéma source sous forme d'arborescence. Le volet droit affiche le schéma de destination sous forme d'arborescence. Le volet central affiche la grille, composée de plusieurs pages. Pour indiquer comment vous voulez mapper des données du schéma source vers le schéma de destination, vous tracez des lignes entre les enregistrements et les champs que vous voulez mapper. Ces lignes sont appelées *liens*, et ils sont la façon la plus simple pour spécifier le mappage de données. Pour plus d’informations sur la liaison d’enregistrements et champs, consultez [des liens dans les mappages](../core/links-in-maps.md).  
  
 Si vous souhaitez implémenter des méthodes de mappage plus avancées, vous pouvez utiliser des fonctoids. Les fonctoids sont des outils disponibles dans la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] du Mappeur BizTalk. Ils permettent de créer des mappages qui autorisent la réalisation d'opérations plus complexes telles que  
  
-   additionner les valeurs de deux champs d'un schéma source et placer le résultat dans un champ du schéma de destination ;  
  
-   calculer la moyenne d'un champ d'un enregistrement de boucle et placer le résultat dans un champ du schéma de destination ;  
  
-   écrire un script personnalisé pour manipuler les données d'instance d'une manière adaptée à vos besoins professionnels.  
  
 Pour plus d’informations sur les fonctoids, consultez [fonctoids dans les mappages](../core/functoids-in-maps.md).  
  
 Le Mappeur BizTalk peut prendre en charge divers scénarios de mappage, des relations parent-enfant simples jusqu'au bouclage complexe d'enregistrements et de hiérarchies. Tenez compte des remarques suivantes lorsque vous créez des mappages :  
  
-   Le Mappeur BizTalk Mapper ne prend en charge ni la fusion ni le tri.  
  
-   Si les structures des schémas sources et cibles sont extrêmement différentes, il est possible que la transformation ne puisse être effectuée dans un seul mappage. Un double passage pourrait être requis.  
  
-   **Bouclage** fonctoids sont flexibles et puissants, mais vous ne pourrez pas interrompre l’itération lorsqu’une modification de valeur sur le schéma source est détectée pour démarrer l’itération suivante de la boucle cible.  
  
-   Vous pouvez déclarer une variable en dehors de la méthode dans un **script** fonctoid, ce qui entraîne la variable en cours dans l’étendue de la durée de vie de la carte. Par conséquent, vous pouvez utiliser la **script** fonctoid pour maintenir les valeurs entre les zones de portée de la transformation.  
  
 Toutes les données traitées par [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au moment de l’exécution doit être au format XML. Toutes les données non XML doivent être converties dans un format XML équivalent avant le mappage. De même, au terme du processus de mappage, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le résultat d'une opération de mappage pour créer un format de fichier reconnu par le partenaire commercial ou par l'application auxquels les données sont envoyées.  
  
 Le Mappeur BizTalk inclut un compilateur. Cet outil génère le langage de transformation de feuille de style extensible (XSLT) requis pour transformer ou convertir des messages d'instance d'entrée en messages d'instance de sortie.  
  
 Cette section fournit des informations spécifiques aux tâches d'utilisation du Mappeur BizTalk pour créer le mappage entre deux schémas. Elle part de l'hypothèse que le Mappeur BizTalk est ouvert et que vous avez choisi vos schémas source et de destination.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Gestion de mappages dans des projets](../core/managing-maps-within-projects.md)  
  
-   [Utilisation de liens pour spécifier des mappages d’enregistrements et de champs](../core/using-links-to-specify-record-and-field-mappings.md)  
  
-   [Utilisation de fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md)  
  
-   [Comment créer un mappage sans mappages](../core/how-to-create-a-map-without-maps.md)  
  
-   [Gérer le comportement du mappeur par défaut à l’aide \<mapsource\>](../core/managing-default-mapper-behavior-using-mapsource.md)