---
title: "Implémentation d’une stratégie de contrôle de version | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a3c7af6-6277-4667-8f14-e6d1cb9e99d4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03bab9863107b26df615af1b51398ca4c314ee3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-a-versioning-strategy"></a>Implémentation d’une stratégie de contrôle de version
Le contrôle de version est le fait de la mise à jour de l’implémentation d’un artefact et incrémentation de son numéro de version.  
  
## <a name="general-versioning-issues"></a>Problèmes généraux de contrôle de version  
 Versioning d’application BizTalk peut devenir un problème lorsque vous devez exécuter deux versions d’une solution BizTalk côte à côte, ou si vous ne pouvez pas planifier des interruptions de service BizTalk pour déployer une nouvelle version. Si vous n’avez pas besoin d’exécuter deux versions de la solution simultanément (par exemple, si vous ne disposez d’aucune orchestration à long terme), il est parfaitement acceptable d’annuler le déploiement de l’ancienne version et de déployer la nouvelle version en tant qu’une stratégie de contrôle de version (aucun contrôle de la version de l’assembly). Il s’agit d’une stratégie de contrôle de version possibles, bien que nous vous recommandons quand même d’incrémenter le numéro de version de fichier (pour vous permettre de savoir quelle version est déployée sur les serveurs BizTalk Server). Pour plus d’informations sur la mise à jour d’une application est déployée, consultez [liste de vérification : mise à jour d’un Assembly](../technical-guides/checklist-updating-an-assembly.md).  
  
 Si vous avez besoin prendre en charge les orchestrations longues ou vous devez effectuer des déploiements d’applications BizTalk sans temps d’arrêt des applications BizTalk, puis une stratégie de contrôle de version de BizTalk solide doit être implémentée et utilisée de bout en bout pour les différents scénarios de contrôle de version. Cela inclut le versioning des assemblys .NET et le contrôle de version de tous les artefacts de BizTalk. Cela inclut les schémas, mappages, pipelines, les composants de pipeline, orchestrations, des adaptateurs personnalisés, les classes personnalisées orchestrations appelées dans et cartes, des règles d’entreprise et BAM. Pour plus d’informations sur le contrôle de version côte à côte, consultez [mise à jour à l’aide du contrôle de version côte à côte](../technical-guides/updating-using-side-by-side-versioning.md).  
  
## <a name="versioning-an-assembly"></a>Contrôle de version un Assembly  
 Lorsque vous mettez à jour un assembly, vous avez le choix entre les éléments suivants :  
  
-   Choix d’une version d’assembly fixe pour un produit et en incrémentant uniquement le numéro de version de fichier.  
  
-   Incrémentation de la version d’assembly et la version du fichier au cours du développement.  
  
 Ces approches sont comparées dans le tableau suivant :  
  
|**Version d’assembly fixe, version de fichier dynamique**|**Version de l’assembly dynamique, version de fichier fixe ou dynamique**|  
|------------------------------------------------------|-----------------------------------------------------------------|  
|Le numéro de version d'assembly est un  numéro fixe.<br /><br /> Le numéro de version du fichier est un numéro généré.|Le numéro de version d'assembly est un numéro généré.<br /><br /> Le numéro de version du fichier est un numéro généré.|  
|Exécution de BizTalk Server peut récupérer une version incorrecte de l’assembly si plusieurs assemblys sont installés.|BizTalk Server s’exécute toujours la dernière version de l’assembly, même si plusieurs assemblys sont installés.|  
|Une seule version de la solution peut être déployée à tout moment.|Différentes versions de la solution peuvent être déployées côte à côte (bien que les autres aspects de la solution, tels que des définitions de schéma, peuvent entrer en conflit).|  
|L'hôte BizTalk doit être redémarré pour forcer le chargement des assemblys mis à jour.|Force BizTalk Server pour charger les nouveaux assemblys.|  
|Cette configuration facilite la création d'un déploiement, car les fichiers qui référencent le numéro de version de l'assembly (par exemple, les fichiers de liaison et les modèles de suivi) n'ont pas besoin d'être modifiés.|Cette configuration rend la création d'un déploiement plus complexe, car les fichiers qui référencent le numéro de version de l'assembly doivent être mis à jour pour correspondre à la nouvelle version.|  
  
 Vous pouvez choisir d’utiliser la version d’assembly fixe et une nouvelle approche de version de fichier dynamique si vous êtes un système de prototypage ou le développement d’un autre type de projet qui n’est pas libérée. Si l'application en cours d'élaboration n'est pas destinée à être livrée à un utilisateur final, vous pouvez rationnaliser les tâches de déploiement et réduire le nombre des dépendances rompues en fixant la version de l'assembly et en incrémentant le numéro de version de fichier. Pour un suivi des versions, n'oubliez pas d'incrémenter le numéro de version de fichier pour chaque version.  
  
 Si vous travaillez sur un projet destiné à un utilisateur final, il est préférable d'incrémenter le numéro de version d'assembly et, éventuellement, de stocker un numéro de version de fichier significatif. Cette solution demande un peu plus de travail, car il vous faut modifier les numéros de version et les dépendances associées. En revanche, elle garantit que les versions d'assembly utilisées sont bien les plus récentes. Grâce aux scripts de déploiement automatisés, vous pouvez réduire l'incidence de la gestion des versions sur votre système. Pour afficher des exemples de déploiement, consultez [déploiement d’Application (dossier d’exemples BizTalk Server)](http://go.microsoft.com/fwlink/?LinkId=155134) (http://go.microsoft.com/fwlink/?LinkId=155134) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
> [!NOTE]  
>  Vous devez choisir le mécanisme de contrôle de version qui garantit que la bonne fichiers sont remis et qui simplifie la maintenance et les améliorations.  
  
 Pour plus d’informations sur les problèmes de contrôle de version, consultez [versions de projet BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=154209) (http://go.microsoft.com/fwlink/?LinkID=154209) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.