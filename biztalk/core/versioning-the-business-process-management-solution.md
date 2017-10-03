---
title: "Contrôle de version de la Solution de gestion des processus métier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- versioning, process management solutions
- process management solution tutorial, modifying
- process management solution tutorial, versioning
- processing, stages
- process management solution tutorial, processing stages
ms.assetid: 501b2162-821f-44e1-87c0-8628cc5bd9c3
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af8afd3666a35b827ff25b243c1bfb4c81262273
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="versioning-the-business-process-management-solution"></a>Contrôle de version de la Solution gestion des processus d’entreprise
La solution de gestion des processus d'entreprise est conçue de manière à que vous puissiez remplacer les étapes si nécessaire. La conception propose également une méthode simplifiée de gestion des versions de schémas.  
  
 Pour plus d’informations sur la division d’un processus d’entreprise en étapes, consultez [certains principes de conception dans la Solution de gestion des processus métier](../core/some-design-principles-in-the-business-process-management-solution.md).  
  
> [!NOTE]
>  Les éléments de la solution sont fortement dépendants au niveau des structures de message. La modification de ces structures implique l'apport d'un grand nombre de modifications aux orchestrations.  
  
 Pour obtenir des consignes générales sur la mise à jour d’assemblys dans une solution déployée et des recommandations pour l’écriture de scripts pour gérer la mise à jour, consultez [mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md).  
  
## <a name="adding-replacing-or-removing-stages"></a>Ajout, remplacement et suppression d'étapes  
 Les orchestrations d’étape de traitement de commande contiennent deux types de code : le code qui implémente le processus d’entreprise et le code qui fournit l’infrastructure de sorte qu’il puisse fonctionner dans la solution. Dans les deux orchestrations de l’étape, **CableOrder1** et **CableOrder2**, le code de processus d’entreprise à l’intérieur d’une forme groupe porte le nom « Processus d’entreprise ».  
  
 La manière la plus simple de créer une nouvelle étape consiste à copier l'une des étapes, à remplacer le code du groupe « Processus d'entreprise » par votre code, puis à laisser intact le code de l'infrastructure.  
  
> [!NOTE]
>  Le **CableOrder2** orchestration possède deux groupes « Processus d’entreprise », la deuxième autour de la forme envoi de l’historique de mise à jour. La forme Envoi fait partie d'une étendue d'envoi efficace. (Pour plus d’informations, consultez « Amélioration des performances avec des étendues imbriquées » dans [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).) Étant donné qu'une forme Groupe ne peut pas chevaucher une partie d'une forme Étendue, le deuxième groupe possède une étiquette pour indiquer qu'il fait partie du code de processus d'entreprise.  
  
 Vous devez définir l'expression de filtre d'une nouvelle orchestration par son numéro dans la séquence. Le **OrderManager** suppose que les numéros des étapes commencent à 1 et incrémenté d’un à chaque étape (1, 2, 3...). Pour filtrer sur la troisième étape, vous devez définir l'expression de filtre comme suit :  
  
 `(Microsoft.Samples.BizTalk.SouthridgeVidoe.Schemas.Stage == 3)`  
  
 L'API BAM permet à la solution de suivre les événements se produisant en son sein, y compris au niveau des étapes du traitement de la commande. La première étape démarre l'activité BAM ; la dernière étape la termine. Si des exceptions sont générées, les gestionnaires de la solution arrêtent les activités BAM impliquées. À des fins de surveillance, BAM réassemble de façon effective les opérations discontinues en une vue continue.  
  
## <a name="changing-configuration"></a>Modification de la configuration  
 Si les modifications que vous avez apportées augmentent ou réduisent le nombre d'étapes, vous devez modifier les informations de configuration stockées dans le magasin des secrets de l'authentification unique de l'entreprise.  
  
 Si vous n’avez pas encore déployé l’application, vous pouvez modifier le paramètre de configuration **TotalStages** dans le fichier de script CreateSouthridgeVideoApplication.cmd. La valeur sera modifiée à l'exécution du script lors de la phase de déploiement.  
  
 Si vous avez déjà déployé l'application, vous pouvez modifier cette valeur en exécutant un utilitaire de ligne de commande, BTSScnSSOApplicationConfig, dans le dossier SDK\Common\SsoApplicationConfig. Pour définir un nombre total de trois étapes, exécutez la ligne de commande suivante :  
  
 `BTSScnSSOApplicationConfig -set SouthRidgeVideo.CableOrder ConfigProperties TotalStages 3`  
  
 Étant donné que la solution met en cache les valeurs de configuration, vous devez patienter jusqu'au prochain intervalle d'actualisation pour que les nouvelles valeurs prennent effet.  
  
## <a name="versioning-schemas"></a>Gestion des versions de schémas  
 BizTalk utilise un schéma à partir de la version la plus récente de l'assembly qui le contient. Si vous créez une nouvelle version d'un schéma, cette action remplace définitivement toutes les versions précédentes de celui-ci. Cette opération est efficace lorsque les transactions sont de courte durée. Toutefois, les transactions dans la solution de gestion des processus d’entreprise sont de longue durées : une commande peut prendre jusqu'à une année à terminer.  
  
 Pour permettre l'emploi de plusieurs versions d'un schéma en cours d'utilisation, chaque schéma de la solution possède un numéro de version contenu dans son espace de noms. Par exemple, l'espace de noms du schéma Order est le suivant :  
  
```  
http://Microsoft.Samples.BizTalk.SouthridgeVideo.Schemas.Order.v1  
```  
  
 Étant donné qu'un espace de noms identifie un schéma et que l'ajout d'un numéro de version à l'espace de noms rend un schéma unique, un nouveau schéma sera différent de sa version plus ancienne. Ainsi, le nouveau schéma peut être utilisé sans remplacer l'ancienne version.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’une Solution de gestion des processus métiers](../core/developing-a-business-process-management-solution.md)