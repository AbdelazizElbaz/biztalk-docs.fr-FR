---
title: "L’ajout de bouclage de Table et de fonctoids Extracteur à un mappage de Table | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c837ab8-55db-471a-af26-9fbd0497d7d4
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4b7844260b7ac5ab29f204a538e61cb99b0d017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-table-looping-and-table-extractor-functoids-to-a-map"></a>Ajout de fonctoids Bouclage de table et Extracteur de table à un mappage
Le **bouclage de Table** et **extracteur de Table** fonctoids sont utilisés ensemble. Le **bouclage de Table** le fonctoid ne comporte une table interne que vous configurez. Pour chaque d’entrée d’enregistrement ou un champ, la **bouclage de Table** fonctoid génère les lignes de la table, une à la fois. Le **extracteur de Table** fonctoid extrait l’élément désiré à partir d’une ligne et le transmet le message d’instance de sortie.  
  
 Pour obtenir des informations conceptuelles sur le **bouclage de Table** et **extracteur de Table** fonctoids, consultez [bouclage de Table et de fonctoids Extracteur de Table](../core/table-looping-and-table-extractor-functoids.md).  
  
### <a name="to-add-the-table-looping-and-table-extractor-functoids-to-a-map-and-configure-them"></a>Pour ajouter les fonctoids Bouclage de table et Extracteur de table à un mappage et les configurer  
  
1.  Avec la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] boîte à outils active, cliquez sur le **Fonctoids avancés** tab pour sélectionner cette catégorie de fonctoids.  
  
     La liste de fonctoids de la catégorie choisie s'affiche.  
  
2.  Faites glisser le **bouclage de Table** fonctoid (![](../core/media/advtablelooping.gif "advtablelooping")) à partir de la boîte à outils vers l’emplacement approprié sur une page de grille.  
  
    > [!NOTE]
    >  Le fonctoid sera placé sur la page de grille affichée. Si vous souhaitez le placer sur une autre page de grille, vous devez d’abord afficher cette page de grille.  
  
    > [!NOTE]
    >  Étant donné que la sortie de la **bouclage de Table** fonctoid sert d’entrée à un ou plusieurs associés **extracteur de Table** fonctoids, assurez-vous que vous laissez un écart à droite de la **debouclagedeTable** fonctoid pour le **extracteur de Table** fonctoids.  
  
3.  Faites glisser un enregistrement ou champ du schéma source vers la nouvelle **bouclage de Table** fonctoid. Comme le premier paramètre d’entrée de la **bouclage de Table** fonctoid, le nombre d’occurrences de cet enregistrement ou un champ dans un message d’instance détermine le nombre de fois où ce fonctoid génère la sortie. Par exemple, si un enregistrement de boucle est déplacé vers le fonctoid, un message d’instance possédant 10 occurrences de cet enregistrement est traité, et la grille de table a été configurée avec une ligne de sources de données de la colonne de la **bouclage de Table** fonctoid effectue une itération 10 fois, produisant 10 lignes de sortie pour l’extraction par un **extracteur de Table** fonctoid et destination 10 permettant d’enregistrements pour être facilement construits.  
  
    > [!NOTE]
    >  Si vous configurez plusieurs lignes dans la grille de table, chaque ligne sera générée pour chaque itération de la **bouclage de Table** fonctoid. Par conséquent, le nombre d’occurrences d’un enregistrement d’entrée multiplié par le nombre de lignes configurées dans la grille de table donne le nombre de lignes de table de sortie disponibles pour l'extraction de données.  
  
4.  Faites glisser un enregistrement ou champ du schéma de destination vers le **bouclage de Table** fonctoid. Ce lien permet de s’assurer que le nœud est créé dans le schéma de destination.  
  
5.  Sélectionnez récemment ajouté **bouclage de Table** fonctoid, puis, dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) bouton associé à son **paramètres d’entrée** propriété.  
  
    > [!NOTE]
    >  Vous pouvez également sélectionner le fonctoid, puis appuyer sur les touches CTRL+M, CTRL+T. Pour obtenir la liste du Mappeur Voir raccourcis clavier [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
6.  Dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue, cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") pour créer le deuxième bouton paramètre d’entrée. Tapez un nombre qui représente le nombre de colonnes qui seront disponibles dans la table que vous créez pour ce **bouclage de Table** fonctoid.  
  
    > [!NOTE]
    >  Le nombre maximal de colonnes dans la table est de 228.  
  
7.  Dans le **configurer le fonctoid Bouclage de Table** boîte de dialogue, cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") pour entrer n’importe quelle constante valeurs qui s’affiche dans la grille de table configurée. L’ordre dans lequel vous créez ces constantes n’est pas important dans cette boîte de dialogue, tant que les premier et second paramètres, le nombre de lignes et de colonnes, respectivement, gardent leur position au début de la liste des paramètres d’entrée. Lorsque vous avez terminé, cliquez sur **OK**.  
  
     Le **configurer le fonctoid Bouclage de Table** boîte de dialogue se ferme.  
  
8.  Faites glisser zéro ou plusieurs nœuds enregistrement ou de champ du schéma source vers le **bouclage de Table** fonctoid que vous avez récemment ajouté. Chacun de ces nœuds d’enregistrement et de champ est ajouté à la fin de la liste des paramètres d’entrée et sera par conséquent disponible lorsque la grille de table sera configurée dans une prochaine étape. À l’instar des constantes de données de table ajoutées précédemment (pas les constantes de nombre de colonne et de ligne), l’ordre dans lequel ces nœuds d’enregistrement et de champ sont ajoutés n’est pas important.  
  
9. Pour attribuer une étiquette à un lien, effectuez la procédure ci-dessous :  
  
    -   Sélectionnez un lien dans la page de grille affichée.  
  
    -   Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, tapez un nom descriptif pour le **étiquette** propriété. Par exemple, vous pouvez donner le nom « link2ndAuthor » à un lien issu d'un champ appelé « Second Author ».  
  
10. Sélectionnez récemment ajouté **bouclage de Table** fonctoid, puis, dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) associés à la **grille Bouclage de Table** propriété associée à ce fonctoid.  
  
     Le **configurer le fonctoid Bouclage de Table** boîte de dialogue s’affiche avec le **grille Bouclage de Table** onglet sélectionné.  
  
    > [!NOTE]
    >  Ou bien, cliquez sur le fonctoid, puis cliquez sur **configurer la grille Bouclage de Table** dans le menu contextuel. Le **configurer le fonctoid Bouclage de Table** boîte de dialogue s’affiche avec le **grille Bouclage de Table** onglet sélectionné.  
  
11. Utilisez les listes déroulantes associées à chaque cellule de table pour configurer au moins une ligne de la grille, éventuellement plus. Les choix disponibles dans les listes déroulantes sont les constantes et les liens que vous avez configuré dans les étapes 6 à 8 en tant que paramètres d’entrée 3 et jusqu'à la **bouclage de Table** fonctoid. (Les paramètres d’entrée 1 et 2 n’apparaissent pas dans ces listes déroulantes.) Lorsque vous avez terminé, cliquez sur **OK**.  
  
     Le **configurer le fonctoid Bouclage de Table** boîte de dialogue se ferme.  
  
    > [!NOTE]
    >  Chaque ligne correspond à une itération de la structure de sortie, en association avec le nombre d’occurrences de l’enregistrement ou le champ spécifié comme premier paramètre d’entrée de la **bouclage de Table** fonctoid. Pour plus d’informations, consultez l’étape 3.  
  
    > [!NOTE]
    >  Vous devez sélectionner une valeur pour chaque colonne que vous avez l’intention d’accéder à l’aide un **extracteur de Table** fonctoid. Si une colonne n’est pas utilisée par un **extracteur de Table** fonctoid, pensez à supprimer, plutôt que de maintenance, cette colonne.  
  
    > [!NOTE]
    >  L’ordre de remplissage de la grille de table est sans importance.  
  
12. Faites glisser autant **extracteur de Table** fonctoids (![](../core/media/advtableextractor.gif "advtableextractor")) à partir de la boîte à outils vers la page de grille affichée en fonction des besoins.  
  
    > [!NOTE]
    >  Étant donné que l’entrée de ces **extracteur de Table** provient de fonctoids le **bouclage de Table** fonctoid ajouté à l’étape précédente, assurez-vous que vous placez le **extracteur de Table** fonctoids à droite de la **bouclage de Table** fonctoid dans la page de grille affichée.  
  
13. Pour créer le premier paramètre d’entrée pour l’une de le **extracteur de Table** fonctoids ajoutés à l’étape 9, faites-le glisser vers la **bouclage de Table** fonctoid à sa gauche.  
  
14. Pour créer le deuxième paramètre d’entrée pour le même **extracteur de Table** fonctoid, sélectionnez le fonctoid, puis, dans le **propriétés** fenêtre, cliquez sur le bouton de sélection (**...** ) bouton associé à son **paramètres d’entrée** propriété.  
  
     Le **configurer le fonctoid Extracteur de Table** boîte de dialogue s’affiche.  
  
15. Cliquez sur le ![Ajout des paramètres d’entrée constants à un fonctoid](../core/media/add-input-parameters.gif "Add_input_parameters") bouton permettant de créer le deuxième paramètre d’entrée. Tapez le numéro de la colonne dans la grille de table correspondantes **bouclage de Table** fonctoid à partir de laquelle vous souhaitez extraire des données. Cliquez sur **OK**.  
  
     Le **configurer le fonctoid Extracteur de Table** boîte de dialogue se ferme.  
  
    > [!NOTE]
    >  Les numéros de colonne démarrent à 1.  
  
16. Pour utiliser la sortie de la **extracteur de Table** fonctoid, faites glisser le **extracteur de Table** fonctoid vers un nœud enregistrement ou de champ dans le schéma de destination, ou faites glisser un nœud enregistrement ou de champ dans le schéma de destination pour le  **Extracteur de table** fonctoid. La valeur d’élément ou d’attribut du message d’instance de destination correspondant à ce nœud d’enregistrement ou de champ dans le schéma de destination est renseignée par la valeur issue de (dans le cas de constantes), ou indiquée par (dans le cas de liens), la cellule spécifiée dans la grille de table.  
  
17. Répétez les étapes 12, 13, 14 et 15 pour chacun de la **extracteur de Table** fonctoids ajoutés à l’étape 11.  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)