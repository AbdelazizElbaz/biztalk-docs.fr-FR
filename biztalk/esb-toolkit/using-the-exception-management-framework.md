---
title: "À l’aide de l’infrastructure de gestion d’Exception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69c9c01-e7e4-4788-8fe2-43d32075155d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47442604831a3a11bb9d00b65f9dc34961de2367
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-exception-management-framework"></a>À l’aide de l’infrastructure de gestion des exceptions
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise des exceptions pour communiquer des erreurs (par exemple, une carte non déployée ou les règles qui ne retournent pas un nom de mappage) pour les transformations dynamiques et le routage. En cas d’échec d’une transformation ou un processus de routage, l’architecture ESB crée un message d’exception et la soumet via un port de liaison directe à la base de données de la boîte de Message. L’architecture ESB implémente également un port d’envoi nommé tous. Exceptions qui s’abonne à et récupère les messages d’exception et les publie dans le portail de gestion ESB.  
  
 En outre, tous les exemples d’orchestration utilisent l’Orchestration d’échec ESB API de routage Exception pour la gestion des exceptions. Vous pouvez utiliser cette API dans n’importe quel projet d’orchestration que vous déployez. La fonctionnalité d’ESB Échec de l’Orchestration Exception routage fournit un moyen standard pour intercepter et signaler toutes les exceptions dans un environnement BizTalk Server.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient plusieurs projets d’exemples qui montrent comment utiliser l’infrastructure de gestion d’Exception ESB. Les deux projets suivants encapsulent l’ESB Échec de l’Orchestration routage API de l’Exception :  
  
-   **ESB. ExceptionHandling**. Ce projet contient toutes les méthodes publiques pour gérer le traitement de message d’erreur dans les orchestrations. Vous devez inscrire l’assembly de ce projet dans le global assembly cache sur le serveur local.  
  
-   **ESB. ExceptionHandling.Schemas.Faults**. Ce projet contient le schéma de message d’erreur défini par l’espace de noms **http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling** et le schéma de propriété système. Vous devez déployer ce projet sur le conteneur d’application Microsoft.Practices.ESB.  
  
 Tous les projets qui utilisent l’Orchestration d’échec ESB API de routage Exception doivent référencer les assemblys principaux :  
  
-   **Microsoft.Practices.ESB.ExceptionHandling.dll**  
  
-   **Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**  
  
 Les sections suivantes fournissent plus d’informations sur l’utilisation de l’infrastructure de gestion d’Exception ESB :  
  
-   [Les membres de l’Exception API ESB](../esb-toolkit/the-esb-exception-api-members.md)  
  
-   [Création et la publication des Messages d’erreur](../esb-toolkit/creating-and-publishing-fault-messages.md)  
  
-   [S’abonner à et l’extraction des Messages](../esb-toolkit/subscribing-to-and-extracting-messages.md)  
  
-   [Étapes Solution du scénario](../esb-toolkit/scenario-solution-steps.md)