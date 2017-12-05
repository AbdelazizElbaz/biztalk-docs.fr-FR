---
title: "Mode de déploiement des assemblys dans BizTalk Server | Documents Microsoft"
description: "Déployer des assemblys dans le GAC et activer le contrôle de version pour les assemblys dans BizTalk Server"
ms.custom: 
ms.date: 01/21/2016
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7f99ed5-b64a-4a38-99d7-83070fb69030
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb6c787219855ca219808fc1e95c0caefbf12a9d
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="biztalk-assemblies"></a>Assemblys BizTalk
L'aspect le plus important de Microsoft BizTalk Server et de .NET FRAMEWORK est que tous les artefacts BizTalk Server, à savoir les mappages, schémas, orchestrations et pipelines, sont compilés dans des assemblys .NET. Les deux principales implications d'une telle conception sont que ces assemblys doivent avoir des noms forts. De ce fait, ils suivent également les règles d'établissement de versions .NET. La principale implication de tout ceci est qu'un projet BizTalk, une fois élaboré à partir d'une version donnée d'un autre projet .NET ou assembly (incluant des projets BizTalk), continue à utiliser cette version jusqu'à ce qu'il soit reconstruit à partir d'une version plus récente.  
  
## <a name="net-versioning-and-assemblies"></a>Établissement de versions .NET et assemblys  
 Un problème d'établissement de versions .NET se produit fréquemment pendant le développement lorsque les numéros de version d'un projet BizTalk ne sont pas modifiés et que l'assembly est redéployé sans arrêter et démarrer l'instance de l'hôte BizTalk dans laquelle les types sont chargés.  
  
 Quand le processus est exécuté à nouveau, les modifications ne prennent pas effet. Ceci est dû au mode de chargement en mémoire des assemblys .NET. Dans la mesure où l'hôte possède déjà une copie de l'assembly en mémoire, il ne recharge pas ce dernier lorsqu'une nouvelle copie est placée dans le Global Assembly Cache. Par exemple, si la version 1.0.0.0 d'un assembly avec orchestration est déployée et exécutée, et que des modifications sont apportées à l'orchestration mais que le numéro de version n'est pas modifié, les modifications ne prennent pas effet. Une fois l'instance de l'hôte arrêtée, la copie en mémoire de l'assembly est publiée. Ensuite, lorsque l'instance de l'hôte redémarre, elle recharge la copie nouvelle de l'assembly et reçoit les modifications. Si une nouvelle version, par exemple la version 2.0.0.0, a été déployée et chargée, les modifications prennent alors effet.  
  
 Le déploiement d'assemblys sur BizTalk Server est un processus en deux parties. La première étape consiste à déployer l'assembly .NET traditionnel dans lequel l'assembly avec nom fort est déployé sur le GAC de chacun des serveurs sur lesquels l'assembly sera utilisé. La deuxième étape consiste à déployer les métadonnées relatives aux assemblys et à leur type dans la base de données de gestion BizTalk Server. Lorsque des assemblys BizTalk Server sont chargés par BizTalk Server, ils sont en général chargés en utilisant leur nom fort, stocké dans la base de données de gestion.  
  
## <a name="deploying-biztalk-server-assemblies-to-the-gac"></a>Déploiement d'assemblys BizTalk Server sur le GAC  
 Les artefacts BizTalk Server créés par un développeur sont compilés dans des classes qui dérivent de types BizTalk Server intégrés. Par exemple, une orchestration devient une classe qui dérive de la classe Microsoft.BizTalkXLANGs.BTXEngine.BTXService. Ceci s'explique par le fait que ces classes de base sont déployées dans des assemblys sur le GAC, lesquels ont des dépendances avec d'autres assemblys du GAC que leur développeur doit également déployer sur le GAC.  
  
 Une autre implication importante des artefacts BizTalk Server déployés dans le Global Assembly Cache et portant par conséquent un nom fort est que les assemblys avec nom fort ne peuvent pas appeler d'autres assemblys qui n'ont pas de nom fort. Cela signifie que tout assembly créé par un développeur et utilisé par ces assemblys BizTalk Server doit également porter un nom fort. De la même manière, les assemblys déployés sur le GAC et qui chargent d'autres assemblys sans utiliser de chemin d'accès spécifique doivent charger ces assemblys à partir du GAC.  
  
 Les composants de pipeline sont ajoutés à la boîte à outils d'un développeur dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ce qui permet de les déplacer par simple glisser sur le Concepteur de pipeline. Lorsqu'un pipeline BizTalk Server est compilé dans un assembly .NET, les informations relatives à tous les composants intervenant aux différentes étapes du pipeline sont compilées dans l'assembly. Lorsque ce pipeline est déployé sur BizTalk Server, les informations relatives aux composants, y compris leur nom de fichier sont insérées dans la base de données de gestion BizTalk et l’assembly de pipeline est déployé dans le GAC. Tous les assemblys qui dépendent de composants de pipeline BizTalk doivent également être déployés dans le GAC pour pouvoir être trouvé lors de l’exécution. Les assemblys de composant de pipeline doivent également être copiés dans le répertoire de composants de BizTalk Server\Pipeline doit être accessible par un pipeline BizTalk lors de l’exécution. Lorsque le pipeline est exécuté, ces composants sont chargés et les interfaces qu'ils implémentent sont appelées selon le besoin.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture d’exécution](../core/runtime-architecture.md)