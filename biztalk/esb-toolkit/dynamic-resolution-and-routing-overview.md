---
title: "Vue d’ensemble de routage et de la résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9a32491-132b-4b25-ac8c-4a927052f0be
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 341b8389530ac85fdc459816f5691f3b814fbd56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="dynamic-resolution-and-routing-overview"></a>Vue d’ensemble de routage et de la résolution dynamique
Les classes de programme de résolution ESB prennent en charge la résolution de l’exécution des opérations suivantes :  
  
-   Points de terminaison remise de message  
  
-   Mappages de transformation  
  
-   Configuration de point de terminaison  
  
-   Métadonnées de service personnalisé  
  
-   Itinéraires côté serveur  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise des chaînes de connexion de programme de résolution pour essayer de résoudre les points de terminaison et les mappages lorsque des messages arrivent. Ces chaînes de connexion peuvent exister dans l’en-tête SOAP d’itinéraire des messages lorsqu’ils arrivent, ou elles peuvent être définies dans un pipeline personnalisé à l’aide d’un des composants de pipeline suivants : sélecteur de feuille de route ESB, ESB répartiteur ou ESB répartiteur désassembler. La résolution se produit ultérieurement dans le cycle de vie de traitement à utiliser les fonctionnalités de résolution « juste-à-temps » (JIT) du programme de résolution ESB et des composants de l’infrastructure d’adaptateurs fournisseur.  
  
 Par exemple, si l’agent de transformation dynamique reçoit un message, il doit être mappé, mais le nom de mappage n’a pas encore été déterminé, il tentera d’utiliser le programme de résolution associé pour effectuer la résolution. Si la résolution JIT échoue, ce qui est classé comme une erreur, le système génère un message d’exception.  
  
 Le programme de résolution et le fournisseur d’infrastructure d’adaptateurs peuvent interroger les banques de données suivantes ou les mécanismes de résolution :  
  
-   Codé en dur des mappages ou des points de terminaison, dans lequel cas résolution dynamique n’a pas lieu  
  
-   Une stratégie du moteur de règles d’entreprise (BRE)  
  
-   Un assembly personnalisé qui implémente le **IResolveProvider** interface  
  
-   Une requête XPath sur le message  
  
-   Une recherche Universal Description, Discovery and Integration (UDDI)