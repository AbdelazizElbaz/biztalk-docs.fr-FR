---
title: 'Leçon 1 : Définir des schémas et un mappage | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- enterprise application integration tutorial, creating solutions
ms.assetid: 4fe7720d-722e-4fa0-a556-477fc66ffa12
caps.latest.revision: 35
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce6411a7a4ffa80b72bad2d84766bf773bbfb42f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-define-schemas-and-a-map"></a>Leçon 1 : Définir des schémas et un mappage
Au cours de cette leçon, vous allez créer et générer le premier projet de la solution d'intégration des applications de l'entreprise (IAE). Le projet contient deux schémas de message et un mappage.  
  
 Dans la solution IAE, un système d'entrepôt envoie un message de demande de réapprovisionnement de stock à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour traitement. Dans cette leçon, vous allez créer les éléments suivants :  
  
-   la solution IAE contenant le projet ;  
  
-   le projet contenant les schémas et le mappage ;  
  
-   le schéma du message envoyé par l'entrepôt à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour demander un réapprovisionnement de stock ;  
  
-   le schéma du message que l'entrepôt est supposé recevoir en cas de refus de la demande ;  
  
-   un mappage pour le reformatage d'un message de demande afin de créer un message de refus de demande.  
  
 Enfin, vous générez le projet avant de démarrer [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md). Dans la leçon 2, vous allez créer le processus d'entreprise permettant d'acheminer les messages et d'évaluer le contenu du message de demande de réapprovisionnement de stock sur la base de critères d'approbation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Création du projet EAISchemas](../core/step-1-create-eaischemas-project.md)  
  
-   [Étape 2 : Création du schéma de demande de stock](../core/step-2-create-the-inventory-request-schema.md)  
  
-   [Étape 3 : Créer le schéma de refus de demande](../core/step-3-create-the-request-decline-schema.md)  
  
-   [Étape 4 : Créer la carte](../core/step-4-create-the-map.md)  
  
-   [Étape 5 : Créer le projet EAISchemas](../core/step-5-build-the-eaischemas-project.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Avant de commencer le didacticiel](../core/before-you-begin-the-tutorial.md)   
 [Leçon 2 : Définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md)   
 [Leçon 3 : Déployer la Solution](../core/lesson-3-deploy-the-solution.md)