---
title: "Ajout de fonctoids de base à un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a81fb73-cccf-4f74-af92-39e4af13e255
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23a6748a5ce128ef13ce012412e36570e4e01eba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-basic-functoids-to-a-map"></a>Ajout d'un fonctoid de base à un mappage
De nombreux fonctoids sont très simples à utiliser. Ils sont désignés ici des fonctoids de base pour les différencier des fonctoids dans la **avancé** catégorie. Les fonctoids de base regroupent les catégories restantes de fonctoids, telles que Conversion, Cumulé, Base de données, Date et heure, Logique, Mathématique, Scientifique et Chaîne.  
  
 En général, les fonctoids de base utilisent des types simples tels que des nombres ou des chaînes pour leurs liens d'entrée et de sortie.  
  
 Pour utiliser un fonctoid de base, il faut l'ajouter à une page de grille, créer des liens d'entrée vers ce fonctoid à partir de la gauche et créer vers la droite un lien de sortie à partir de ce dernier. Cette rubrique contient des instructions détaillées concernant ce type d'opérations.  
  
## <a name="add-a-basic-functoid-to-a-map"></a>Ajouter un fonctoid de base à un mappage  
  
1.  Avec la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] active, cliquez sur l'onglet approprié pour sélectionner la catégorie du fonctoid que vous souhaitez utiliser.  
  
     La liste des fonctoids disponibles dans la catégorie choisie s’affiche.  
  
2.  Faites glisser le fonctoid que vous souhaitez utiliser de la boîte à outils vers l'emplacement approprié d'une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous voulez le placer sur une autre page de grille, vous devez d'abord afficher cette page.  
  
    > [!NOTE]
    >  Si vous construisez un mappage de l’utilisation conjointe de plusieurs fonctoids, vous devez envisager de leur gauche relatif à la sélection élective de droite. Les fonctoids sont exécutés de la gauche vers la droite. La sortie d'un fonctoid ne peut être placée qu'en entrée d'un autre fonctoid qui se trouve à sa droite.  
  
## <a name="create-input-links-to-a-basic-functoid"></a>Créer des liens d’entrée vers un fonctoid de base  
  
1.  Faites glisser un nœud d'enregistrement ou de champ du schéma source vers le fonctoid de base de la page de grille affichée.  
  
     **- Ou -**  
  
     Dans la page de grille qui s'affiche, faites glisser un autre fonctoid, situé plus à gauche, vers le fonctoid de base avec lequel vous souhaitez établir un lien d'entrée.  
  
     **- Ou -**  
  
     Faites glisser le fonctoid de base de la page de grille affichée vers un nœud d'enregistrement ou de champ du schéma source.  
  
     **- Ou -**  
  
     Dans la page de grille qui s'affiche, faites glisser le fonctoid de base avec lequel vous souhaitez établir un lien d'entrée vers un autre fonctoid, situé plus à gauche.  
  
    > [!NOTE]
    >  Contrairement au point de terminaison fixe du lien, le point de terminaison mobile du lien prend, pendant l'opération de glisser-déposer, la forme d'une croix pour cibler plus précisément le deuxième point de terminaison. Si vous pointez le point de terminaison mobile du lien sur un objet qui n'est pas un deuxième point de terminaison approprié pour le lien (ce qui peut arriver en cas d'incompatibilité de types de données), la croix se transforme en une icône constituée d'un cercle barré d'un trait diagonal.  
  
2.  Répétez l'étape 1 le nombre de fois nécessaire pour établir l'ensemble des liens d'entrée (mais peut-être pas l'ensemble des paramètres d'entrée) vers le fonctoid de base.  
  
    > [!NOTE]
    >  Quelques fonctoids ne requièrent aucun lien d'entrée. Par exemple, le **Date**, **temps**, et **Date et heure** fonctoids dans le **Date et heure** catégorie de fonctoid Indiquez la date actuelle, heure, ou la date et heure, respectivement, à laquelle un message d’instance est en cours de traitement. Ils ne nécessitent donc aucun paramètre d'entrée à partir du schéma source.  
  
    > [!NOTE]
    >  L’ordre des paramètres d’entrée de nombreux fonctoids est important, comme indiqué dans la rubrique de référence de fonctoids correspondante (voir **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]). L'ordre dans lequel vous créez des liens détermine l'ordre des paramètres d'entrée du fonctoid. Pour plus d’informations sur les propriétés des fonctoids et en spécifiant l’ordre des paramètres d’entrée du fonctoid, consultez [modification des propriétés de fonctoid et les paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md). Pour plus d’informations sur la façon de configurer les paramètres d’entrée d’un fonctoid, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).  
  
    > [!NOTE]
    >  Avant de commencer à établir des liens, assurez-vous que les fonctoids ou que le nœud de schéma source que vous souhaitez lier sont visibles dans la page de grille ou la fenêtre de schéma source affichée.  
  
## <a name="create-the-output-link-from-a-basic-functoid"></a>Créer le lien de sortie à partir d’un fonctoid de base  
  
1.  Faites glisser un nœud d'enregistrement ou de champ du schéma de destination vers le fonctoid de base dans la page de grille affichée.  
  
     **- Ou -**  
  
     Dans la page de grille affichée, faites glisser un autre fonctoid, situé à droite, vers le fonctoid de base avec lequel vous souhaitez établir le lien de sortie.  
  
     **- Ou -**  
  
     Faites glisser le fonctoid de base de la page de grille affichée vers un nœud d'enregistrement ou de champ du schéma de destination.  
  
     **- Ou -**  
  
2.  Dans la page de grille affichée, faites glisser le fonctoid de base avec lequel vous souhaitez établir un lien de sortie vers un autre fonctoid, situé à sa droite.  
  
    > [!NOTE]
    >  Avant de commencer l'opération de connexion, assurez-vous que les fonctoids et que le nœud de schéma source que vous souhaitez lier sont déjà visibles respectivement dans la page de grille affichée et la fenêtre de schéma source.  
  
    > [!NOTE]
    >  La connexion de fonctoids tente toujours de désactiver les liens inappropriés, notamment les liens dont les types de données source et cible ne correspondent pas.  
  
    > [!NOTE]
    >  Contrairement au point de terminaison fixe, le point de terminaison mobile du lien, pendant l'opération de glisser-déposer, prend la forme d'une croix pour cibler plus précisément le deuxième point de terminaison. Si vous pointez le point de terminaison mobile du lien sur un objet qui n'est pas un deuxième point de terminaison approprié pour le lien (ce qui peut arriver en cas d'incompatibilité de types de données), la croix se transforme en une icône constituée d'un cercle barré d'un trait diagonal.  
  
## <a name="see-also"></a>Voir aussi  
**Référence du fonctoid**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]