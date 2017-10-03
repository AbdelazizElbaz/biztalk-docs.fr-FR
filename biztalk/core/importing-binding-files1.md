---
title: Importation de liaison Files1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- CLASSPATH environment variable
- importing binding files
- cleaning target computer
ms.assetid: b2a9b19b-2d3d-45ea-bd92-a2501791b86a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fca64580b692f01834b48085aa2d88085fb743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a>importation des fichiers de liaison
Avant d'importer un fichier de liaison à l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vérifiez les éléments suivants :  
  
-   CLASSPATH pointe vers un emplacement particulier pour les fichiers spécifiques à PeopleSoft. Vérifiez que l’emplacement de ces fichiers est le même sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur, ou modifier le fichier de liaison.  
  
-   S'ils sont présents dans la configuration, les mots de passe du système PeopleSoft Enterprise sont enregistrés dans le fichier de liaison sous la forme *****. Pour plus d’informations, consultez [limitations concernant le déploiement](../core/deployment-limitations3.md).  
  
> [!NOTE]
>  Le déploiement remplace la configuration de l'emplacement de réception. Lorsque vous déployez un fichier de liaison et l’assembly sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
 Pour obtenir des instructions détaillées sur l'importation des fichiers de liaison, consultez la rubrique « Importation des liaisons dans un groupe BizTalk » dans la documentation [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="cleaning-the-target-computer"></a>Nettoyage de l'ordinateur cible  
 Pour nettoyer l'ordinateur cible afin de déployer la nouvelle application, procédez comme suit.  
  
#### <a name="to-clean-the-target-computer"></a>Pour nettoyer l'ordinateur cible  
  
-   Supprimez les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
     Si Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] n'est pas installé sur l'ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts suivants :  
  
     **\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove envoyer Port\VBScript\RemoveSendPort.vbs**  
  
     **\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove Port\VBScript\RemoveReceivePort.vbs de réception**  
  
     Par exemple, à une invite de commandes, exécutez :  
  
     **cscript RemoveSendPort.vbs \<nom du port d’envoi >**  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement de Ports et assemblys](../core/deploying-ports-and-assemblies5.md)