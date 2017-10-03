---
title: "Les opérations sont prises en charge par l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: operations, performing by using the adapter
ms.assetid: 800cf44b-357f-4850-8878-f49ceb549adf
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40bfb247ff0f3af2abeec584c5fd079f392cd18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-siebel-adapter"></a>Les opérations sont prises en charge par l’adaptateur Siebel
Les clients de carte peuvent effectuer des opérations sur le système Siebel par soit :  
  
-   Création de projets BizTalk.  
  
-   À l’aide du modèle de canal WCF.  
  
-   À l’aide du modèle de service WCF.  
  
 Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expose les opérations que les applications peuvent appeler dessus et qu’il peut, à son tour, appeler sur applications. Ces opérations sont appelées en envoyant des messages SOAP sur un canal. Si une réponse est requise, il est retourné dans un message SOAP sur le même canal. Pour plus d’informations sur la structure du message et l’action SOAP associée à chaque opération, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md).  
  
 Cette section fournit des informations sur les opérations prises en charge sur le système Siebel en utilisant le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] ne prend pas en charge la réception des appels entrants à partir d’un système Siebel.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Opérations sur les composants d’entreprise Siebel](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md)  
  
-   [Opérations sur les Services métier de Siebel](../../adapters-and-accelerators/adapter-siebel/operations-on-business-services-in-siebel.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/overview-of-biztalk-adapter-for-siebel-ebusiness-applications.md)