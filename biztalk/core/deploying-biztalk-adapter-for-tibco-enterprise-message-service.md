---
title: Importer des liaisons pour TIBCO EMS | Documents Microsoft
description: "Déployer votre adaptateur BizTalk pour les applications de TIBCO Enterprise Message Service à l’aide de la fonctionnalité d’importation des liaisons dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69dae448-4ec6-4a56-a628-bb447bc21b62
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79f7f3ec0478746b8c2c6762fe212229f9c7b11d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="deploy-tibco-ems-ports-and-assemblies"></a>Déployer des assemblys et des ports de TIBCO EMS

## <a name="overview"></a>Vue d'ensemble
Avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez dupliquer des ports et des assemblys sur un ordinateur cible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]configuration de l’emplacement de réception/ports d’envoi exporte dans un fichier XML.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'exécuter les tâches suivantes :  
  
-   déploiement ou suppression des assemblys [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans une base de données de configuration BizTalk ;  
  
-   installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;  
  
-   importation/exportation des informations de liaison des assemblys BizTalk vers/à partir de fichiers de liaison.  
  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service requiert l'installation de Visual Studio sur un ordinateur (de développement) source. Visual Studio n'est pas requis sur l'ordinateur de production.  

## <a name="confirm-your-setup"></a>Vérifiez votre configuration
Avant d'importer un fichier de liaison à l'aide de BizTalk Server, vérifiez les éléments suivants :  
  
-   Les dossiers pour les réponses doivent exister et être identiques sur le nouvel ordinateur. Si ce n'est pas le cas, vous devez modifier le fichier de liaison.  
  
-   S'ils sont inclus dans la configuration, les mots de passe du système TIBCO Enterprise Message Service doivent être enregistrés dans le fichier de liaison sous la forme *****. Consultez **Limitations** dans cette rubrique.


## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible
Déploiement remplace la configuration d’emplacement de réception. Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  

Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs`  
  
`\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs`
  

Par exemple, à une invite de commandes, exécutez :  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```

## <a name="limitations"></a>Limitations
Le mot de passe d’adaptateur de Transport est stocké en tant qu’étoiles (\*\*\*\*\*\*) dans le fichier de liaison qui est exporté par BizTalk Server et la transmet au composant de gestion dans le même format. Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.  
  
 Il s'agit d'une limitation connue. Lorsque vous exportez les informations de liaison, le fichier de liaison qui en résulte ne contient pas les mots de passe utilisés par les adaptateurs de transport dans les emplacements de réception/ports d'envoi. Ceci empêche l'affichage des informations de mot de passe en texte clair. Lors de la prochaine utilisation du fichier pour importer les informations de liaison, vous devez entrer les mots de passe à l'aide de l'interface utilisateur des pages de propriétés du transport. Vous pouvez également modifier temporairement le fichier de liaison avant l'importation en y tapant les mots de passe. Dans ce cas, vous devez supprimer les mots de passe à partir du fichier de liaison une fois l’opération d’importation terminée avec succès.  
  
 
### <a name="password-limitation-workaround"></a>Contournement de la limitation de mot de passe  
 Pour contourner cette limitation de mot de passe, vous pouvez suivre l'une des méthodes suivantes :  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par du texte brut.  
  
    > [!CAUTION]
    >  Cette opération n'est pas recommandée pour des raisons de sécurité.  
  
-   Modifiez le fichier de liaison avant l'importation en remplaçant les étoiles par des valeurs aléatoires (c'est-à-dire, un mot de passe erroné). Entrez le mot de passe correct à l’aide de la **propriétés du Transport** page dans la Console Administration de BizTalk Server après avoir importé le fichier de liaison.  
  
    > [!NOTE]
    >  Cette solution de contournement ne peut être utilisée que si Visual Studio est installé sur l'ordinateur cible ou en développant un outil personnalisé.  
  
-   Vérifiez le système logique et les services de transmission et de réception.  

## <a name="next-steps"></a>Étapes suivantes
[Utiliser BizTalk Server des exceptions dans votre orchestration](../core/using-biztalk-server-exception-handling5.md)