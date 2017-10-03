---
title: "Comment configurer la forme Démarrer Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [Orchestration Designer], Start Orchestration shapes
- Start Orchestration shape [Orchestration Designer], parameters
- Start Orchestration shape [Orchestration Designer], configuring
- orchestrations, starting
- Start Orchestration shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer], starting orchestrations
- Start Orchestration shape [Orchestration Designer], about Star Orchestration shape
ms.assetid: 9d01c41e-9bc5-4c1c-a869-b2f0df13036a
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f8181849b700939ba86f55cd372b80ed2ebf70e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-start-orchestration-shape"></a>Configuration de la forme Démarrer orchestration
Le **démarrer Orchestration** forme est similaire à la **appeler Orchestration** forme, mais permet d’appeler une autre orchestration de façon asynchrone avec le **démarrer Orchestration** forme, autrement dit, le flux de contrôle dans l’orchestration appelante se poursuit au-delà de l’appel, sans attendre que l’orchestration appelée terminer son travail.  
  
 Vous pouvez spécifier les paramètres qui seront transmis à l'orchestration appelée. Les paramètres incluent les messages, variables, références de port, liens de rôle ou ensembles de corrélations. Le **démarrer Orchestration** acceptent uniquement les formes *dans* paramètres ; il ne peut pas prendre *hors* ou *ref* paramètres.  
  
> [!CAUTION]
>  Si vous passez des objets non sérialisables tels que XmlDocument ou XmlNode comme paramètres à une orchestration, il échouera.  
  
 Le **démarrer Orchestration** forme est la seule forme dans laquelle vous pouvez inverser la polarité d’un port transmis en tant que paramètre, par exemple un *utilise* port (port d’envoi) peut être passé à une orchestration appelée, mais l’orchestration appelée peut le traiter comme un *implémente* port (port de réception). Notez que cela n'est possible qu'avec des ports qui utilisent une liaison directe.  
  
 Le **démarrer Orchestration** forme peut également être utilisé pour appeler une orchestration qui est référencée dans un autre projet. Cela permet de réutiliser les modèles de workflow d'orchestration communs sur les divers projets BizTalk. Pour l’orchestration référencée puisse être appelée, assurez-vous que le **modificateur de Type** pour l’orchestration appelée est définie sur **Public**. Pour définir le **modificateur de Type** propriété d’une orchestration à **Public**, ouvrez l’orchestration dans Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], cliquez sur la forme Début verte en haut de l’orchestration pour afficher le  **Propriétés d’orchestration** boîte de dialogue et définissez la **modificateur de Type** propriété **Public**. La valeur par défaut **modificateur de Type** est **privé**.  
  
 Pour obtenir un exemple montrant comment utiliser **démarrer Orchestration** mettre en forme, téléchargez l’exemple de kit de développement logiciel « Mise en œuvre à nuages de points modèle et de collecter des » [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).  
  
### <a name="to-configure-a-start-orchestration-shape"></a>Pour configurer une forme Démarrer orchestration  
  
1.  À l’aide de la **sélection de l’Orchestration** zone de liste déroulante, sélectionnez une orchestration dans la liste.  
  
2.  À l’aide de la **paramètres de l’Orchestration** grille contrôler, indiquez les arguments à passer à l’orchestration — comme spécifié dans le **sélection de l’Orchestration** zone de liste déroulante : qui est démarré. Pour indiquer ces arguments dans les cellules de la colonne Variable (une variable par cellule), entrez le nom d'une variable ou cliquez sur celle-ci dans la liste déroulante d'une cellule.  
  
3.  Pour configurer le **démarrer Orchestration** mettre en forme en fonction du service et les arguments que vous avez spécifié dans la boîte de dialogue, cliquez sur **OK**. Pour fermer la **Configuration de démarrer Orchestration** boîte de dialogue sans apporter de modifications à la **démarrer Orchestration** mettre en forme, cliquez sur **Annuler**.  
  
    > [!CAUTION]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne prend pas en charge les orchestrations récursives. Si l'orchestration A appelle ou démarre l'orchestration B, cette dernière ne peut pas appeler ou démarrer directement l'orchestration A, de même que les orchestrations qui appellent directement ou indirectement l'orchestration A.  
  
## <a name="orchestration-selection-drop-down-list-box"></a>Zone de liste déroulante de sélection de l'orchestration  
 Cliquez sur la flèche pointant vers le bas dans la liste déroulante pour afficher les orchestrations disponibles, puis sélectionnez celle souhaitée. Cette liste contient toutes les orchestrations qui peuvent être démarrées à partir de l'orchestration actuelle, y compris les assemblys référencés.  
  
## <a name="orchestration-parameters-grid-control"></a>Contrôle de grille Paramètres de l'orchestration  
 Vous spécifiez les arguments à passer à une orchestration paramétrée par à l’aide de la **paramètres de l’Orchestration** contrôle de grille. La grille comporte quatre colonnes : les Variables dans l’étendue, nom de paramètre, Type de paramètre et Direction du paramètre. Seule la première colonne est modifiable, les autres étant en lecture seule.  
  
 Lorsque vous sélectionnez une orchestration valide, ses paramètres complètent les colonnes de nom, de type et de direction du contrôle de grille. Vous pouvez sélectionner les variables dans chaque ligne pour les transmettre en tant qu'arguments. Ces variables sont accessibles dans la liste déroulante de chaque cellule dans la colonne Variables de l'étendue. Cette liste affiche toutes les variables disponibles pour le type spécifié dans la cellule adjacente Type de paramètre. Si un seul objet de ce type est disponible, la cellule Variables de l'étendue est automatiquement complétée avec celui-ci. Vous pouvez également sélectionner une variable dans la liste déroulante d'une cellule Variables de l'étendue.  
  
> [!NOTE]
>  Car un **démarrer Orchestration** forme démarre une orchestration, les « paramètres d’Orchestration » vous sélectionnez dans cette boîte de dialogue font en fait référence aux variables d’orchestration.  
  
 Si l'orchestration que vous exécutez n'a pas de paramètres définis, le contrôle de grille de cette boîte de dialogue n'est pas disponible.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comment créer des Orchestrations appelées abonnements de réception](../core/how-to-create-receive-subscriptions-at-invoked-orchestrations.md) 
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer la forme appeler Orchestration](../core/how-to-configure-the-call-orchestration-shape.md)