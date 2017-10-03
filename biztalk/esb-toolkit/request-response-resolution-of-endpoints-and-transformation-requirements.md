---
title: "Résolution de requête-réponse des points de terminaison et les exigences de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a1bfdae-2651-402c-b164-16db663aaa95
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72f442f1d9df457a3c1384f1d717e29c17b433f4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="request-response-resolution-of-endpoints-and-transformation-requirements"></a>Résolution de requête-réponse des points de terminaison et les exigences de Transformation
Dans ce cas de figure, une application cliente envoie un message de demande pour une rampe d’entrée et reçoit une réponse. Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] agit en tant que médiateur entre le client et le point de terminaison du service cible et utilise le programme de résolution ESB et l’infrastructure d’adaptateurs pour effectuer la transformation du message dynamique et le routage en fonction de la configuration de démarrage, comme illustré dans la Figure 1.  
  
 ![Demande &#45; Résolution de réponse de points de terminaison](../esb-toolkit/media/ch3-requestresponse.gif "Ch3-requête-réponse")  
  
 **Figure 1**  
  
 **Résolution de requête-réponse des points de terminaison et les exigences de transformation**  
  
 L’exemple de résolution dynamique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. Il montre comment appliquer une transformation dynamique et la résolution pour des scénarios bidirectionnelle à l’aide de XML Path Language (XPath), Universal Description, Discovery, and Integration (UDDI), statique, ou les stratégies dans le moteur de règles d’entreprise de BizTalk Server.  
  
 Pour plus d’informations, consultez le scénario de messagerie bidirectionnels décrit dans [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).