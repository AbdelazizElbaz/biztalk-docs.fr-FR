---
title: Comment configurer la forme appeler Orchestration | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Orchestration shape [Orchestration Designer], parameters
- Call Orchestration shape [Orchestration Designer], configuring
- Call Orchestration shape [Orchestration Designer], about Call Orchestration shapes
- configuring [Orchestration Designer], Call Orchestration shapes
- Call Orchestration shape [Orchestration Designer]
- nonserializable objects
- orchestrations, nonserializable objects
- Call Orchestration shape [Orchestration Designer], referencing orchestrations
- orchestrations, parameters
ms.assetid: 718ce2a0-ac08-4662-8b4e-1be279dbc749
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dabb73b3bed616f17c69923799169a7c6ca2b6d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-call-orchestration-shape"></a>Configuration de la forme Appeler orchestration
Le **appeler Orchestration** forme peut être utilisée pour appeler de façon synchrone une orchestration qui est référencée dans un autre projet. Cela permet de réutiliser les modèles de workflow d'orchestration communs sur les divers projets BizTalk. Quand vous appelez une autre orchestration synchrone avec la **appeler Orchestration** forme l’orchestration associée attend que l’orchestration imbriquée soit terminée avant de continuer.  
  
 Vous pouvez spécifier les paramètres qui seront transmis à l'orchestration imbriquée. Les paramètres incluent les messages, variables, références de port, liens de rôle ou ensembles de corrélations. Références de port dans le passé, les liens de rôle et les ensembles de corrélations toutes s’exécutent comme des enveloppes renseignés automatiquement : ils fournissent les informations de l’orchestration imbriquée il peut utiliser pour renvoyer des informations à l’orchestration associée.  
  
> [!CAUTION]
>  Si vous transmettez des objets non sérialisables tels que XmlDocument ou XmlNode comme paramètres à une orchestration, elle échoue.  
  
 Pour obtenir un exemple montrant comment utiliser **appeler Orchestration** mettre en forme, consultez [CallOrchestration (exemple BizTalk Server)](../core/callorchestration-biztalk-server-sample.md).  
  
### <a name="to-configure-a-call-orchestration-shape"></a>Pour configurer une forme Appeler orchestration  
  
1.  À l’aide de la **sélection de l’Orchestration** zone de liste déroulante, sélectionnez une orchestration dans la liste.  
  
2.  À l’aide de la **paramètres de l’Orchestration** grille contrôler, indiquez les arguments à passer à l’orchestration — comme spécifié dans le **sélection de l’Orchestration** zone de liste déroulante : qui est appelée. Pour indiquer ces arguments dans les cellules de la colonne Variable (une variable par cellule), entrez le nom d'une variable ou cliquez sur celle-ci dans la liste déroulante d'une cellule.  
  
3.  Pour configurer le **appeler Orchestration** mettre en forme en fonction du service et les arguments que vous avez spécifié dans la boîte de dialogue, cliquez sur **OK**. Pour fermer la **Configuration d’appeler Orchestration** boîte de dialogue sans apporter de modifications à la **appeler Orchestration** mettre en forme, cliquez sur **Annuler**.  
  
    > [!CAUTION]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge les orchestrations récursives. Si l'orchestration A appelle ou démarre l'orchestration B, cette dernière ne peut pas appeler ou démarrer directement l'orchestration A, de même que les orchestrations qui appellent directement ou indirectement l'orchestration A.  
  
## <a name="referenced-orchestrations"></a>Orchestrations référencées  
 Pour que l'orchestration référencée puisse être appelée, assurez-vous que les propriétés suivantes ont été configurées pour l'orchestration appelée :  
  
-   Définir le **modificateur de Type** propriété **Public** pour l’orchestration appelée. Pour définir le **modificateur de Type** propriété d’une orchestration à **Public**, ouvrez l’orchestration dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], cliquez sur la forme Début verte en haut de l’orchestration pour afficher le  **Propriétés d’orchestration** boîte de dialogue et définissez la **modificateur de Type** propriété **Public**.  
  
-   Définir le **activer** propriété de la forme réception initiale de l’orchestration à **False**.  
  
## <a name="orchestration-selection-drop-down-list-box"></a>Zone de liste déroulante de sélection de l'orchestration  
 Cliquez sur la flèche pointant vers le bas dans la liste déroulante pour afficher les services disponibles et sélectionnez celui de votre choix. Cette liste contient tous les services qui peuvent être appelés à partir de l'orchestration en cours, y compris les assemblys référencés.  
  
## <a name="orchestration-parameters-grid-control"></a>Contrôle de grille Paramètres de l'orchestration  
 Vous spécifiez les arguments à passer à une orchestration paramétrée par à l’aide de la **paramètres de l’Orchestration** contrôle de grille. La grille comporte quatre colonnes : les Variables dans l’étendue, nom de paramètre, Type de paramètre et Direction du paramètre. Seule la première colonne est modifiable, les autres étant en lecture seule.  
  
 Lorsque vous sélectionnez une orchestration valide, ses paramètres de remplissent les colonnes de nom, type et la direction de paramètre du contrôle de grille. Vous pouvez sélectionner les variables dans chaque ligne pour les transmettre en tant qu'arguments. Ces variables sont accessibles dans la liste déroulante de chaque cellule dans la colonne Variables de l'étendue. Cette liste affiche toutes les variables disponibles pour le type spécifié dans la cellule adjacente Type de paramètre. Si un seul objet de ce type est disponible, la cellule Variables de l'étendue est automatiquement complétée avec celui-ci. Vous pouvez également sélectionner une variable dans la liste déroulante d'une cellule Variables de l'étendue.  
  
> [!NOTE]
>  Car un **appeler Orchestration** forme appelle une orchestration, les « paramètres d’Orchestration » vous sélectionnez dans cette boîte de dialogue font en fait référence aux variables d’orchestration.  
  
 Si l'orchestration que vous appelez n'a pas de paramètres définis, le contrôle de grille de cette boîte de dialogue n'est pas disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer la forme Démarrer Orchestration](../core/how-to-configure-the-start-orchestration-shape.md)