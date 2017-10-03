---
title: "Conditions préalables requises pour créer des applications d’Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b02ea286-f301-46b3-b748-d954dead23a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90eac318264f53e95aade98cf9574fc0eea45483
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="prerequisites-to-create-oracle-e-business-suite-applications"></a>Conditions préalables requises pour créer des applications d’Oracle E-Business Suite
Cette section fournit des informations sur la marche à suivre avant de développer des applications BizTalk à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Cette section pointe également vers le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils qui permettent de développer des applications BizTalk.  
  
## <a name="create-a-strong-named-key-file"></a>Créer un fichier de clé de nom fort

Vous devez créer un fichier de clé de nom fort pour générer des projets dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Un nom fort est constitué de l’identité du projet : son simple nom textuel, numéro de version et des informations de culture (le cas échéant), ainsi qu’une clé publique et une signature numérique. Le fichier de clé de nom fort contient la clé publique et la clé privée.  
  
> [!IMPORTANT]
>  Création d’un fichier de clé de nom fort est une tâche unique. Vous pouvez utiliser la même clé pour toutes les applications BizTalk que vous développez.  
  
### <a name="prerequisites"></a>Conditions préalables  
 Vous devez disposer de Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] installé sur l’ordinateur où vous souhaitez créer une clé de nom fort.  
  
### <a name="create-a-strong-name-key-file"></a>Créer un fichier de clé de nom fort  
  
1.  Ouvrez l’invite de commandes développeur pour Visual Studio.  
  
2.  À l’invite de commandes, accédez à l’emplacement où vous souhaitez créer le fichier de clé. Par exemple, tapez `cd C:\Sample`, puis appuyez sur ENTRÉE.  
  
3.  À l'invite de commandes, tapez `sn -k <key file name>.snk`, puis appuyez sur ENTRÉE.  
  
    > [!NOTE]
    >  Vous devez recevoir un message à l’invite de commandes signalant que la paire de clés a été écrite dans le fichier de clé de nom fort.  
  
4.  À l'invite de commandes, tapez `exit`, puis appuyez sur ENTRÉE.  
  
## <a name="learn-the-biztalk-server-tools"></a>Découvrez les outils de BizTalk Server

Les rubriques sur l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] dans [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md) sont écrits dans l’hypothèse que vous avez connaissance d’un nombre de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils. Vous allez utiliser les outils suivants pour développer des applications BizTalk à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
-   Microsoft [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)] 
  
-   Explorateur BizTalk  
  
-   Orchestration eesigner  
  
-   Concepteur de pipeline  
  
-   Mappeur BizTalk  
  
-   Console d’Administration de BizTalk Server  
  
### <a name="prerequisites"></a>Conditions préalables  
 Vous devez installer Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] avant de pouvoir accéder le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] outils.  
  
### <a name="biztalk-server-tools"></a>Outils de BizTalk Server  
 Le tableau suivant présente les rubriques de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation qui expliquent comment utiliser chacun des outils répertoriés.  
  
|Outil|Rubriques de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] documentation de base|  
|---|---|  
|[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]|-   [À l’aide de Visual Studio](../../core/using-visual-studio.md) <br />-   [Utilisation des projets BizTalk](../../core/working-with-biztalk-projects.md)<br />-   [Déploiement d’assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md)<br /><br /> En savoir plus sur les solutions de Visual Studio, projets et les éléments à [Solutions et projets dans Visual Studio](https://msdn.microsoft.com/library/b142f8e7.aspx).|  
|Concepteur d'orchestration|[Création d’orchestrations à l’aide du Concepteur d’orchestration](../../core/creating-orchestrations-using-orchestration-designer.md)|  
|Concepteur de pipeline| [Création de pipelines à l’aide du Concepteur de pipeline](../../core/creating-pipelines-using-pipeline-designer.md)|  
|Mappeur BizTalk| [Création de mappages à l’aide du Mappeur BizTalk](../../core/creating-maps-using-biztalk-mapper.md)|  
|Console d’Administration de BizTalk Server|[Utilisation de la console Administration de BizTalk Server](../../core/using-the-biztalk-server-administration-console.md)|  
  
## <a name="next"></a>Suivant

[Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)  