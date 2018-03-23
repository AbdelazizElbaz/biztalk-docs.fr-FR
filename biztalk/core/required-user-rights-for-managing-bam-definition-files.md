---
title: Droits d’utilisateur requis pour la gestion des fichiers de définition BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb4fb73f-b783-4a04-9bd6-a135b3dd2655
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5e39c86eec0cf198a5b879cbc98d29321de71dc
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="required-user-rights-for-managing-bam-definition-files"></a>Droits d'utilisateur requis pour gérer les fichiers de définition BAM
Les fichiers de définition BAM peuvent être créés, gérés et consultés par les utilisateurs de n'importe quel rôle. La gestion des fichiers de définition BAM implique leur déploiement et leur suppression ainsi que la gestion des activités, des vues, des alertes et des artefacts qui leur sont associés.  
  
 Il est recommandé aux administrateurs d'assurer une protection correcte des actifs, par exemple en créant des dossiers partagés à l'accès protégé par des autorisations. Nous enjoignons également les utilisateurs faisant appel au complément BAM pour Excel qu'ils définissent le niveau de sécurité des macros sur « élevé ».  
  
 Aucun droit d'utilisateur n'est requis pour modifier les fichiers de définition BAM (en fonction des autorisations définies là où les fichiers de définition sont stockés). Les modifications apportées aux fichiers de définition ne sont pas automatiquement appliquées à l'infrastructure BAM. Pour appliquer ces modifications, vous devez utiliser l'utilitaire de gestion de l'analyse BAM.  
  
 Pour vous servir de l'utilitaire de gestion de l'analyse BAM, vous devez être administrateur sur l'ordinateur sur lequel la définition BAM est appliquée, ou membre du groupe d'administrateurs BizTalk Server.  
  
> [!NOTE]
>  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Qu’est une définition BAM ?](../core/what-is-a-bam-definition.md)   
 [Comment déployer des définitions BAM](../core/how-to-deploy-bam-definitions.md)