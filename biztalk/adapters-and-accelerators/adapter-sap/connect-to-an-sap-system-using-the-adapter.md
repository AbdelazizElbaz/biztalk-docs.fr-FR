---
title: "Se connecter à un système SAP à l’aide de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection URI
- adapters, connecting to an SAP system
- connection string
ms.assetid: d506a948-5f4a-420b-a404-508824683099
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75f8c4b8650b2c81b3b82bf520958646e20da380
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-an-sap-system-using-the-adapter"></a>Se connecter à un système SAP à l’aide de l’adaptateur
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] exige que les clients de l’adaptateur fournir une chaîne de connexion, appelée la connexion identificateur URI (Uniform Resource) pour se connecter au système SAP. Avec un URI de connexion, les clients de carte peuvent spécifier des paramètres de connexion pour se connecter à un système externe. Pour plus d’informations sur l’URI de connexion, consultez [créer une connexion au système SAP](../../adapters-and-accelerators/adapter-sap/create-a-connection-to-the-sap-system.md).  
  
 Veillez à que respecter les consignes de sécurité lors de l’établissement d’une connexion avec un système SAP. Pour plus d’informations sur les règles de sécurité, consultez [sécuriser vos applications SAP](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md).
  
## <a name="how-many-connections-can-the-adapter-open-to-the-sap-system"></a>Le nombre de connexions peut la carte ouverte pour le système SAP ?  
 Par défaut, le système SAP permet aux clients d’ouvrir de 100 connexions au système SAP. Toutefois, vous pouvez définir une variable d’environnement sur l’ordinateur exécutant le système SAP pour augmenter la limite du nombre de connexions. Pour plus d’informations, consultez [dépanner les problèmes opérationnels avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation de l’architecture de l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/architecture-overview-of-the-biztalk-adapter-for-mysap-business-suite.md)