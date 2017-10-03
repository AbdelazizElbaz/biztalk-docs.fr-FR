---
title: "Problèmes connus avec la mise à jour des Applications et artefacts | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 220ea03c-d453-40cc-8ddb-18a96f8ddfe5
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a42fb3ca8381faedbd2283b9f4d297738bbb040d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-updating-applications-and-artifacts"></a>Problèmes connus avec la mise à jour des Applications et des artefacts
## <a name="updating-an-application"></a>Mise à jour d’une Application  
 **Suppression d’un artefact ne le supprime pas de tous les emplacements**  
  
 La suppression d'un artefact l'élimine des bases de données BizTalk Server de sorte qu'il n'apparaît plus ni dans la console d'administration, ni dans la liste des artefacts d'une application générée par la commande BTSTask ListApp. Elle ne supprime pas l’artefact à partir du Registre Windows, le global assembly cache (GAC), un répertoire virtuel ou le système de fichiers, s’il existe dans ces emplacements. Dans le cas des ports d'envoi, des groupes de ports d'envoi, des ports de réception et des emplacements de réception, qui n'existent que dans la base de données de gestion BizTalk, cette opération efface entièrement l'artefact.  
  
## <a name="updating-an-artifact"></a>Mise à jour d’un artefact  
 **Suppression ou modification de l’état d’un artefact peut entraîner une application de fonctionner**  
  
 Lorsque vous ajoutez une référence à partir d’une application à l’autre et apportez des modifications à l’état d’un artefact sur lesquels dépend d’une autre application ou supprimer de l’artefact, l’application qui possède la dépendance ne fonctionnera pas correctement. Pour plus d’informations sur la modification de l’état d’un artefact, consultez la section sur l’artefact approprié dans [la gestion des artefacts](http://go.microsoft.com/fwlink/?LinkID=154725) (http://go.microsoft.com/fwlink/?LinkID=154725).  
  
 **Fichiers de stratégie .NET ne sont pas pris en charge.**  
  
 L'utilisation des fichiers de stratégie .NET n'est pas prise en charge dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. En effet, il arrive que les fichiers de stratégie ne fonctionnent pas comme prévu. Ils redirigent .NET vers une version de l’assembly spécifié dans le GAC, mais [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accède souvent aux assemblys et les données des artefacts à partir d’un cache ou la base de données de gestion BizTalk. En fonction du type d'artefact, de la mise en cache et du redémarrage ou non des instances d'hôte, les fichiers de stratégie peuvent ne pas répondre correctement.  
  
## <a name="updating-an-assembly"></a>Mise à jour d’un Assembly  
 **Modifications apportées à un assembly ne prendront effet si l’hôte n’est pas arrêté.**  
  
 Assemblys BizTalk doivent respecter les règles de contrôle de version de .NET. La principale implication de tout ceci est qu'un projet BizTalk, une fois élaboré à partir d'une version donnée d'un autre projet .NET ou assembly (incluant des projets BizTalk), continue à utiliser cette version jusqu'à ce qu'il soit reconstruit à partir d'une version plus récente.  
  
 Un problème d'établissement de versions .NET se produit fréquemment pendant le développement lorsque les numéros de version d'un projet BizTalk ne sont pas modifiés et que l'assembly est redéployé sans arrêter et démarrer l'instance de l'hôte BizTalk dans laquelle les types sont chargés.  
  
 Quand le processus est exécuté à nouveau, les modifications ne prennent pas effet. Ceci est dû au mode de chargement en mémoire des assemblys .NET. Étant donné que l’ordinateur hôte dispose déjà d’une copie en mémoire de l’assembly, il ne recharge pas l’assembly lorsqu’une nouvelle copie est placée dans le global assembly cache (GAC). Par exemple, si la version 1.0.0.0 d'un assembly avec orchestration est déployée et exécutée, et que des modifications sont apportées à l'orchestration mais que le numéro de version n'est pas modifié, les modifications ne prennent pas effet. Une fois l'instance de l'hôte arrêtée, la copie en mémoire de l'assembly est publiée. Ensuite, lorsque l'instance de l'hôte redémarre, elle recharge la copie nouvelle de l'assembly et reçoit les modifications. Si une nouvelle version a été déployée, par exemple la version 2.0.0.0 et il a été chargé, puis la modification entrera en vigueur.  
  
 **Modification de la version de l’assembly peut rompre la relation entre un assembly et les éléments qui y font référence à la version**  
  
 Dans le développement de .NET Framework, il est courant de mettre à jour le numéro de version d’assembly pour le numéro de build en cours lorsqu’une génération se produit. Cependant, lors du développement d'une solution BizTalk, le changement du numéro de version de l'assembly peut entraîner une rupture de la relation entre l'assembly et les éléments dépendants qui font référence au fichier DLL en utilisant le numéro de version. Le tableau suivant répertorie les éléments qui font référence à un assembly BizTalk Server à l’aide de son numéro de version et l’effet de la modification d’un numéro de version d’assembly.  
  
|Entité|Implications du changement dans le numéro de version de l'assembly|  
|------------|------------------------------------------------|  
|Fichiers de liaison|Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de liaison qui font référence à cet assembly. Cela est dû au fait que le fichier de liaison fait référence à l'assembly au moyen d'attributs qui comprennent le numéro de version.<br /><br /> Vous pouvez mettre à jour les informations de version dans le fichier de liaison à l'aide du Bloc-notes ou d'un autre éditeur. Vous pouvez également redéployez la solution et puis régénérer le fichier de liaison à l’aide de la console Administration de BizTalk Server. Enfin, vous avez la possibilité d'utiliser des scripts pour automatiser le déploiement et la gestion des versions. Pour plus d’informations sur le déploiement, consultez [déploiement et la gestion des Applications BizTalk](http://go.microsoft.com/fwlink/?LinkID=154210) (http://go.microsoft.com/fwlink/?LinkID=154210).|  
|Fichiers de définition du modèle de suivi BAM (.btt)|Le changement du numéro de version de l'assembly entraîne l'échec de tous les fichiers de définition du modèle de suivi BAM. Étant donné que les fichiers de suivi BAM sont dans un format binaire, ils ne peuvent pas être modifiés et doivent donc être régénérés. Si les modèles de suivi BAM sont nécessaires, il vous faut respecter l'une ou l'autre de ces instructions :<br /><br /> -Éviter la mise à jour fréquemment des numéros de version pendant le processus de génération<br />-Retarder la création de profils de suivi jusqu'à ce que les numéros de version sont stables BAM|  
|Services Web publiés à l'aide de l'Assistant Publication de services Web|Lorsque l’Assistant Publication de Services Web est utilisé pour produire une interface Web ASP.NET, la version d’assembly de l’assembly BizTalk Server est incluse dans le code source ASP.NET. Le numéro de version d’assembly est utilisé lors de l’exécution par l’interface ASP.NET dans le cadre de la propriété bodyTypeAssemblyQualifiedName de l’opération de service Web. Si le numéro de version de l’assembly BizTalk Server change sans mettre à jour la propriété bodyTypeAssemblyQualifiedName, les opérations de service Web suivantes seront rejetées par BizTalk Server.<br /><br /> Lorsque l'emplacement de réception utilise le pipeline XmlDefaultPipeline, l'abonnement se réfère au type de document. Ce dernier se sert des informations d'assembly incorporées et il échoue si l'assembly n'existe pas. Si le pipeline utilisé est PassThruPipeline (pipeline par défaut lorsqu'un port est exposé et que l'Assistant crée de lui-même l'emplacement de réception), l'abonnement ignore ces informations d'assembly incorporées.|