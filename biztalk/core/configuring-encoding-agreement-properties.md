---
title: "Configuration des propriétés de l’accord de codage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.admin.ediagreement.properties
ms.assetid: 0cb1146e-177c-42fa-b1d8-a834229c2af9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cde69b1514b2e376a7df415befc0a686300009f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-encoding-agreement-properties"></a>Configuration des propriétés d'un accord sur le codage
Un accord de partenariat commercial (TPA) est un accord définitif et ferme entre deux partenaires commerciaux pour le traitement des messages via un protocole interentreprise spécifique. Plus simplement, il s'agit d'un accord entre deux profils d'entreprise pour utiliser un protocole de codage de message spécifique (X12 ou EDIFACT) ou un protocole de transport spécifique (AS2) lors de l'échange de messages interentreprise. En plus de s'accorder sur le protocole de codage et de transport, un accord peut servir à personnaliser le format et la remise des messages.  
  
-   Dans les paramètres du protocole de codage, vous pouvez également définir si le tiers expéditeur attend un accusé de réception, si les messages sont traités par lot ou envoyés individuellement, etc.  
  
-   Dans les paramètres du protocole de transport, vous pouvez également définir si le message doit être signé, chiffré, etc.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les paramètres de protocole (AS2) de transport, consultez [propriétés de configuration de l’accord AS2](../core/configuring-as2-agreement-properties.md).  
  
 Lors de la création d'un accord, vous devez prendre en compte les points suivants :  
  
-   Un accord de partenariat commercial entre deux tiers est bidirectionnel. Un seul accord entre deux tiers (A et B) peut être utilisé pour envoyer des messages du tiers A au tiers B, mais également pour recevoir des messages du tiers B au tiers A. Pour représenter un accord bidirectionnel dans l'interface utilisateur, chaque accord unidirectionnel est représenté dans un seul onglet. Par conséquent, dans l’interface utilisateur du contrat, vous verrez deux onglets, **pourquoi -> Tiersb** (représentant l’accord unidirectionnel pour les messages envoyés à partir de tiers A au tiers B) et **Tiersb -> Pourquoi** (représentant le accord unidirectionnel pour les messages envoyés à partir d’est à pourquoi.)  
  
-   Chaque accord unidirectionnel s'adresse à une seule transaction de message de bout en bout. L'envoi et la réception d'accusés de réception faisant partie intégrante de la transaction de message, ils doivent être configurés dans le même onglet d'accord unidirectionnel. Par exemple, considérez le tiers A les envoie l’échange EDI au tiers B et en réponse, tiers B renvoie un accusé de réception au tiers A. Par conséquent, toutes les propriétés relatives à l’envoi d’un échange et attend un accusé de réception doivent être définies sur le **pourquoi -> Tiersb** onglet.  
  
    > [!NOTE]
    >  Même si l’accusé de réception fait partie de la même transaction de message, les propriétés relatives à la façon de générer l’accusé de réception sont configurées dans le **Tiersb -> Pourquoi** onglet. Cela est nécessaire car les propriétés de contexte d’accusé de réception pour l’expéditeur et récepteur les qualificateurs sont définis sur le contraire des valeurs que vous avez spécifié dans le **pourquoi -> Tiersb** onglet. Par exemple, si les identificateurs de l'expéditeur et du récepteur sont définis sur THEM et US dans l'accord auquel correspond le message d'échange, les propriétés de contexte de l'expéditeur et du récepteur sont définies sur US et THEM dans l'accusé de réception. De manière générale, l'autre onglet de l'accord unidirectionnel dispose également des identificateurs de l'expéditeur et du récepteur définis sur US et THEM, respectivement. Ainsi, le message d'accusé de réception correspond à cet accord et la configuration des propriétés est choisie. Par conséquent, si vous souhaitez disposer de l’accusé de réception à utiliser d’autres séparateurs d’éléments ou si vous souhaitez disposer de l’accusé de réception à utiliser CR LF, spécifiez les propriétés de la **Tiersb -> Pourquoi** onglet.  
    >   
    >  Sur le plan conceptuel, les propriétés de l'accusé de réception sont récupérées à partir de l'un des onglets de l'accord unidirectionnel possédant les mêmes qualificateurs d'expéditeur et de récepteur que ceux définis dans les propriétés de contexte de l'accusé de réception. Toutefois, pour des raisons de commodité, vous définissez ces propriétés sous l'autre onglet de l'accord unidirectionnel créé, auquel correspond l'échange.  
  
-   Vous pouvez disposer d'un accord sur le codage (pour définir le type de code à utiliser pour les messages) et d'un accord de transport (pour définir le protocole de transport à utiliser pour l'échange de messages). L'accord sur le codage est obligatoire. Les tiers doivent uniquement choisir un accord AS2 s'ils souhaitent utiliser le protocole AS2 pour transférer les messages. Par exemple, un accord AS2 n'est pas obligatoire si les deux tiers choisissent de transférer les messages par courrier électronique.  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’accord AS2, consultez [propriétés de configuration de l’accord AS2](../core/configuring-as2-agreement-properties.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration des propriétés d’accord spécifique X12](../core/configuring-x12-specific-agreement-properties.md)  
  
-   [Configuration des propriétés de l’accord EDIFACT spécifique](../core/configuring-edifact-specific-agreement-properties.md)