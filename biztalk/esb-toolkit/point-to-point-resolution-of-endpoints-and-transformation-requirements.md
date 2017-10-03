---
title: "Résolution de point à point des points de terminaison et les exigences de Transformation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4c570bf-8274-4779-ae83-2aef2bf57ded
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8899c5f713f1c9ebfe299d3e431754dd8b9794d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="point-to-point-resolution-of-endpoints-and-transformation-requirements"></a>Résolution de point à point des points de terminaison et les exigences de Transformation
Dans ce cas de figure, un client de service Web appelle un service Web sans passer par l’architecture ESB. Les deux points de communiquent directement, mais avant que le client effectue l’appel, il doit résoudre le point de terminaison du service Web. L’appel au service Web peut être unidirectionnel ou requête-réponse. Un seul parvenir consiste à utiliser les fonctionnalités de résolution dynamique de l’architecture ESB, comme indiqué dans la Figure 1.  
  
 ![Point de &#45; à &#45; Résolution de point de terminaison](../esb-toolkit/media/ch3-pointtopoint.gif "Ch3-PointToPoint")  
  
 **Figure 1**  
  
 **Résolution des points de terminaison à l’aide de UDDI**  
  
 L’exemple de Service de résolution fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure. L’exemple montre comment appeler le Service de programme de résolution ESB pour effectuer la résolution, qui vous permet de tester la résolution que vous développez le contenu des magasins principaux, tels que Universal Description, Discovery and Integration (UDDI), XML Path Language (XPath), Statique, ou des stratégies dans le moteur de règles d’entreprise de BizTalk Server.  
  
 Pour plus d’informations, consultez [installer et exécuter l’exemple de Service de programme de résolution](../esb-toolkit/installing-and-running-the-resolver-service-sample.md).