---
title: Importer des liaisons pour TIBCO Rendezvous | Documents Microsoft
description: "Déployer votre adaptateur BizTalk pour les applications de TIBCO Rendezvous à l’aide de la fonctionnalité d’importation des liaisons dans BizTalk Server"
ms.custom: 
ms.date: 10/24/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec5751a9-0a08-4cf8-a3ef-e51e488a4180
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e880bcbce388bb15924e96739c8bb617c04d0e24
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="deploy-tibco-rendezvous-ports-and-assemblies"></a>Déployer des assemblys et des ports de TIBCO Rendezvous
  
## <a name="overview"></a>Vue d'ensemble
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de dupliquer des ports et des assemblys sur un ordinateur cible. L'Assistant exporte la configuration des ports d'envoi/emplacements de réception dans un fichier XML.  
  
 Vous pouvez utiliser BizTalk pour effectuer les opérations suivantes :  
  
-   Déployer ou supprimer des assemblys BizTalk Server dans une base de données de Configuration BizTalk.  
  
-   installation ou désinstallation des assemblys dans le GAC (Global Assembly Cache) ;  
  
-   Importer ou exporter des informations de liaison d’assembly BizTalk Server vers et à partir de fichiers de liaison.  
  
 Pour plus d’informations sur l’utilisation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour déployer des ports et des assemblys, consultez [comment exporter les liaisons d’une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md).  
  
> [!NOTE]
>  L'adaptateur Microsoft BizTalk pour TIBCO Rendezvous requiert l'installation de Visual Studio sur un ordinateur (de développement) source. Visual Studio n'est pas requis sur l'ordinateur de production.  

## <a name="confirm-your-setup"></a>Vérifiez votre configuration

Avant d’utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour importer un fichier de liaison, vérifiez que les dossiers pour les réponses existent et qu’ils sont identiques sur le nouvel ordinateur, ou vous devez modifier le fichier de liaison.  
  
## <a name="clean-the-target-computer"></a>Nettoyer l’ordinateur cible
Déploiement remplace la configuration d’emplacement de réception. Lorsque vous déployez un fichier de liaison (et un assembly) sur un ordinateur cible, les ports d’envoi et emplacements de réception sont remplacés par ceux dans le fichier de liaison XML lorsqu’ils sont importés.  
  
Avant d’importer, supprimer les ports d’envoi et emplacements de réception liés à l’orchestration.  
  
Si vous n’avez pas de Microsoft Visual Studio est installé sur l’ordinateur cible, vous pouvez supprimer les ports en exécutant les scripts :  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs  
  
-   [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs  
  
Par exemple, à une invite de commandes, exécutez :  
  
```
cscript RemoveSendPort.vbs \<Send port name>
```
  
## <a name="next-steps"></a>Étapes suivantes
[Utiliser BizTalk Server des exceptions dans votre orchestration](../core/using-biztalk-server-exception-handling4.md)  
[Dépanner](../core/troubleshooting-tibco-rendezvous.md)