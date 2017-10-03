---
title: "Étapes de développement d’orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designing, orchestrations
- orchestrations, designing
- orchestrations, creating
- creating, orchestrations
- Copy Local property
ms.assetid: 556b1e6c-63a6-4805-a0a5-e555f198fe4e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3fd0a19754871a6e736365e622513b193dcbf06a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="steps-in-orchestration-development"></a>Étapes du développement d'orchestrations
Pour développer une orchestration, vous devrez généralement effectuer les opérations de base suivantes :  
  
-   Ajouter des formes pour représenter vos processus d'entreprise.  
  
     Le Concepteur d'orchestration vous fournit une boîte à outils de formes qui peuvent être utilisées pour représenter diverses actions et autres abstractions. Pour plus d’informations, consultez [formes d’Orchestration](../core/orchestration-shapes.md).  
  
-   Définir des schémas pour décrire le format de vos messages.  
  
     Vous pouvez définir des schémas avec l'Éditeur BizTalk. Pour plus d’informations, consultez [comment créer les schémas des Messages XML](../core/how-to-create-schemas-for-xml-messages.md).  
  
-   Définir des ports via lesquels les messages sont envoyés et reçus.  
  
     Vous pouvez définir des ports pour indiquer comment et où les messages sont envoyés et reçus. Pour plus d’informations, consultez [à l’aide des Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md).  
  
-   Lier **envoyer** et **réception** formes aux ports.  
  
     Vous pouvez vous connecter votre **envoyer** et **réception** formes aux ports et spécifier les opérations de port qu’ils utilisent. Pour plus d’informations, consultez [comment configurer la forme envoi](../core/how-to-configure-the-send-shape.md). Consultez également [comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md).  
  
-   Attribuer ou transformer des données entre des messages.  
  
     Vous pouvez utiliser la **construire un Message** forme pour affecter des valeurs de message ou de des transformations de message. Pour plus d’informations, consultez [construction de Messages](../core/constructing-messages.md).  
  
-   Identifier tous les composants personnalisés que vous pourrez souhaiter écrire ou ajouter en tant que référence afin de travailler dans votre orchestration.  
  
> [!NOTE]
>  Si le **copie locale** de l’assembly référencé est définie sur **True**, Orchestration ne sera pas en mesure de récupérer toutes les modifications apportées à l’assembly externe une fois que la référence de l’ajout initial a lieu Projet BizTalk.  
  
-   Définir et attribuer des variables d'orchestration pour gérer les données dans votre orchestration en cours d'exécution.  
  
     Vous pouvez vous servir du dossier Variables de la fenêtre Vue Orchestration afin de déclarer vos variables d'orchestration, et de l'Éditeur d'expression BizTalk pour modifier les expressions qui attribuent et utilisent les variables dans différentes formes. Pour plus d’informations, consultez [les Types de données XLANG-s](../core/xlang-s-data-types.md).  
  
-   Créer votre orchestration pour vérifier qu'elle est bien complète.  
  
     Vous créez votre orchestration en compilant le projet ou la solution qui la contient. Pour plus d’informations, consultez [comment générer des Orchestrations](../core/how-to-build-orchestrations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Création et l’exécution des Orchestrations](../core/building-and-running-orchestrations.md)   
 [La gestion des Orchestrations](../core/managing-orchestrations.md)   
 [Création d’Orchestrations à l’aide du Concepteur d’Orchestration](../core/creating-orchestrations-using-orchestration-designer.md)