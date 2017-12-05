---
title: "Assemblys et des artefacts installés par l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d9ffdc4-1721-4202-839c-04e5bffe8668
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee337b56c6e0901de6b02b28df69101ad3aaf3ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="assemblies-and-artifacts-installed-by-the-dynamic-resolution-sample"></a>Assemblys et des artefacts installés par l’exemple de résolution dynamique
Le tableau suivant répertorie les assemblys et les artefacts installés par le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple de résolution dynamique.  
  
|Emplacement|Catégorie|Nom et la version du composant|  
|--------------|--------------|---------------------------------------|  
|Application BizTalk GlobalBank.ESB|Orchestrations|(aucun)|  
|Application BizTalk GlobalBank.ESB|Ports d'envoi|DynamicResolutionSolicitResp|  
|||DynamicResolutionOneWay|  
|Application BizTalk GlobalBank.ESB|Ports de réception|DynamicResolutionReqResp|  
|||DynamicResolution|  
|Application BizTalk GlobalBank.ESB|Emplacements de réception|DynamicResolutionReqResp_SOAP<br /><br /> DynamicResolution_FILE|  
|Application BizTalk GlobalBank.ESB|Schémas|GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderDoc Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.NAOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderDoc Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNOrderResponse Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas.CNPurchaseOrderDoc Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Pipelines|GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveSendXMLXML Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBReceiveXML Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Pipelines.ESBPassThrough Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Ressources|GlobalBank.ESB.DynamicResolution.Pipelines Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms Version 2.0.0.0|  
|Application BizTalk GlobalBank.ESB|Stratégies|CanadaSubmitOrderMaps.xml|  
|||GetCanadaEndPoint.xml|  
|||GetCanadaPurchaseEndPoint.xml|  
|||ResolveMap.xml|  
|||ResolveEndPoint.xml|  
|Application BizTalk GlobalBank.ESB|Vocabulaires|DynamicRunTimeDocSpecs.xml<br /><br /> DynamicRunTimeEndPoints.xml<br /><br /> DynamicRunTimeMapTypes.xml<br /><br /> DynamicRunTimeServiceActions.xml|  
|Application BizTalk GlobalBank.ESB|Cartes|GlobalBank.ESB.DynamicResolution.Transforms.SubmitPurchaseOrderResponseCN_To_SubmitOrderResponseNA Version = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitOrderRequestCN Version = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderRequestNA_To_SubmitPurchaseOrderRequestCN Version = 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms.SubmitOrderResponseCN_To_SubmitOrderResponseNA Version = 2.0.0.0|  
|Cache d’assembly global|Assemblys|GlobalBank.ESB.DynamicResolution.Pipelines Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Schemas Version 2.0.0.0|  
|||GlobalBank.ESB.DynamicResolution.Transforms Version 2.0.0.0|  
|%Program Files%\\BizTalk Server\Pipeline composants|Composants de pipeline|(aucun)|