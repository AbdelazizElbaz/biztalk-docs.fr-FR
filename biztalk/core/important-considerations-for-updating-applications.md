---
title: "Considérations importantes pour la mise à jour des Applications | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updating, applications
- applications, planning
- applications, updating
- planning, applications
- planning, updating
- updating, planning
ms.assetid: e7690bdf-943d-4bb6-b8cd-a6841b722d40
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24528dcce390376b7ac2e47199aa5ae06d412a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="important-considerations-for-updating-applications"></a>Considérations importantes relatives à la mise à jour d'applications
Vous trouverez ci-dessous d'importantes remarques à prendre en considération avant de mettre une application à jour, en particulier si celle-ci est exécutée dans un environnement de production.  
  
## <a name="general-considerations"></a>Observations générales  
  
-   Les tiers et les règles sont visibles au niveau des groupes. L'ajout de tiers et de règles peut donc perturber les autres applications.  
  
-   Si vous annulez le déploiement d'un artefact dont dépend un autre artefact, le déploiement de l'artefact dépendant doit être annulé au préalable.  
  
    > [!NOTE]
    >  La console Administration de BizTalk Server affiche un avertissement pour vous empêcher d'annuler le déploiement des artefacts dans le mauvais ordre.  
  
-   Si un assembly BizTalk dans une application existante est mise à jour, vous devrez peut-être redémarrer les instances d’hôte pour que les modifications prennent effet. Le redémarrage d’une instance d’hôte arrête toutes les autres applications qui sont exécutent sur l’instance d’hôte.  
  
-   Si vous utilisez Visual Studio pour déployer une application dans un environnement de production (ce que nous vous déconseillons fortement) et que l'option Redémarrer les instances d'hôte est définie sur True dans les propriétés de projet, toutes les instances d'hôte redémarreront lorsque vous déploierez l'application, y compris celles qui ne sont pas associées à l'application. Ce processus interrompra toutes les autres applications exécutées sur les instances d'hôte de l'ordinateur local.  
  
-   Pour mettre à jour un assembly BizTalk Server (contenant une orchestration, un schéma ou un mappage) déployé comme application BizTalk, vous pouvez effectuer l'une des opérations suivantes :  
  
    -   Effectuez un déploiement côte à côte. Vous pouvez généralement modifier de façon appropriée l'assembly plus récent en incrémentant sa version. Cela a pour effet d'attribuer aux deux assemblys un nom complet distinct. Pour plus d’informations, consultez [comment déployer une nouvelle Version d’une Application à exécuter de côte à côte avec une Version existante](../core/deploy-new-application-version-to-run-side-by-side-with-existing-version.md).  
  
    -   Remplacez l'assembly BizTalk Server existant par un nouvel assembly. Vous devez arrêter toutes les instances de l'hôte susceptibles de charger l'assembly obsolète, remplacer ce dernier dans le GAC, puis redémarrer les instances de l'hôte.  
  
-   Si vous déployez une toute nouvelle application en remplacement de l'application existante, vous devez corriger toutes les références entre les autres applications et l'application que vous remplacez.  
  
## <a name="considerations-for-updating-schemas"></a>Observations concernant la mise à jour des schémas  
  
-   Si vous ajoutez un assembly à une application qui comprend un nouveau schéma avec le même type de message en tant qu’un schéma existant dans le groupe BizTalk, le schéma avec le numéro de version le plus élevé sera utilisé lors de la résolution de schéma se produit dans les pipelines. En outre, si un type de message fait référence à plusieurs types .NET, cette ambiguïté peut entraîner d’échec d’exécution du pipeline. En effet, la recherche de schémas utilise le type de message, l'espace de noms cible et le nom de la racine de l'instance. Ceci peut se produire pour les pipelines des applications qui utilisent un schéma possédant le même type de message que le nouveau schéma. Pour plus d’informations sur la résolution de schéma, consultez [résolution de schéma dans les composants de Pipeline](../core/schema-resolution-in-pipeline-components.md).  
  
-   Lorsque vous mettez un schéma à jour, vous devez également mettre à jour les mappages qui font référence au schéma (ou créer de nouveaux mappages), ainsi que les orchestrations reposant sur ce schéma.  
  
-   Si vous incrémentez la version d'un schéma, vous devez mettre à jour la référence à ce schéma pour toutes les instances et composants de pipeline qui l'utilisent.  
  
-   L'annulation du déploiement d'un schéma entraîne l'activation de la version précédente de ce schéma, si tant est qu'elle soit disponible.  
  
## <a name="considerations-for-updating-policies"></a>Observations concernant la mise à jour des stratégies  
  
-   La version la plus élevée d'une stratégie déployée est utilisée par le moteur d'exécution BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md)