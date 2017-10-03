---
title: "Migration d’un projet BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a4dde72-6555-4bf6-b90e-676aa65312ff
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5ba2da42c6cbfad2b0c053aba296d34e38211fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="migrating-a-biztalk-server-project"></a>Migration d'un projet BizTalk Server
[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]les projets développés pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent être migrés vers les environnements plus récente à l’aide de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] conversion. Pour obtenir la liste des versions de migration pris en charge, consultez [pris en charge les chemins de mise à niveau et les Guides d’Installation](http://social.technet.microsoft.com/wiki/contents/articles/28554.biztalk-server-supported-upgrade-paths-and-installation-guides.aspx).  
  
## <a name="biztalk-project-changes-after-running-the-conversion-wizard"></a>Modifications apportées à un projet BizTalk après l'exécution de l'Assistant Conversion  
 Le tableau suivant montre comment [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] modification de noms de configuration de projet, et où déplacement de certaines propriétés de configuration spécifiques après le projet est converti en une version [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet. La plupart de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-paramètres de projet associés se trouvent sur le **déploiement** onglet du Concepteur de projet.  
  
|[!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]projet|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]projet|  
|------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|  
|**Incorporer les informations de suivi** propriété de configuration de sortie|**Définir la constante TRACE** option de conception la **générer** onglet du Concepteur de projet|  
|**Générer des informations de débogage** propriété de configuration de sortie|**Définir la constante DEBUG** option de conception la **générer** onglet du Concepteur de projet|  
|**Compatibilité BPEL** propriété de configuration de la génération de code|**Compatibilité BPEL** propriété de génération dans la fenêtre de propriétés de projet de code|  
  
> [!NOTE]
>  Projets BizTalk ont maintenant deux types de build : **version** et **déboguer**, qui remplace **développement** et **déploiement** de version antérieure versions. Toutefois, vous continuerez à voir les **développement** et **déploiement** configurations pour les projets qui sont migrés à partir de [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)].  
  
> [!CAUTION]
>  Uniquement si vous sélectionnez et \*. les fichiers de projet btproj.user sont sauvegardés en choisissant l’option lors de la conversion de la sauvegarde. Les autres fichiers doivent être sauvegardés manuellement.  
  
> [!CAUTION]
>  Les personnalisations apportées aux éléments générés automatiquement, comme les fichiers XSD ou ODX, seront perdues lors de la conversion. Cela s'applique également aux fichiers XSD générés lorsqu'une référence Web est ajoutée à un projet BizTalk.  
  
## <a name="project-migration-and-delay-signing"></a>Migration de projet et temporisation de la signature  
 [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)]les projets qui utilisent [signature différée](http://go.microsoft.com/fwlink/p/?LinkId=140992) peut échouer pendant le processus de génération après avoir été convertis pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela peut se produire si **générer l’assembly de sérialisation** paramètre de génération pour la configuration de projet migré n’est pas définie sur **hors**.  
  
## <a name="project-migration-and-msmqt"></a>Migration de projet et MSMQT  
 MSMQT ne fait désormais plus partie de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la manière dont cela peut affecter la migration d’un projet, consultez la rubrique [suppression de MSMQT](../core/msmqt-deprecation.md).  
  
## <a name="project-conversion-requires-the-project-and-solution-file"></a>Opération de conversion de projet demandant les fichiers de projet et de solution  
 Si vous tentez de convertir un projet [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] et que vous ne disposez pas du fichier de solution, vous recevrez le message d'erreur suivant :  
  
 **Erreur lors de la conversion du fichier de projet. Élément enfant \<BIZTALK > de l’élément \<VisualStudioProject > n’est pas valide.**  
  
 La conversion du projet nécessite le fichier de solution (.sln) du projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si le fichier de solution n'est pas disponible, vous devez alors en créer un à l'aide de [!INCLUDE[btsVStudioNet2005](../includes/btsvstudionet2005-md.md)], puis ajouter le projet [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] à la solution. Exécutez ensuite l'Assistant Conversion de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
> [!NOTE]
>  Vous serez peut-être en mesure de convertir le projet en utilisant uniquement le fichier projet (.btproj) avec Visual Studio.