---
title: "Comment configurer la forme réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filter expressions, Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], about Receive shape
- configuring [Orchestration Designer], Receive shapes
- Receive shape [Orchestration Designer]
- Receive shape [Orchestration Designer], filter expressions
ms.assetid: 15aadee4-fa05-4edd-a191-e4d191c1ea22
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e74220ab71c0efcc09e1736511e8388de71f387
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-the-receive-shape"></a>Configuration de la forme Réception
![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")  
Forme Réception  
  
 A **réception** forme peut être utilisée pour démarrer une orchestration. Si vous définissez la **activer** propriété **True**, le moteur d’exécution testerez un message entrant pour voir s’il s’agit du type approprié et, si un filtre a été appliqué, si l’expression de filtre est satisfaite. Si les critères pour la réception du message, le moteur d’exécution crée et exécute une nouvelle instance de l’orchestration et le **réception** forme reçoit le message.  
  
> [!NOTE]
>  Si le **activer** propriété d’une forme réception est définie sur True, le **réception** doit être la première action dans l’orchestration.  
  
> [!NOTE]
>  Si le **activer** est définie sur False sur tous les **réception** formes, l’orchestration doit être appelée par une autre orchestration pour pouvoir pour s’exécuter.  
  
> [!NOTE]
>  Si vous placez un **réception** forme à l’intérieur d’une étendue avec le **activer** propriété la valeur **True**, puis ajoutez une variable de classe .NET à votre orchestration sans modifier le la variable **utiliser le constructeur par défaut** propriété **False**, la réception avec activation instruction sera hors de portée dans le code généré de XLANG/S, mais continue à l’aire de conception afficher comme étant à l’intérieur de l’étendue.  
  
 Chaque orchestration doit avoir au moins un **réception** mettre en forme avec la **activer** propriété **True**.  
  
 Si vous vous attendez à recevoir une réponse indirecte ou asynchrone à un message précédemment envoyé (sans passer par un port de requête-réponse), vous devez mettre le message en corrélation avec l'instance d'orchestration en cours d'exécution, afin que la réponse puisse être dirigée vers l'instance appropriée. Vous pouvez appliquer à la forme Envoi un ensemble de corrélations initial, si vous prévoyez d'effectuer une corrélation ultérieure des valeurs du message entrant, ou un ensemble de corrélations ultérieur pour une corrélation utilisant un ensemble de corrélations précédemment initialisé. Pour plus d’informations, consultez [à l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md).  
  
### <a name="to-configure-a-receive-shape"></a>Pour configurer une forme Réception  
  
1.  Définissez un message et une opération de port.  
  
    1.  Dans la fenêtre Vue Orchestration, vérifiez que votre orchestration comporte à la fois un message et une opération de port définis pour le type de message reçu.  
  
         Dans la fenêtre Propriétés, sélectionnez le message à recevoir dans le **Message** liste de propriétés de liste déroulante.  
  
    2.  Dans la fenêtre Propriétés, sélectionnez l’opération de port pour recevoir le message à partir de la **opération** liste déroulante.  
  
         — Ou :  
  
         Faites glisser le connecteur de réception à partir de la **réception** forme pour le socket de port qui recevra le message.  
  
2.  Spécifier que le **réception** forme activera l’orchestration.  
  
3.  Dans la fenêtre Propriétés, définissez la propriété Activer sur True.  
  
    1.  Dans la fenêtre Propriétés, cliquez sur le **points de suspension** (**...** ) bouton de la propriété Expression de filtre créer un filtre pour limiter les messages que ce **réception** forme accepte.  
  
         — Ou :  
  
         Cliquez sur le **réception** mettre en forme, puis cliquez sur **modifier l’Expression de filtre**.  
  
    2.  Le **Expression de filtre** boîte de dialogue s’affiche. Utilisez cette boîte de dialogue pour créer une ou plusieurs expressions de filtre.  
  
        > [!NOTE]
        >  Un type de message doit être défini et affecté à la **réception** mettre en forme avant de pouvoir appliquer un filtre à ce dernier.  
  
4.  Spécifier les ensembles de corrélations pour limiter les messages le **réception** forme accepte.  
  
    -   Pour chaque ensemble de corrélations que vous souhaitez suivre, vérifiez une corrélation défini dans la liste déroulante sur le **ensembles de corrélations suivants** propriété.  
  
    -   Pour chaque correspondance de jeu que vous souhaitez initialiser, vérifiez une corrélation défini dans la liste déroulante sur le **l’initialisation des ensembles de corrélations** propriété.  
  
## <a name="filter-expression-grid-control"></a>Contrôle de grille Expression de filtre  
 Créez une expression de filtre à l'aide de ce contrôle de grille pour définir les prédicats composant l'expression. Vous pouvez ajouter, modifier et supprimer des prédicats dans les cellules de la grille. Ce contrôle de grille comporte quatre colonnes : propriété, opérateur, valeur et groupement.  
  
-   **Propriété.** Vous pouvez entrer une référence de propriété ou en sélectionner une dans la liste déroulante de la cellule. La liste comprend des propriétés de message entrant.  
  
-   **Opérateur.** Vous pouvez entrer valeur dans cette cellule ou sélectionner un opérateur dans la liste déroulante de la cellule. Les sélections possibles sont :  
  
    |Opérande|Signification|  
    |-------------|-------------|  
    |==|Est égal à|  
    |!=|n'est pas égal à|  
    |<|Est inférieur à|  
    |\<=|Est inférieur ou égal à|  
    |>|Est supérieur à|  
    |\>=|Est supérieur ou égal à|  
    |Exists|Exists|  
  
-   **Valeur.** Cellules de la **valeur** colonne peut contenir n’importe quelle constante que vous tapez dans : un littéral de chaîne, un littéral entier, ou null.  
  
    > [!NOTE]
    >  Si la propriété sélectionnée est du type chaîne, la valeur doit être encadrée par des guillemets. Par exemple, SMTP.From = "MyServer".  
  
-   **Regroupement.** Utiliser cette colonne pour contrôler les groupes de prédicats. Les expressions de filtre sont toujours exprimées dans le formulaire de normale disjonctive (FND) afin de regroupement peut être déterminé automatiquement. AND indique que le prédicat doit être regroupé avec le prédicat suivant, tandis que OR indique que le prédicat est séparé du prédicat de la ligne suivante. Des parenthèses grises à gauche du contrôle de grille apparaissent lorsque les prédicats sont regroupés ensemble. Il est impossible d'imbriquer des groupes de prédicats. Si vous n'entrez pas de valeur dans cette cellule, la valeur par défaut est AND.  
  
 Par exemple, vous pouvez créer l'expression suivante :  
  
 `MSMQ.MsgID = 1`  
  
 Avec ce filtre, le groupe de ports d'envoi s'abonnera uniquement aux messages ayant un ID de message MSMQ correspondant à 1.  
  
 Vous pouvez créer des expressions supplémentaires et leur définir une relation AND ou OR avec d'autres expressions, par exemple :  
  
 `MSMQ.MsgID = 1 OR`  
  
 `SMTP.From = "MyServer"`  
  
 Dans ce cas, le groupe de ports d'envoi s'abonnera à tous les messages ayant un ID de message MSMQ de 1 ou qui proviennent du serveur SMTP nommé MyServer.  
  
## <a name="hint-label"></a>Étiquette d'indication  
 Ce champ constitue une aide pour l'utilisateur. Le texte de l'étiquette change en fonction de la colonne contenant la cellule active. Le texte affiche le nom de la colonne suivi par une indication, comme suit :  
  
-   **Propriété.** Veuillez sélectionner une propriété pour le message entrant dans la liste.  
  
-   **Opérateur.** Sélectionnez un opérateur afin de comparer la Propriété avec la Valeur.  
  
-   **Valeur.** Sélectionnez une propriété de message dans la liste, ou tapez une valeur littérale.  
  
-   **Regroupement.** Spécifiez la manière dont cette lignée doit être regroupée avec la ligne suivante. "AND" entraîne la liaison des lignes, "OR" les sépare.  
  
## <a name="move-up-button"></a>Bouton Monter   
 Cliquez sur ce bouton pour déplacer la ligne sélectionnée vers le haut. (Commencez par sélectionner une ligne en cliquant sur le *flèche droite* (**>)** bouton sur le côté gauche du contrôle de grille.)  
  
## <a name="move-down-button"></a>Bouton Descendre   
 Cliquez sur ce bouton pour déplacer la ligne sélectionnée vers le bas. (Commencez par sélectionner une ligne en cliquant sur le *flèche droite* (**>)** bouton sur le côté gauche du contrôle de grille.)  
  
## <a name="filter-expression-created-field"></a>Champ Expression de filtre créée  
 Cette zone de texte en lecteur seule contient l'expression telle que vous l'avez créée.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation des filtres avec la forme Réception de messages](../core/using-filters-with-the-receive-message-shape.md)