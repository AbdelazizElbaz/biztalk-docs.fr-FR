---
title: Accord de partenariat commercial | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40a3847-ee36-4a75-ab50-def9b0caf07e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a62ada3317bc347a6d39af9fb2f983e02647e5e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="trading-partner-agreement"></a>Accord de partenariat commercial
## <a name="overview"></a>Vue d'ensemble
Un accord de partenariat commercial est défini comme un accord définitif et ferme entre deux partenaires commerciaux pour le traitement des messages via un protocole interentreprises spécifique. Les accords combinent les propriétés de traitement des messages bidirectionnelles à partir des profils commerciaux spécifiques des deux partenaires. Il s'agit d'un ensemble complet d'aspects régissant la transaction commerciale entre deux partenaires commerciaux. L'accord de partenariat commercial est généralement dérivé des profils de chaque partenaire, les paramètres requis pouvant être personnalisés et remplacés.  
  
 Plus simplement, il s'agit d'un accord entre deux profils d'entreprise pour utiliser un protocole de codage des messages spécifique ou un protocole de transport spécifique lors de l'échange de messages interentreprises.  
  
 ![Profils avec les accords de partenaires](../core/media/tradingpartneragreement.gif "TradingPartnerAgreement")  
  
 Dans l’illustration précédente, il existe un accord entre les profils « Shipping » et « Invoice » de Fabrikam et Contoso respectivement à utiliser le X12 encodage des messages de l’entreprise (**accord sur le codage**) et pour le transport AS2 échange de messages (**accord de transport**). Il peut y avoir de nombreux accords entre les divers profils d'entreprise. Par exemple, il peut exister un accord entre les profils « Payments » et « Invoice » pour utiliser la norme de codage des messages EDIFACT. Ces accords pour tous les profils d’un couple de partenaires commerciaux constituent un **partenariat** entre les deux partenaires commerciaux.  
  
## <a name="bi-directional-agreements"></a>Accords bidirectionnels  
 Chaque accord entre deux profils d'entreprise est bidirectionnel. Par exemple, l'accord entre les profils d'entreprise « Shipping » et « Invoice » contiennent des propriétés pour traiter les messages :  
  
-   Reçus par le profil « Shipping » du profil « Invoice », et  
  
-   Envoyés par le profil « Shipping » au profil « Invoice ».  
  
 En d'autres termes, un accord bidirectionnel est constitué de deux accords unidirectionnels. Un accord unidirectionnel peut être considéré comme une collection de propriétés qui définissent comment la transaction de message se produit à partir de tiers A et tiers B. L’autre accord unidirectionnel peut être considéré comme une collection de propriétés qui définissent comment les transaction de message se produit entre le tiers B au tiers A.  
  
## <a name="considerations-when-defining-an-agreement"></a>Considérations relatives à la définition d’un accord  
 Vous devez prendre en compte les points suivants lors de la création d'un accord de partenariat commercial :  
  
-   Pour deux profils d'entreprise qui échangent des messages interentreprises, la définition d'un accord sur le codage des messages est obligatoire. Les départements peuvent uniquement choisir un accord AS2 s'ils souhaitent utiliser le protocole AS2 pour transférer les messages. Par exemple, un accord AS2 n'est pas obligatoire si les départements choisissent de transférer les messages par courrier électronique.  
  
-   Si deux profils d'entreprise prennent en charge les codages X12 et EDIFACT et qu'ils s'accordent à utiliser les deux protocoles de codage lors de l'échange de messages, il doit exister des accords séparés pour chaque protocole. Il doit y avoir un seul accord pour le protocole X12 et un seul accord pour le protocole EDIFACT. Il ne peut pas y avoir un accord unique qui peut être utilisé pour les deux protocoles.  
  
-   L'accord sur le codage des messages X12 et EDIFACT et l'accord de transport (pour AS2) ne peuvent pas faire partie d'un seul et même accord. Vous devez créer des accords distincts pour les deux.  
  
## <a name="global-or-fallback-agreement"></a>Accord global ou de secours  
 Certaines organisations commerciales peuvent choisir d'avoir un ensemble singulier de mécanismes de traitement interentreprises sans différencier les tiers impliqués dans l'échange de messages interentreprises spécifique. En effet, de telles organisations commerciales ont en commun un seul paramètre de protocole interentreprises qui est partagé avec tous les autres partenaires commerciaux. De même, comme de telles organisations ne doivent pas avoir de paramètres spécifiques pour des partenaires spécifiques, les paramètres du protocole interentreprises sont définis pour le partenaire commercial lui-même et non pour un profil d'entreprise de partenaire commercial. Dans [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], ces organisations commerciales sont répercutées comme **partenaires commerciaux globaux**. Autres entreprises qui doivent faire des échanges avec une entreprise représentée comme un partenaire commercial global utilisent des accords avec le partenaire commercial global qui sont appelées **accord de partenariat commercial Global**. Ces accords sont conformes aux paramètres de codage des messages et de protocole définis pour le partenaire commercial global.  
  
 Les paramètres définis au niveau global peuvent également être utiles dans les cas où les paramètres de protocole spécifiques au profil entre deux partenaires commerciaux ne formulent pas d'accord de partenariat commercial. Dans ce cas, l'organisation hébergeant [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] peut utiliser les paramètres de protocole définis pour le partenaire pour formuler un accord avec un autre profil d'entreprise de partenaire commercial. Dans ce cas, l’accord conclu pour l’utilisation de paramètres de protocole globaux définis pour le partenaire est appelé le **accord de partenariat commercial de secours**.  

## <a name="learn-next"></a>Découvrez ensuite

[Vue d’ensemble : définition d’un commercial de solution de gestion des partenaires](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md)