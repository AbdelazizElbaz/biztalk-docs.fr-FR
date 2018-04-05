---
title: Créer une connexion au système Siebel | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting, to the Siebel system
ms.assetid: 5810eeb1-6e26-4620-a731-fb352eebea2e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a108335263e85db832f4db144d27b64b92429683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-siebel-system"></a>Créer une connexion au système Siebel
Le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Par conséquent, il permet la communication à un système Siebel via une adresse de point de terminaison WCF. Dans WCF, l’adresse de point de terminaison identifie l’emplacement réseau d’un service et est généralement exprimée comme une ressource identificateur URI (Uniform). Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] exprime cet emplacement en tant qu’URI qui contient des propriétés de connexion qui le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] utilise pour établir une connexion au système Siebel. Vous devez spécifier un URI de connexion lorsque vous :  
  
-   Créer une fabrique de canaux ou d’un écouteur de canal à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de canal, ou créer un hôte de service ou client WCF à l’aide de la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] modèle de service.  
  
-   Créer une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour générer une classe de client WCF ou une interface de service WCF pour un [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] solution de modèle de service.  
  
-   Utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour extraire les schémas de message à partir de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   Utilisez l’outil Service Model Metadata Utility (svcutil.exe) pour générer une classe de client WCF, ou une interface de service WCF pour une solution de modèle de service WCF.  
  
 Les rubriques de cette section décrivent comment établir une connexion entre le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] et le système Siebel en fournissant des :  
  
-   Informations sur les propriétés de connexion et la structure de l’URI de connexion Siebel.  
  
-   Liens vers des rubriques qui montrent comment établir une connexion à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  

  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)