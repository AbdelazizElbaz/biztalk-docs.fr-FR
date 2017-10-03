---
title: Exportation Bindings6 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings, exporting
- exporting, bindings
ms.assetid: 052a429e-3237-44d4-8933-00aa5edfb212
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3362984eca1dcec4fb68bfbac92c30da81de8a3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exporting-bindings"></a>L’exportation des liaisons
Les sections de cette rubrique décrivent comment exporter des liaisons d'un groupe, d'un assembly ou d'une application BizTalk dans un fichier .xml. Les liaisons déterminent la façon dont les hôtes, ports d'envoi, groupes de ports d'envoi, ports de réception, emplacements de réception et parties sont associés aux orchestrations, pipelines, mappages et schémas. Vous pouvez ensuite importer les liaisons à partir du fichier .xml dans un autre groupe ou une autre application. Les liaisons que vous importez remplacent les liaisons existantes portant le même nom dans le groupe ou l'application. Vous pouvez aussi ajouter des liaisons à une application, ce qui n'écrase pas les liaisons existantes. Les liaisons ajoutées ne prennent effet qu'une fois l'application importée.  
  
 Les fichiers de liaison peuvent accélérer le déploiement de l'application dans les cas suivants en évitant le recours à la configuration manuelle :  
  
-   Déplacement d'une application d'un environnement de déploiement à un autre  
  
-   Mise à jour d'un assembly  
  
-   Déploiement d'un assembly avec ses liaisons dans plusieurs groupes BizTalk  
  
 Pour plus d’informations sur l’utilisation des fichiers de liaison à ces fins, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
 Pour plus d’informations sur l’importation et l’ajout de liaisons, consultez [comment importer les liaisons dans un groupe BizTalk](../core/how-to-import-bindings-into-a-biztalk-group.md), [comment importer les liaisons dans une Application BizTalk](../core/how-to-import-bindings-into-a-biztalk-application.md), et [l’ajout d’une liaison Fichier à une Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
> [!IMPORTANT]
>  Le fichier de liaison peut contenir des données sensibles. Veillez à sécuriser le fichier.  
  
> [!NOTE]
>  Pour des raisons de sécurité, lorsque vous exportez un fichier de liaison, BizTalk Server ne conserve pas les mots de passe des liaisons du fichier. Une fois les liaisons importées, vous devez reconfigurer les mots de passe des ports d'envoi et des emplacements de réception pour qu'ils fonctionnent. Vous configurez ces mots de passe dans la boîte de dialogue Propriétés du transport de la console Administration de BizTalk Server pour le port d'envoi ou l'emplacement de réception. Pour obtenir des instructions, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Voir aussi [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment exporter des liaisons d’un groupe BizTalk](../core/how-to-export-bindings-for-a-biztalk-group.md)  
  
-   [Comment exporter des liaisons pour une Application BizTalk](../core/how-to-export-bindings-for-a-biztalk-application.md)  
  
-   [Comment exporter des liaisons d’un Assembly BizTalk](../core/how-to-export-bindings-for-a-biztalk-assembly.md)  
  
-   [Comment exporter des liaisons pour une Solution EDI AS2](../core/how-to-export-bindings-for-an-edi-as2-solution.md)