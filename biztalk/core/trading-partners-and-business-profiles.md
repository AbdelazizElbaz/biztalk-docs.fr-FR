---
title: "Partenaires commerciaux et les profils d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbeac421-c319-4a60-a188-28f7268888fc
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fff632199d3acd8be4ade7724eaa49748dab5db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="trading-partners-and-business-profiles"></a>Partenaires commerciaux et les profils d’entreprise

## <a name="overview"></a>Vue d'ensemble
Chaque organisation participante dans une relation commerciale est un partenaire commercial. Également appelé « partie commerciale » ou « tiers », un partenaire commercial se trouve au niveau racine et forme la base d'une solution de partenariat commercial. Il est l'un des participants dans une relation commerciale continue. Il s'agit d'une entité commerciale qui peut envoyer et recevoir des messages vers ou depuis un autre partenaire.  
  
 Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], solution GPC peut être utilisée pour modéliser et stocker les informations des partenaires commerciaux, tels que l’envoi du port associations et les certificats utilisés pour valider l’identité d’un tiers. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]utilise ces informations pour la gestion des messages reçus et envoyés. Chaque organisation participant à une relation commerciale, y compris l’organisation d’origine (l’organisation de l’hôte local exécutant le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hôte), est représenté sous la forme d’un partenaire commercial.
  
 ![Partenaires commerciaux](../core/media/tradingparties.gif "TradingParties")  
  
 Par exemple, prenons les deux organisations : Fabrikam et Contoso. Fabrikam utilise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour gérer tous les échanges de données d'entreprise avec Contoso, Fabrikam doit créer deux partenaires commerciaux, un pour lui et un pour Contoso. Lors de la création d’un tiers, vous fournir certaines informations telles que les partenaires de nom et ainsi de suite.  
 
## <a name="business-profiles"></a>Profils d’entreprise

Le profil d'entreprise d'un partenaire commercial représente le visage commercial d'une organisation. Chaque département d’une organisation de transactions avec un autre département d’une autre organisation est représentée comme un profil d’entreprise dans une solution GPC. Toutes les propriétés qui définissent les paramètres de messagerie interentreprises spécifiques au département, à l'unité commerciale ou au système d'entreprise sont capturées dans son profil d'entreprise. Par exemple, supposons que Fabrikam a deux départements : « Paiement » et « Shipping ». Contoso dispose d’un département « Factures ». Vous envisagez de Fabrikam utilise [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il doit créer :  
  
-   deux profils d'entreprise Paiements et Expédition, sous le partenaire commercial Fabrikam ;  
  
-   un profil d'entreprise Facturation, sous le partenaire commercial Contoso.  
  
 La figure suivante illustre la manière dont les partenaires commerciaux et les profils d'entreprise sont gérés dans une solution GPC :  
  
 ![Des profils d’entreprise du partenaire commercial](../core/media/businessprofile.gif "BusinessProfile")  
  
 Une fois les profils d'entreprise définis, les départements peuvent définir les formats et transports de codage des messages qu'ils utilisent lors de l'envoi et de la réception de messages interentreprises. Ces modèles de communication entre les profils d’entreprise sont décrits dans [paramètres de protocole](../core/protocol-settings.md).  
  
### <a name="why-do-i-need-business-profiles"></a>Pourquoi ai-je besoin de profils d'entreprise ?  
 Les profils d'entreprise permettent aux utilisateurs de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de représenter de manière optimale leur modèle d'entreprise dans une solution GPC. Une société constituée de plusieurs départements peut être représentée de manière indépendante dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Ce modèle permet également aux utilisateurs de configurer des propriétés pour chaque profil d'entreprise qui définissent l'interaction entre plusieurs profils. Par exemple, prenons l'exemple d'une société dont les départements sont situés aux États-Unis et en Europe. La division États-Unis attend les messages EDI uniquement dans X12 standard, tandis que la division en Europe attend les messages EDI EDIFACT standard. En créant des tiers, la société peut configurer le droit de propriétés de messagerie au niveau du profil et en même temps utilisent les propriétés qui sont déjà définies au niveau du partenaire. Sans les profils d’entreprise, l’entreprise doit être créer des partenaires commerciaux pour l’ensemble des départements, puis répliquer un hôte de propriétés entre ces partenaires commerciaux.  
  
 Vous pouvez également associer des identités d'entreprise aux profils d'entreprise pour que ceux-ci possèdent une identification unique. Ces entités d'entreprise peuvent être fournies par un corps de normes ou convenues mutuellement.  
  
> [!IMPORTANT]
>  Si deux départements d'une même organisation doivent entretenir des relations commerciales, vous devez les créer en tant que partenaires commerciaux distincts. Deux profils définis pour un même partenaire ne peuvent pas interagir car seules les relations de partenariat commercial entre des partenaires distincts sont acceptées.  
  
## <a name="learn-next"></a>Découvrez ensuite

[Paramètres de protocole](../core/protocol-settings.md)  
[Accord de partenariat commercial](../core/trading-partner-agreement.md)  
[Assemblage : définition d’une Solution de gestion des partenaires commerciaux](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)
 
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md)