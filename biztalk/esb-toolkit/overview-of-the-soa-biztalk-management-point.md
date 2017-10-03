---
title: "Vue d’ensemble du Point de gestion BizTalk SOA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d4c3a30-c50e-4c1c-9f59-d9a364078388
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60f73834a9bc02e371d4050115b1eccf5e88e02f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-soa-biztalk-management-point"></a>Vue d’ensemble du Point de gestion BizTalk SOA
En mode natif, le Point de gestion BizTalk s’intègre avec les produits de Gestionnaire des services SOA et le banc d’essai. Contrairement au Point de gestion de Services Web par défaut, cette implémentation est associée avec les services fournis par l’environnement de Microsoft BizTalk Server, exprimée en termes de BizTalk Server des emplacements de réception et ports d’envoi. En raison de l’élément arbitraire nature des emplacements de réception et ports (configurés sur un grand nombre d’adaptateurs BizTalk Server) d’envoi, ces services ne sont pas nécessairement associés à des services Web, mais elles peuvent être traitées comme les services Web en termes de SOA Service Manager et SOA banc d’essai.  
  
 Figure 1 montre l’application Web du Gestionnaire des services SOA affichant la page de banc d’essai pour un exemple d’application. L’arborescence de gauche permet aux utilisateurs de naviguer dans les applications et services installés au sein de BizTalk Server, et le volet de droite permet aux utilisateurs d’afficher les détails de l’application, les opérations, ports d’accès, catégories, les règles et les informations d’analyse.  
  
 ![Ch9 &#45; SOAServiceManager](../esb-toolkit/media/ch9-soaservicemanager.jpg "Ch9-SOAServiceManager")  
  
 **Figure 1**  
  
 **Le Gestionnaire des services SOA affichant les fonctionnalités d’analyse disponibles sur la page de banc d’essai**  
  
 Vous pouvez surveiller toutes les opérations dans une application (tous les ports d’envoi et emplacements de réception), ou des opérations spécifiques ; l’affiche de banc d’essai une liste des messages transitant par le texte sélectionné les ports d’envoi et emplacements de réception. Lorsque vous double-cliquez sur un message dans la liste, le banc d’essai affiche les détails du message et ses propriétés de contexte (si l’enregistrement est activé). Ou bien, vous pouvez sélectionner un service spécifique et un moniteur dans les messages en temps réel en passant par ce service.