---
title: "Génération d’un Message et la Validation de l’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a306846-3942-4ba1-a74e-6ead8deb0322
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 964f9bd2ee2b8bb20872bc593723cea778b5ed81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-generation-and-validation"></a>Validation et génération d’un message d’instance
Une fois que vous avez validé un schéma, vous pouvez l'utiliser pour générer un exemple de message d'instance. L'exemple de message d'instance généré contient la structure d'élément et d'attribut spécifiée par le schéma et des données factices de génération le cas échéant.  
  
> [!NOTE]
>  Le mécanisme de génération de données utilisé pour la génération des messages d'instance n'est pas suffisamment sophistiqué pour générer des données en fonction des valeurs spécifiées pour plusieurs propriétés. Par exemple, si le schéma contient des valeurs pour le **modèle** propriété, qui est disponible dans le **Restrictions** catégorie **élément de champ** nœuds et **Attribut de champ** nœuds lors de leur **Derived By** est définie sur **Restriction**, le message d’instance généré ne peut pas servir comme cela est, en tant qu’entrée à la **Valider l’Instance** opération.  
  
 Pour générer un exemple de message d’instance à partir d’un schéma, utilisez la **générer l’Instance** du menu contextuel associé au schéma dans l’Explorateur de solutions. Les résultats de l'opération de génération de message d'instance sont reportés dans la fenêtre de sortie [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  Le **générer l’Instance** opération inclut le **valider le schéma** opération. Si la validation échoue, aucun exemple de message d'instance ne sera généré.  
  
 Pour obtenir des instructions détaillées sur la génération d’un message d’instance à partir d’un schéma, y compris la configuration d’un fichier de sortie qui contiendra le message d’instance généré, consultez [génération de Messages d’Instance](../core/how-to-generate-instance-messages.md).  
  
> [!NOTE]
>  Si vous ne spécifiez pas une valeur pour le **référence de racine** propriété de la **schéma** nœud, l’Éditeur BizTalk génère un message d’instance pour le premier nœud racine dans le schéma. Si vous spécifiez une valeur pour le **référence de racine** propriété, l’Éditeur BizTalk génère un message d’instance pour la racine spécifiée.  
  
 Si vous avez validé votre schéma, vous pouvez utiliser l'Éditeur BizTalk pour déterminer si un message d'instance est conforme à ce schéma.  
  
 Pour valider un message d’instance par rapport à un schéma, utilisez la **valider l’Instance** du menu contextuel associé au schéma dans l’Explorateur de solutions. Les résultats de la validation sont affichés dans la fenêtre Sortie de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  Les messages d'instance générés ne sont pas toujours validés par rapport au schéma à partir duquel ils ont été générés. Par exemple, si vous tentez de valider un message d’instance qui a été généré à l’aide de la **générer l’Instance** commande dans l’Éditeur BizTalk et le schéma pertinent inclut les **élément de champ** nœuds ou  **Attribut de champ** les nœuds qui ont leur **Derived By** propriété **Restriction** et qui utilisent le **modèle** propriété pour spécifier un modèle auquel les données correspondantes doivent être conformes, la validation échoue. Il s’agit, car le mécanisme de génération de données utilisé lors de la génération des messages d’instance n’est pas suffisamment sophistiqué pour générer des données en fonction des valeurs spécifiées pour le **modèle** propriété. Cela n'est qu'un exemple parmi d'autres.  
  
 Pour obtenir des instructions détaillées concernant la validation d’un message d’instance, y compris comment spécifier le message d’instance à valider, consultez [validation de schémas](../core/how-to-validate-schemas-in-visual-studio.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À propos des schémas](../core/about-schemas.md)   
 [Test de schémas](../core/testing-schemas.md)