---
title: "Comment créer ou ajouter un artefact | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, artifacts
- artifacts, creating
- applications, artifacts
ms.assetid: fea7487c-b5fa-457f-8c74-a20ea3a6df85
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b231cdf6a25c4ca316c9620ee789e6e3a715fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-or-add-an-artifact"></a>Ajout ou création d'un artefact
Une fois que vous avez créé une application BizTalk, vous pouvez ajouter des artefacts basés sur un fichier (par exemple des assemblys BizTalk, des assemblys .NET, scripts et certificats) à partir du système de fichiers ou ajouter des stratégies à partir de la base de données du moteur de règles. Vous pouvez également créer des ports d’envoi, des groupes de ports d’envoi, des emplacements de réception, des ports de réception au sein de l'application. La création ou l’ajout d’artefacts permet de les ajouter à la base de données de gestion BizTalk. Vous pouvez ensuite déployer l’application et ses artefacts en tant qu’entité unique, comme décrit dans [déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md).  
  
> [!NOTE]
>  Certains types d’artefacts doivent être uniques dans un groupe ou une application BizTalk. Pour plus d’informations, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  
  
 Pour les procédures d’ajout et de création de chacun des artefacts, voir les rubriques suivantes :  
  
-   [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)  
  
-   [Comment créer un groupe de ports d’envoi](../core/how-to-create-a-send-port-group.md)  
  
-   [Comment créer un Port de réception](../core/how-to-create-a-receive-port.md)  
  
-   [Comment créer un emplacement de réception](../core/how-to-create-a-receive-location.md)  
  
-   [Comment ajouter une stratégie à une Application](../core/how-to-add-a-policy-to-an-application.md)  
  
-   [Comment ajouter un Assembly BizTalk à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md)  
  
-   [Comment ajouter un Script de pré-traitement ou de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [Comment ajouter un fichier à une Application](../core/how-to-add-a-file-to-an-application.md)  
  
-   [Comment ajouter un certificat à une Application](../core/how-to-add-a-certificate-to-an-application.md)  
  
-   [Comment ajouter un composant COM à une Application](../core/how-to-add-a-com-component-to-an-application.md)  
  
-   [Comment ajouter un Assembly .NET à une Application](../core/how-to-add-a-net-assembly-to-an-application.md)  
  
-   [Comment ajouter un artefact BAM à une Application](../core/how-to-add-a-bam-artifact-to-an-application.md)  
  
-   [Comment ajouter un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md)  
  
> [!NOTE]
>  Si le chemin d'accès (nom du fichier compris) à l'artefact que vous ajoutez est très long, l'opération consistant à ajouter un artefact à une application peut échouer. Un chemin d'accès est limité à 260 caractères.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et modification des Applications BizTalk](../core/creating-and-modifying-biztalk-applications.md)   
 [Comment ajouter un artefact 64 bits à une Application](../core/how-to-add-a-64-bit-artifact-to-an-application.md)