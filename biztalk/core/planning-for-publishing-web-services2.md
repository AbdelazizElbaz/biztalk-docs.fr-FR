---
title: Planification de la publication Web Services2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, planning
- virtual directories, updating
- BizTalk Server Web Services Publishing Wizard
ms.assetid: 69107557-48e2-4f15-ba42-9fad476a8294
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d0b9d593a3309f7b4477f2fa735f7e265b614c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-publishing-web-services"></a>Planification de la publication de Services Web
Vous pouvez accéder aux services Web depuis vos orchestrations. Vous pouvez également utiliser l'Assistant Publication de services Web BizTalk pour publier votre service Web.  
  
 Le tableau suivant présente certaines des questions auxquelles vous devez répondre au moment de planifier la création de schémas dans les services Web.  
  
|Question relative à la planification|Recommandation|  
|-----------------------|--------------------|  
|Avez-vous créé votre projet BizTalk Server ?|Vous devez créer votre projet BizTalk Server avant d'exécuter l'Assistant Publication de services Web BizTalk.|  
|Avez-vous activé l'exécution des services Web sur votre système ?|Vous devez activer l'exécution des services Web sur votre ordinateur avant d'exécuter l'Assistant Publication de services Web BizTalk. Pour plus d’informations sur l’activation de votre système pour les services Web, consultez [activation des Services Web](../core/enabling-web-services.md).|  
|Avez-vous vérifié que votre schéma contient uniquement des éléments et caractères XML valides ?|Les services Web ne gèrent pas les caractères chinois, japonais ou coréen (CJC) unifiée IDÉOGRAMME Extension A. Des restrictions s'appliquent également à certains éléments de schéma XML (XSD). Pour plus d’informations sur les caractères XML valides et les éléments pris en charge et les considérations relatives aux éléments, consultez [Considérations lors de la publication de Services Web](../core/considerations-when-publishing-web-services.md).|  
|L'un des types de messages dans votre projet BizTalk Server utilise-t-il des classes .NET définies par l'utilisateur ?|Vous devez installer les assemblys contenant les classes .NET définies par l'utilisateur référencés par les types de messages dans le Global Assembly Cache (GAC).|  
|Effectuez vos clients Web utilisent-ils les informations d’identification fournies pour le **WindowsUser** propriété de contexte ?|Les informations d’identification fournies par les clients Web un service Web publié utilisent la **WindowsUser** propriété de contexte. La résolution du tiers utilise cette propriété. Si vous configurez un tiers à l’aide de la **WindowsUser** propriété de contexte et le client Web utilise le service Web avec les informations d’identification correspondant au tiers, BizTalk Server identifie le message comme provenant du tiers prédéfini correspondant. Pour plus d’informations sur des composants de pipeline Résolution du tiers, consultez [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de Services Web](../core/publishing-web-services.md)