---
title: "Comment créer une requête de recherche d’activité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Builder [BAM portal], creating queries
- queries [BAM], saving
- queries [BAM], creating
- queries [BAM], executing
- Query Builder [BAM portal], executing queries
- Query Builder [BAM portal], opening queries
- Query Builder [BAM portal], saving queries
- queries [BAM], opening
ms.assetid: 7940e47d-10e4-4eb1-b4e6-a8b98461e3a8
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: caca07dd077f171bc35f2e8e61260bb15940685f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-query-in-activity-search"></a>Création d'une requête dans Recherche d'activité
Les utilisateurs finaux du processus d'entreprise et les autres utilisateurs qui ont besoin d'être avertis des événements et états correspondant à leur activité ont recours à des requêtes pour créer des recherches d'activité sur lesquelles baser des alertes.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer d'une vue déployée.  
  
### <a name="to-open-a-query"></a>Pour ouvrir une requête  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.  
  
2.  Dans le **Mes vues** frame du portail, cliquez sur une vue existante pour développer les menus disponibles pour cette vue.  
  
3.  Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.  
  
4.  Cliquez sur une activité dans la liste. La page Recherche d'activité pour l'activité sélectionnée est chargée.  
  
5.  Dans le cadre contenu, en haut de la page, cliquez sur le **Parcourir** bouton pour ouvrir la **choisir un fichier** boîte de dialogue.  
  
6.  Accédez au dossier dans lequel vous avez préalablement enregistré les requêtes.  
  
7.  Cliquez sur Enregistrer requête.  
  
8.  Cliquez sur le **ouvrir** bouton. Charger le chemin d’accès à la requête dans la zone de texte à gauche de la **Parcourir** bouton. Vous pouvez également entrer directement le chemin de la requête dans la zone de texte.  
  
9. Cliquez sur le **ouvrir la requête** bouton à droite de la **Parcourir** bouton.  
  
### <a name="to-construct-a-query"></a>Pour créer une requête  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.  
  
2.  Dans le **Mes vues** frame du portail est une liste de configuré des vues. Sous chaque vue figurent les trois tâches que vous pouvez y effectuer. Si la vue est actuellement réduite, cliquez dessus pour développer la liste des tâches.  
  
3.  Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.  
  
4.  Cliquez sur une activité dans la liste. La page Recherche d'activité pour l'activité sélectionnée est chargée.  
  
5.  Dans le cadre contenu, dans le **requête** , choisissez un champ à partir de la **données d’entreprise** liste déroulante à utiliser pour une comparaison dans la requête.  
  
6.  À partir de la **opérateur** liste déroulante, sélectionnez l’opérateur de comparaison à utiliser.  
  
7.  Dans le **valeur** , entrez la valeur à comparer. Vous pourrez entrer uniquement une valeur adaptée au champ avec lequel effectuer la comparaison. (Si l'élément de données d'entreprise est un champ de date, les données de comparaison sont une date ou une date et une heure formatées selon vos paramètres régionaux.)  
  
8.  Si vous avez des clauses à ajouter à la requête, cliquez sur le **ajouter** bouton à droite de la zone de requête. Une nouvelle ligne est alors ajoutée pour la clause suivante. Vous pouvez choisir de joindre ou non les clauses en utilisant AND ou OR.  
  
    > [!NOTE]
    >  Vous ne pouvez pas regrouper des clauses pour constituer des requêtes plus complexes. Une requête est un ensemble simple de clauses jointes par un opérateur AND ou OR.  
  
    > [!NOTE]
    >  Si vous cliquez sur le bouton précédent pendant ces procédures et que vous recevez un « avertissement : page a expiré, « vous pouvez appuyer sur F5 pour revenir à votre contenu d’origine. Vous devrez éventuellement appuyer plusieurs fois sur F5.  
  
9. Dans le sélecteur de colonne, sélectionnez les données ou les étapes majeures à partir de la **données disponibles et les étapes majeures** zone de liste pour la requête retourner sous forme de données. Il est possible de sélectionner plusieurs éléments adjacents en cliquant sur le premier élément puis, tout en maintenant enfoncée la touche MAJ, sur le dernier élément du groupe à retourner. Vous pouvez également sélectionner plusieurs éléments de la liste en maintenant enfoncée la touche CTRL et en sélectionnant les divers éléments à retourner.  
  
10. Utilisez le  **>>**  bouton pour déplacer les éléments sélectionnés vers le **éléments à afficher** zone de liste. Vous pouvez supprimer des éléments dans cette liste en les sélectionnant et en utilisant le  **<<**  bouton à les replacer dans la zone de liste données et étapes majeures.  
  
11. Une fois que vous avez sélectionné tous les éléments à retourner par la requête, vous pouvez réorganiser les résultats pour déterminer l'ordre d'affichage des colonnes. Pour déplacer une colonne à la première position dans le jeu de données retourné, sélectionnez-le en cliquant dessus et en cliquant sur le **monter** bouton jusqu'à ce qu’il soit en haut de la liste des éléments. De même, pour déplacer un élément à une position postérieure dans le jeu de données retourné, sélectionnez l’élément en cliquant dessus, puis en cliquant sur le **Descendre** bouton jusqu'à ce qu’il se trouve dans la position dans laquelle vous souhaitez afficher.  
  
### <a name="to-save-a-query"></a>Pour enregistrer une requête  
  
1.  Dans le cadre contenu, en haut de la page, cliquez sur le **enregistrer la requête** bouton pour ouvrir la **enregistrer le fichier** boîte de dialogue.  
  
2.  Sur le **télécharger le fichier** boîte de dialogue, cliquez sur le **enregistrer** bouton.  
  
3.  Accédez à l'emplacement où vous souhaitez enregistrer la requête.  
  
4.  Vous pouvez accepter le nom par défaut de la requête ou vous pouvez entrer un nouveau nom dans la **nom de fichier** zone de texte.  
  
5.  Cliquez sur le **enregistrer** bouton.  
  
### <a name="to-execute-a-query"></a>Pour exécuter une requête  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Site Web du portail BAM**.  
  
2.  Dans le **Mes vues** frame du portail, cliquez sur une vue existante pour développer les menus disponibles pour cette vue.  
  
3.  Cliquez sur **recherche d’activité** pour développer la liste des activités disponibles pour la vue.  
  
4.  Cliquez sur une activité dans la liste. La page Recherche d'activité pour l'activité sélectionnée est chargée.  
  
5.  Ouvrez une requête existante ou créez-en une.  
  
6.  Dans le cadre contenu du portail, cliquez sur le **exécuter la requête** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherches d’activité dans le portail BAM](../core/activity-searches-in-the-bam-portal.md)