---
title: "Contrôle de version de projet BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dcdd5354-6335-4320-adbf-28ac934c9ce6
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1893509d569dc74bf8d6d28680026ebe90ba9149
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-project-versioning"></a>Gestion des versions du projet BizTalk Server
Lorsque vous développez un projet BizTalk à l'aide de [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], la gestion des versions est sous-tendue par un ensemble standard de règles permettant de minimiser l'incidence d'un changement dans le numéro de version. Selon la manière dont un [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]application ou un composant est déployé, dépendances peuvent être gérées par un fichier de configuration d’application, par le biais d’une installation XCOPY ou par d’autres [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] mécanismes de déploiement. Comme le démontrent les sections ci-après, la gestion des versions et des dépendances dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est complexe.  
  
## <a name="implications-of-changing-version-numbers"></a>Implications d'un changement du numéro de version  
 En général, lors d'un développement [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)], le numéro de version de l'assembly est mis à jour pour correspondre au numéro de version actuel lorsqu'une mise à jour est effectuée. Cependant, lors du développement d'une solution BizTalk, le changement du numéro de version de l'assembly peut entraîner une rupture de la relation entre l'assembly et les éléments dépendants qui font référence au fichier DLL en utilisant le numéro de version. Le tableau suivant répertorie les éléments qui font référence à un assembly [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en utilisant son numéro de version ainsi que les différentes implications d'un changement du numéro de version.  
  
|Entité|Implications du changement dans le numéro de version de l'assembly|  
|------------|------------------------------------------------|  
|Fichiers de liaison|Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de liaison qui font référence à cet assembly. Cela est dû au fait que le fichier de liaison fait référence à l'assembly au moyen d'attributs qui comprennent le numéro de version.<br /><br /> Vous pouvez mettre à jour les informations de version dans le fichier de liaison à l'aide du Bloc-notes ou d'un autre éditeur. Il est également possible de redéployer la solution, puis de régénérer le fichier de liaison à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Enfin, vous avez la possibilité d'utiliser des scripts pour automatiser le déploiement et la gestion des versions. Pour plus d’informations sur le déploiement, consultez [déploiement et la gestion des Applications BizTalk](../core/deploying-and-managing-biztalk-applications.md).|  
|Fichiers de définition du modèle de suivi BAM (.btt)|Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de définition du modèle de suivi BAM. Étant donné que les fichiers de suivi BAM sont dans un format binaire, ils ne peuvent pas être modifiés et doivent donc être régénérés. Si les modèles de suivi BAM sont nécessaires, il vous faut respecter l'une ou l'autre de ces instructions :<br /><br /> -Évitez fréquemment mise à jour des numéros de version pendant le processus de génération.<br />-Retarder la création de profils de suivi jusqu'à ce que les numéros de version sont stables BAM.|  
|Services Web publiés à l'aide de l'Assistant Publication de services Web|Lorsque l'Assistant Publication de services Web est utilisé pour créer une interface Web ASP.NET, la version de l'assembly [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est incluse dans le code source d'ASP.NET. Le numéro de version d’assembly est utilisé au moment de l’exécution par l’interface ASP.NET dans le cadre de la **bodyTypeAssemblyQualifiedName** propriété de l’opération de service Web. Si le numéro de version de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] modifications assembly sans mettre à jour le **bodyTypeAssemblyQualifiedName** propriété, puis Web suivantes seront rejetées par les opérations de service [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].<br /><br /> Lorsque l'emplacement de réception utilise le pipeline XmlDefaultPipeline, l'abonnement se réfère au type de document. Ce dernier se sert des informations d'assembly incorporées et il échoue si l'assembly n'existe pas. Si le pipeline utilisé est PassThruPipeline (pipeline par défaut lorsqu'un port est exposé et que l'Assistant crée de lui-même l'emplacement de réception), l'abonnement ignore ces informations d'assembly incorporées.|  
  
 Pour en savoir plus sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assemblys et le déploiement, consultez [assemblys BizTalk](../core/biztalk-assemblies.md).  
  
## <a name="approaches-to-versioning"></a>Traitement de la gestion des versions  
 Lors de la planification d'un projet, il existe deux options possibles :  
  
-   utiliser une version d'assembly fixe pour un produit fini où seul le numéro de version du fichier est modifié par incrémentation ;  
  
-   incrémenter la version de l'assembly ainsi que la version du fichier au cours du développement.  
  
 Vous trouverez ci-après un tableau comparatif détaillant ces deux possibilités.  
  
|Version d'assembly fixe / version de fichier dynamique|Version d'assembly dynamique / version de fichier fixe ou dynamique|  
|--------------------------------------------------|-------------------------------------------------------------|  
|Le numéro de version d'assembly est un  numéro fixe.<br /><br /> Le numéro de version du fichier est un numéro généré.|Le numéro de version d'assembly est un numéro généré.<br /><br /> Le numéro de version du fichier est un numéro généré.|  
|Lors de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il se peut que la version d'assembly sélectionnée soit incorrecte si plusieurs assemblys sont installés.|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] exécute toujours la dernière version de l'assembly, même si plusieurs assemblys sont installés.|  
|Une seule version de la solution peut être déployée à tout moment.|Des versions différentes de la solution peuvent être déployées côte à côte. Néanmoins, d'autres aspects de la solution, tels que les définitions de schéma, peuvent entrer en conflit.|  
|L'hôte BizTalk doit être redémarré pour forcer le chargement des assemblys mis à jour.|Force [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à charger les nouveaux assemblys.|  
|Cette configuration facilite la création d'un déploiement, car les fichiers qui référencent le numéro de version de l'assembly (par exemple, les fichiers de liaison et les modèles de suivi) n'ont pas besoin d'être modifiés.|Cette configuration rend la création d'un déploiement plus complexe, car les fichiers qui référencent le numéro de version de l'assembly doivent être mis à jour pour correspondre à la nouvelle version.|  
  
 Si vous élaborez un prototype pour votre système ou que vous développez tout autre type de projet qui n'est pas destiné à la production, vous pouvez opter pour la solution qui consiste à utiliser un numéro de version d'assembly fixe et un numéro de version de fichier dynamique. Si l'application en cours d'élaboration n'est pas destinée à être livrée à un utilisateur final, vous pouvez rationnaliser les tâches de déploiement et réduire le nombre des dépendances rompues en fixant la version de l'assembly et en incrémentant le numéro de version de fichier. Pour un suivi des versions, n'oubliez pas d'incrémenter le numéro de version de fichier pour chaque version.  
  
 Si vous travaillez sur un projet destiné à un utilisateur final, il est préférable d'incrémenter le numéro de version d'assembly et, éventuellement, de stocker un numéro de version de fichier significatif. Cette solution demande un peu plus de travail, car il vous faut modifier les numéros de version et les dépendances associées. En revanche, elle garantit que les versions d'assembly utilisées sont bien les plus récentes. Grâce aux scripts de déploiement automatisés, vous pouvez réduire l'incidence de la gestion des versions sur votre système. Pour afficher des exemples de déploiement, consultez [déploiement d’Application (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md).  
  
> [!NOTE]
>  Choisissez le mécanisme de gestion des versions qui garantit que les fichiers appropriés sont livrés correctement et qui simplifie la maintenance et les améliorations.  
  
## <a name="map-function-version-numbering"></a>Numérotation des versions de la fonction de mappage  
 Les assemblys .NET qui peuvent être appelées depuis un mappage à l’aide de la **script** fonctoid. Cela apporte une grande flexibilité et permet au développeur de résoudre de nombreux problèmes relatifs au mappage personnalisé. En outre, une seule contrainte est imposée pour le mappage : il doit, de manière interne, faire référence au nom du type d'assembly ainsi qu'au numéro de version complet de l'assembly invoqué. Cela signifie que, si le numéro de version de l'assembly appelé par le mappage change, tous les liens qui font référence à cet assembly sont rompus.  
  
 Pour éviter ce type de difficulté lorsqu'il est nécessaire d'appeler des assemblys dans un mappage, il est conseillé de créer un assembly consacré à la fonctionnalité de mappage et de fixer le numéro de version de cet assembly. Ainsi, la version d'assembly des autres fonctions d'assistance peut être mise à jour sans supprimer les mappages.  
  
 Si un assembly référencé dans un mappage est modifié après le développement des mappages, pensez à mettre à jour le fichier de mappage hors de l'Éditeur de mappage pour répercuter les numéros de version mis à jour.  
  
#### <a name="to-use-notepad-to-modify-the-map-file-to-reflect-updated-version-numbers"></a>Pour utiliser le Bloc-notes afin de modifier le fichier de mappage permettant de mettre à jour les numéros de version  
  
1.  À l’aide de la **Démarrer** menu, lancez le bloc-notes.  
  
2.  Dans le bloc-notes, sur le **fichier** menu, cliquez sur **ouvrir**. Dans le **ouvrir** boîte de dialogue, sélectionnez le fichier de mappage que vous souhaitez modifier, puis cliquez sur **ouvrir**.  
  
3.  Dans le menu **Edition** , cliquez sur **Rechercher**. Dans le **trouver** boîte de dialogue, entrez **Assembly =**, puis cliquez sur **suivant**.  
  
4.  S'il existe une référence de script à un assembly externe, le Bloc-notes doit rechercher un élément XML tel que :  
  
    ```  
    <Script Language="ExternalAssembly" Assembly="Contoso.Scripts, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c5145e4e089" Class="Contoso.Scripts" Function="CalculateValue" AssemblyPath="Contoso.Scripts.dll"/>  
    ```  
  
     Mettez à jour le numéro de version. S’il existe plusieurs instances, utilisez **remplacer** sur la **modifier** menu.  
  
5.  Enregistrez le fichier.  
  
     Vous pouvez maintenant ouvrir le mappage à l'aide de l'Éditeur de mappage.  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques pour déployer une Application BizTalk](../core/best-practices-for-deploying-a-biztalk-application.md)   
 [Admin (dossier d’exemples BizTalk Server)](../core/admin-biztalk-server-samples-folder.md)   
 [Déploiement et démarrage d’une nouvelle Version d’une Orchestration par programme](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md)