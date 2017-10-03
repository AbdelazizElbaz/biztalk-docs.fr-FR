---
title: Pipelines | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines
- deploying, pipelines
- receive pipelines, about receive pipelines
- pipelines, deploying
- send pipelines, about send pipelines
- receive pipelines
- pipelines, about pipelines
- send pipelines, stages
- send pipelines
- pipelines, receive pipelines
- pipelines, send pipelines
- receive pipelines, stages
ms.assetid: 76947dd8-728a-4fa3-bd33-7a708ae82cac
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5fec49dcc9ba21c5d117188f280f7e9b65fe2b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pipelines"></a>Pipelines
Les pipelines sont un composant de Microsoft BizTalk Server qui fournit une implémentation du modèle d'intégration de canaux et de filtres. Pendant la réception et l'envoi de messages, plusieurs raisons justifient les opérations de transformation sur des messages en vue de les préparer à entrer dans BizTalk Server ou à en sortir.  
  
 Un exemple courant est la transformation d'un fichier plat délimité par des virgules en fichier XML pour permettre à ce fichier d'utiliser certaines fonctionnalités de BizTalk Server, telles que les mappages. C'est exactement le rôle du composant Désassembleur de fichier plat. Les scénarios d'intégration exigent souvent que les messages subissent plusieurs transformations avant de pouvoir être envoyés ou reçus. Les pipelines répondent à ces besoins. En effet, ils permettent aux développeurs de définir la série de transformations à effectuer sur un message lors de son envoi ou de sa réception.  
  
 Il existe deux types de pipelines : les pipelines d'envoi et les pipelines de réception. Ils correspondent aux ports dans lesquels ils s'exécutent. *Pipelines d’envoi* sont exécutés dans les ports d’envoi et de port de réception dans la partie de la réponse d’une demande/réponse pendant *pipelines de réception* sont exécutées dans emplacements de réception et dans la partie de la réponse d’une sollicitation-réponse port d’envoi. Les pipelines de réception sont principalement destinés à la transformation des messages en cours de publication sur la base de données MessageBox, alors que les pipelines d'envoi sont destinés à être utilisés pour des messages faisant l'objet d'un abonnement et envoyés de BizTalk Server.  
  
 Chaque pipeline se compose d'un ensemble d'étapes qui sont exécutées dans l'ordre lors de l'exécution du pipeline. Chaque étape peut contenir plusieurs composants ou aucun. Le nombre maximal de composants est fonction de l'étape.  
  
## <a name="receive-pipeline-stages"></a>Étapes d'un pipeline de réception  
 ![Étapes du pipeline de réception](../core/media/arch-pipe-receive.gif "arch_pipe_receive")  
  
|Étape|Fonction|  
|-----------|-------------|  
|**Décoder**|Décrypte ou décode les données du message.|  
|**Désassembler**|Désassemble un échange en petits messages et analyse le contenu du message.|  
|**Valider**|Valide les données du message, généralement par rapport à un schéma.|  
|**Résoudre le tiers**|Identifie le tiers BizTalk Server associé à certain jeton de sécurité dans le message ou le contexte du message.|  
  
## <a name="send-pipeline-stages"></a>Étapes du Pipeline d’envoi  
 ![Étapes du pipeline d’envoi](../core/media/arch-pipe-send.gif "arch_pipe_send")  
  
|Étape|Fonction|  
|-----------|-------------|  
|**Préassembler**|Effectue tout le traitement de message nécessaire avant d'assembler le message.|  
|**Assembler**|Assemble le message et le prépare pour la transmission au moyen d'actions, telles que l'ajout d'enveloppes, la conversion du format XML au format de fichier plat, ainsi que d'autres tâches complémentaires à l'étape de désassemblage du pipeline de réception.|  
|**Encoder**|Code ou crypte le message avant qu'il ne soit remis.|  
  
 Une étape dans un pipeline a un *mode d’exécution* de tous ou PremièreCorrespondance, qui contrôle les composants qui sont exécutées si plus d’un composant est ajouté à une étape. Dans le cas des étapes s'exécutant en mode Tous, chaque composant est appelé pour traiter le message dans l'ordre dans lequel il est configuré au sein de l'étape. En mode PremièreCorrespondance, chaque composant est interrogé pour déterminer lequel d'entre eux correspond. Lorsque le composant correspondant est trouvé, il est exécuté alors que les composant restant ne le sont pas.  
  
 Pour illustrer l'explication, voici quelques exemples de mode d'exécution : l'étape Désassembler d'un pipeline de réception est une étape PremièreCorrespondance dans la mesure où chaque composant de l'étape est appelé pour déterminer lequel d'entre eux reconnaît le message et est capable de le traiter. Si la réponse d'un composant est affirmative, les composants suivants de l'étape ne sont pas interrogés. En revanche, l'étape Décoder d'un pipeline de réception s'exécute en mode Tous, car tous les composants sont appelés pour traiter le message dans l'ordre dans lequel ils ont été configurés. Le premier composant peut par exemple décrypter le message alors que le second peut décompresser un message contenu dans un fichier zip.  
  
 Une conséquence courante du mode d'exécution au cours du traitement d'un pipeline se produit lorsque le développeur souhaite utiliser plusieurs désassembleurs dans un seul pipeline de réception. Il est fréquent que les composants de désassemblage présentent de légères différences, par exemple deux désassembleurs de fichiers plats comportant des schémas configurés similaires cependant différents. Dans ce cas, bien que le message puisse correspondre au schéma défini dans le second désassembleur, le premier peut déterminer grâce au sondage, qu'il peut traiter le message. Ce n'est qu'au terme du traitement du message qu'une erreur est découverte et que le message est suspendu. Dans cette situation, vous pouvez soit créer un désassembleur doté d'une logique de sondage plus spécifique, soit créer deux pipelines distincts qui traiteront des messages différents provenant d'emplacements différents.  
  
## <a name="pipeline-deployment"></a>Déploiement de pipeline  
 Lorsque vous déployez un assembly qui contient un pipeline, la base de données de gestion enregistre le pipeline. Celui-ci est associé à la version spécifique de l'assembly et présente les résultats suivants :  
  
-   Si vous déployez plusieurs assemblys qui utilisent le même pipeline, la base de données de gestion crée une entrée de pipeline pour chaque assembly.  
  
-   Lorsque vous supprimez un assembly qui contient un pipeline, la base de données de gestion supprime le pipeline associé à l'assembly. Comme une copie du pipeline existe pour chaque assembly associé dans la base de données de gestion, la suppression d'un pipeline n'a pas d'incidence sur les autres assemblys.  
  
## <a name="see-also"></a>Voir aussi  
 [Artefacts](../core/artifacts.md)