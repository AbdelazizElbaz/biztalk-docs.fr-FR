---
title: "Comment déployer des définitions BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, definitions [BAM]
- managing [BAM definitions], deploying definitions
- definitions [BAM], deploying
- Deploy-All command [BAM]
ms.assetid: 02b8888c-6f6c-45dd-8445-6e507a02f5f0
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 094a37d90db41e505adeaec3a31ece9128785e04
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-deploy-bam-definitions"></a>Déploiement de définitions BAM
Les administrateurs utilisent la **déployer-all** commande d’utilitaire de gestion BAM pour déployer une définition BAM à partir du classeur Excel ou le fichier de définitions XML exporté à partir du classeur. Lorsque vous effectuez une installation complète de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], l'Assistant Configuration configure automatiquement le fichier XML de configuration BAM.  
  
> [!NOTE]
>  Si plusieurs utilisateurs travaillent avec le complément BAM pour Excel, ils doivent tous utiliser la même version de Microsoft Data Access Components (MDAC). À défaut, des problèmes de compatibilité risquent de se présenter. Notamment, si vous créez un modèle sur un ordinateur équipé de la dernière version de MDAC et que vous essayez ensuite de l'ouvrir sur un ordinateur équipé d'une version plus ancienne, une erreur du compilateur se produit.  
  
> [!NOTE]
>  Vous pouvez utiliser un seul élément de données (« ville » par exemple) par dimension de données (« situation géographique » par exemple). Ensuite, vous ne pouvez plus utiliser l'élément « ville » dans une autre dimension telle que la dimension « région ».  
  
> [!IMPORTANT]
>  Il est recommandé de vérifier la sécurité des classeurs Excel (.xls) du composant BAM avant de les déployer. Pour cela, utilisez Excel sur l'ordinateur d'administration. Avant de déployer un classeur, ouvrez-le et garantir la sécurité des macros est définie sur élevé, et qu’il n’y a pas d’avertissements.  
  
> [!IMPORTANT]
>  Dans les bases de données BAM, le « BAM_\<... \>« convention d’affectation de noms est réservée pour toutes les entités SQL (tables, index, procédures stockées, rôles, etc....). *Ne le faites pas* cette convention d’affectation de noms permet de créer des entités SQL ; une telle utilisation peut entraîner un comportement non défini.  
  
 Avant de déployer un fichier XML de définition BAM, vous devez vous assurer que les paramètres régionaux utilisés lors de sa création correspondent à ceux de l'ordinateur où vous le déployez. Par exemple, si vous créez le fichier sur un ordinateur exécutant une version japonaise de Microsoft Windows, les paramètres régionaux de l'ordinateur où vous effectuez le déploiement du fichier doivent également être définis sur Japonais. Si ces paramètres ne correspondent pas, vous devez modifier en conséquence les paramètres régionaux de l'ordinateur où vous exécutez l'utilitaire de gestion de l'analyse BAM, puis redémarrer l'ordinateur avant de lancer l'utilitaire.  
  
> [!NOTE]
>  Le fichier XML de définition BAM ne peut pas contenir de texte en plusieurs langues à moins que ces langues utilisent le même codepage, ou que seules deux langues soient utilisées, dont l'anglais.  
  
 Pour plus d'informations sur la modification des paramètres régionaux de votre ordinateur, reportez-vous à l'aide de votre système d'exploitation.  
  
### <a name="to-deploy-a-bam-definition"></a>Pour déployer une définition BAM  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant **C:\Program Files\Microsoft BizTalk Server \<version\>\Tracking** à l’invite de commandes. Appuyez sur **Entrée**.  
  
3.  Type **bm déployer-all - DefinitionFile :\<fichier de définition BAM\>**.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion BAM](../core/bam-management-utility.md)   
 [Recommandations de sécurité pour les services BAM](../core/bam-security-recommendations.md)