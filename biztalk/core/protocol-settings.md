---
title: "Paramètres de protocole | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 224a9837-5c85-4511-b6d9-c8fda63a27d1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a8fe9e7024bfe3a9d5f1d5d7727a2115bcd31a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# Paramètres de protocole
## Vue d'ensemble
Après la création des profils d'entreprise (qui reflètent les départements au sein d'une organisation), une entreprise doit déclarer les paramètres qui définissent le mode de communication entre ces profils d'entreprise. Ces paramètres de communication sont définis en tant que paramètres de protocole. Les paramètres de protocole définissent la manière dont les transactions commerciales doivent être prises en charge pour un protocole interentreprises spécifique. Chaque profil d’entreprise définit les différents paramètres de traitement des messages (codage) ou de leur transmission (transport) pour chacun des protocoles B2B sur laquelle le partenaire peut communiquer. Les paramètres de communication pour les profils d'entreprise sont définis sous les deux catégories suivantes :  
  
-   **Paramètres de protocole de codage**: les protocoles de codage régissent la structure et le contenu d’un message B2B. Les paramètres de protocole de codage pour un profil d’entreprise définissent le protocole de codage par un département pour envoyer et recevoir les messages B2B. X12, EDIFACT, HL7 sont des exemples de protocoles de codage. Pour plus d’informations sur environ pris en charge que les protocoles de codage pour [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], consultez [prise en charge des normes EDI](../core/edi-standards-support.md). Dans le cadre du protocole de codage, vous pouvez fournir divers paramètres et indiquer si le tiers expéditeur attend un accusé de réception, si les messages sont traités par lot ou envoyés individuellement, etc. Vous pouvez toujours remplacer ces paramètres dans le cadre de l'accord de partenariat commercial. Consultez [accord de partenariat commercial](../core/trading-partner-agreement.md).  
  
-   **Paramètres de protocole de transport**: le protocole de transport régit le canal de transport utilisé pour envoyer les messages dans les deux sens entre deux partenaires. Comme le transport est essentiellement réalisé entre deux points de terminaison de transport, chaque profil d'entreprise définit sa propre configuration du point de terminaison de transport et communique avec un seul point de terminaison de transport du profil d'entreprise de son partenaire commercial. Pour plus d’informations sur le protocole de transport pris en charge, consultez [prise en charge AS2 dans BizTalk Server](../core/as2-support-in-biztalk-server.md). Dans le cadre du protocole de transport, vous pouvez fournir divers paramètres et indiquer si le message doit être signé, chiffré, etc. Vous pouvez toujours remplacer ces paramètres dans le cadre de l'accord de partenariat commercial. Pour plus d’informations sur les contrats, consultez [accord de partenariat commercial](../core/trading-partner-agreement.md).  
  
 En définissant les paramètres de protocole, les profils d'entreprise déclarent le format du message et le protocole de transport à utiliser pour l'envoi de messages interentreprises entre partenaires commerciaux.  
  
> [!NOTE]
>  La définition des paramètres de protocole dans le cadre d'un profil d'entreprise est facultative. Si vous ne spécifiez pas les paramètres de protocole dans le cadre du profil d'entreprise, vous pouvez toujours le faire dans un accord.  
  
 La figure suivante illustre la manière dont des partenaires commerciaux, des profils d'entreprise et des paramètres de protocole sont réunis dans une solution GPC :  
  
 ![Commerciaux de profils de partenaires et des paramètres de protocole](../core/media/protocolsettings.gif "ProtocolSettings")  
  
 Dans l'illustration précédente, le profil d'entreprise « Shipping » peut envoyer et recevoir des messages avec le format de codage X12 via le protocole de transport AS2. De même, le profil « Invoice » peut envoyer et recevoir des messages avec les formats de codage X12 et EDIFACT via le protocole de transport AS2.  
  
 Il est à présent évident à quel point la définition d'un profil d'entreprise est utile à la création d'une solution GPC dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Actuellement, comme le montre l'illustration, le profil d'entreprise « Shipping » peut envoyer et recevoir des messages X12 uniquement. Ainsi, tout profil d'entreprise communiquant avec le profil d'entreprise « Shipping » devra adhérer aux paramètres de propriété de ce dernier. Cependant, à l'avenir, si le profil d'entreprise « Shipping » commence à accepter les messages au codage EDIFACT, il suffira de définir les propriétés pertinentes pour inclure la prise en charge d'EDIFACT. L'organisation partenaire ne doit pas créer un profil d'entreprise pour le même département d'expédition.  
  
## Dois-je toujours spécifier les paramètres de protocole lors de la création d'un profil d'entreprise ?  
 En théorie, oui, un profil d'entreprise doit contenir la définition des paramètres de protocole. Cependant, cela n'implique pas que vous deviez définir les paramètres de protocole lors de la création d'un profil d'entreprise dans l'interface utilisateur GPC. GPC vous offre la flexibilité de spécifier les paramètres de protocole lors de la création du profil d'entreprise ou d'un accord de partenariat commercial. Si vous définissez les paramètres de protocole dans le cadre du profil d'entreprise, ils sont disponibles lors de la création d'un accord de partenariat commercial pour ce profil. Toutefois, si vous définissez les paramètres de protocole dans le cadre de l'accord, vous devrez fournir toutes les valeurs dans le cadre de l'accord.  
  
> [!IMPORTANT]
>  Si vous ne définissez pas les paramètres de protocole dans le cadre du profil d'entreprise, vous devez entrer les valeurs dans le cadre de chaque accord pour ce profil d'entreprise, faisant échouer le modèle d'évolutivité de la nouvelle solution GPC. Par conséquent, Microsoft recommande de définir les paramètres de protocole pour chaque profil d'entreprise. Vous pouvez toujours remplacer ces paramètres, si nécessaire, lors de la création d'un accord de partenariat commercial.  

## Découvrez ensuite
[Accord de partenariat commercial](../core/trading-partner-agreement.md)  
[Assemblage : définition d’une Solution de gestion des partenaires commerciaux](../core/putting-it-all-together-defining-a-trading-partner-management-solution.md)  
  
## Voir aussi  
 [Blocs de construction d’une Solution de gestion des partenaires commerciaux](../core/building-blocks-of-a-trading-partner-management-solution.md)