---
title: "Comment supprimer un artefact d’une Application | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- artifacts, deleting
- applications, modifying
- applications, artifacts
- modifying, applications
- deleting, artifacts
ms.assetid: c528be0b-0b1a-4c5f-acd2-7355da91a253
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25d57c41311cef12a33685dcc4c8aacd85290b7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-remove-an-artifact-from-an-application"></a>Comment supprimer un artefact d’une Application
La suppression d'un artefact l'élimine des bases de données BizTalk Server de sorte qu'il n'apparaît plus ni dans la console d'administration, ni dans la liste des artefacts d'une application générée par la commande BTSTask ListApp. Par contre, il n'est effacé ni dans le Registre Windows, ni dans le Global Assembly Cache, ni dans le répertoire virtuel, ni dans le système de fichiers, si tant est qu'il existe à ces emplacements. Dans le cas des ports d'envoi, des groupes de ports d'envoi, des ports de réception et des emplacements de réception, qui n'existent que dans la base de données de gestion BizTalk, cette opération efface entièrement l'artefact. Pour plus d’informations, consultez [que se passe-t-il lorsque artefacts sont ajoutés et supprimés](../core/what-happens-when-artifacts-are-added-and-removed.md)  
  
 En fonction du type de l'artefact, sa suppression peut avoir différents effets sur le fonctionnement d'une application. Pour plus d'informations et d'instructions sur la suppression d'un type particulier d'artefact, voir la rubrique correspondante :  
  
-   [Comment supprimer une Orchestration à partir d’une Application](../core/how-to-remove-an-orchestration-from-an-application.md)  
  
-   [Comment supprimer un Port d’envoi](../core/how-to-delete-a-send-port.md)  
  
-   [Comment supprimer un groupe de ports d’envoi](../core/how-to-delete-a-send-port-group.md)  
  
-   [Comment supprimer un Port de réception](../core/how-to-delete-a-receive-port.md)  
  
-   [Comment supprimer un emplacement de réception](../core/how-to-delete-a-receive-location.md)  
  
-   [Comment supprimer une stratégie à partir d’une Application et le groupe BizTalk](../core/how-to-remove-a-policy-from-an-application-and-the-biztalk-group.md)  
  
-   [Comment supprimer un schéma à partir d’une Application](../core/how-to-remove-a-schema-from-an-application.md)  
  
-   [Comment supprimer un mappage à partir d’une Application](../core/how-to-remove-a-map-from-an-application.md)  
  
-   [Comment supprimer un Assembly BizTalk à partir d’une Application](../core/how-to-remove-a-biztalk-assembly-from-an-application.md)  
  
-   [Comment supprimer un Script de pré-traitement ou de post-traitement à partir d’une Application](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)  
  
-   [Comment supprimer un Assembly .NET, certificat ou autre artefact de ressource à partir d’une Application](../core/remove-a-net-assembly-certificate-or-resource-artifact-from-an-application.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Commande RemoveResource](../core/removeresource-command.md)