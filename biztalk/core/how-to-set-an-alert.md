---
title: "Comment définir une alerte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- alerts, creating
- Query Builder [BAM portal], creating alerts
- queries [BAM], aggregations
- Query Builder [BAM portal], activity searches
- Query Builder [BAM portal], aggregation alerts
- queries [BAM], alerts
- aggregations, alerts
ms.assetid: 8745d2c6-5bc0-4d7a-8c17-361535f5c6e6
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 774fbab86c1da1389b813f621c89f38cf0aa7656
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-an-alert"></a>Définition d'une alerte
Vous pouvez définir une alerte en la joignant à une recherche d'activité ou en parcourant une agrégation.  
  
> [!NOTE]
>  Avant de définir une alerte sur une requête, il est préférable que vous exécutiez cette dernière et évaluiez si les durées des cycles d'alerte sont appropriées pour le processus dont vous effectuez l'analyse. Si la durée d'un cycle est trop brève, il est possible qu'une condition d'alerte soit transitoire et qu'elle soit manquée par le système d'alerte.  
  
> [!NOTE]
>  Si vous cliquez sur le bouton précédent pendant ces procédures, vous pouvez recevoir le message suivant : « avertissement : page a expiré. » Pour revenir au contenu précédent, appuyez sur F5. (Vous devrez peut-être appuyer plusieurs fois sur F5.)  
  
> [!NOTE]
>  Lorsque vous créerez la première alerte dans une vue, aucune donnée associée ne sera affichée. La définition d'une alerte n'entraîne pas la collection de données à partir du laps de temps précédant sa création.  
  
## <a name="prerequisites"></a>Conditions préalables  
 La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :  
  
-   Vous devez disposer d'une vue déployée.  
  
-   Vous devez disposez d'une recherche d'activité pour une alerte d'instance.  
  
-   Vous devez disposer d'une agrégation renseignée pour une alerte d'agrégation.  
  
### <a name="to-set-an-alert-on-an-activity-search"></a>Pour définir une alerte sur une recherche d'activité.  
  
1.  Dans le **Mes vues** frame, cliquez sur une vue pour développer la liste des tâches pour l’affichage.  
  
2.  Cliquez sur le **recherche d’activité** tâche sous la vue que vous avez développé.  
  
3.  Créez ou ouvrez une recherche d'activité. Pour plus d’informations sur la procédure à suivre, consultez [la création d’une requête de recherche d’activité](../core/how-to-create-a-query-in-activity-search.md).  
  
4.  Dans le cadre contenu du portail BAM, cliquez sur le **définir l’alerte** bouton. Le frame de contenu sera chargé avec le modèle de création de l'alerte.  
  
5.  Dans le **nom** texte, tapez un nom descriptif pour l’alerte.  
  
    > [!NOTE]
    >  Les noms sont limités à 100 caractères et ne peut pas contenir les caractères suivants : ~ ! @# $% ^&amp;* () ;  Si vous entrez un de ces caractères dans un nom, une bordure rouge pointillée apparaît autour du champ de texte signalant une erreur que vous devez corriger pour terminer l’action.  
  
6.  Si vous ne souhaitez pas l’alerte soit activée pour l’instant, désactivez le **alerte activée** case à cocher.  
  
7.  Dans le **Message** texte, tapez le message est remis lorsque l’alerte est déclenchée.  
  
8.  À partir de la **priorité** liste déroulante, sélectionnez le niveau de priorité pour cette alerte. Le paramètre de priorité indique la gravité du problème sur laquelle l'alerte a été définie.  
  
9. Dans le **propriétaires** zone de texte, tapez les alias des propriétaires de cette alerte. Utilisez des points-virgules entre les noms de plusieurs utilisateurs.  
  
10. Dans le **alerte sécurité** zone, sélectionnez la case à cocher pour autoriser d’autres utilisateurs à voir cette alerte et vous abonner à ce dernier.  
  
    > [!NOTE]
    >  Vous pouvez basculer entre la sécurité d'alerte privée et publique à tout moment ; l'existence d'abonnés à l'alerte n'a pas d'incidence sur cette action. Néanmoins, lorsque vous faites passer la sécurité d'alerte de publique à privée, demandez-vous s'il y a des abonnés à l'alerte. Si c'est le cas, ils n'auront aucun moyen de modifier leur abonnement à partir du moment où l'alerte sera privée.  
  
11. Dans le coin supérieur droit de la **détails de l’alerte** zone, cliquez sur le **enregistrer l’alerte** bouton.  
  
### <a name="to-set-an-alert-on-an-aggregation"></a>Pour définir une alerte sur une agrégation  
  
1.  Dans le **Mes vues** frame, cliquez sur une vue pour développer la liste des tâches pour l’affichage.  
  
2.  Cliquez sur le **agrégations** de tâches dans **Mes vues** sous la vue que vous avez développé.  
  
3.  Dans le frame de contenu du portail BAM, cliquez avec le bouton droit sur une cellule de la colonne des totaux du rapport de tableau croisé dynamique. Cela aura pour effet d'ouvrir un menu contextuel contenant des fonctions à exécuter sur le total d'agrégation.  
  
    > [!NOTE]
    >  Vous pouvez définir une alerte sur un composant spécifique du total d'agrégation en développant cet élément de ligne. Vous pouvez développer de cette façon plusieurs niveaux se succédant jusqu'à ce que vous ayez atteint le niveau auquel vous désirez définir votre alerte.  
  
4.  En haut du menu contextuel, cliquez sur **créer une alerte**. Le frame de contenu sera chargé avec le modèle de création de l'alerte.  
  
5.  Dans le **nom** texte, tapez un nom descriptif pour l’alerte.  
  
    > [!NOTE]
    >  Les noms sont limités à 100 caractères et ne peut pas contenir les caractères suivants : ~ ! @# $% ^&amp;* () ;  Si vous entrez un de ces caractères dans un nom, une bordure rouge pointillée apparaît autour du champ de texte signalant une erreur que vous devez corriger pour terminer l’action.  
  
6.  Si vous ne souhaitez pas l’alerte soit activée pour l’instant, désactivez le **alerte activée** case à cocher.  
  
7.  Dans le **Message** texte, tapez le message est remis lorsque l’alerte est déclenchée.  
  
8.  À partir de la **priorité** liste déroulante, sélectionnez le niveau de priorité pour cette alerte. Le paramètre de priorité indique la gravité du problème sur laquelle l'alerte a été définie.  
  
9. Dans le **propriétaires** zone de texte, tapez les alias des propriétaires de cette alerte. Utilisez des points-virgules entre les noms de plusieurs utilisateurs.  
  
10. Dans le **seuil** zone, sélectionnez une condition de comparaison de la **nombre** liste déroulante.  
  
11. Dans le **durée** texte, entrez le nombre d’unités de temps sur laquelle le seuil est mesuré.  
  
12. À partir de la **durée** liste déroulante, sélectionnez l’unité de temps.  
  
13. Dans le **alerte sécurité** zone, sélectionnez la case à cocher pour autoriser d’autres utilisateurs à voir cette alerte et vous abonner à ce dernier.  
  
    > [!NOTE]
    >  Vous pouvez basculer entre la sécurité d'alerte privée et publique à tout moment ; l'existence d'abonnés à l'alerte n'a pas d'incidence sur cette action. Néanmoins, lorsque vous faites passer la sécurité d'alerte de publique à privée, demandez-vous s'il y a des abonnés à l'alerte. Si c'est le cas, ils n'auront aucun moyen de modifier leur abonnement à partir du moment où l'alerte sera privée.  
  
14. Dans le coin supérieur droit de la **détails de l’alerte** zone, cliquez sur le **enregistrer l’alerte** bouton.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer une requête de recherche d’activité](../core/how-to-create-a-query-in-activity-search.md)