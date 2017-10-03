---
title: "Composants d’interopérabilité ESB Pipeline | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25f9fb9d-d3d4-4df8-8e81-38b432f42ccf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccf4d4353e6928b998d31e8096ee642cd80bb60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="esb-pipeline-interop-components"></a>Composants Interop Pipeline ESB
Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] fournit la prise en charge des composants et services, notamment les suivantes :  
  
-   **Composants de pipeline JMS.** Ces composants reconnaîtront, valider et exposent les métadonnées et le contenu des messages conformes au format JMS MQRFH2 utilisé par les systèmes de messagerie IBM MQSeries. Cette fonctionnalité permet une [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] application à recevoir des messages et envoyer des messages aux systèmes JMS via MQ Series. Les composants automatiquement promouvoir les informations d’en-tête et rétrograder du contenu du message.  
  
-   **Composants de pipeline Namespace.** Ces composants peuvent ajouter ou supprimer des espaces de noms dans le contenu des messages XML. Cela permet aux applications réparer des espaces de noms en conflit ou ajouter des espaces de noms manquant pour éviter les collisions d’espace de noms dans les orchestrations de base de données et application de boîte de Message. Les composants permettent également de BizTalk Server consommer POX (Plain Old XML) sans modifier la publication des systèmes externes.  
  
 Pour plus d’informations sur les composants de pipeline ESB, consultez [à l’aide de composants de prise en charge du Pipeline](../esb-toolkit/using-the-pipeline-support-components.md).