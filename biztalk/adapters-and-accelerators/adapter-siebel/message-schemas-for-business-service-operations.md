---
title: Schémas de message pour les opérations de Service d’entreprise | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message schemas, for business service methods
ms.assetid: ba23248b-5d73-4de0-9f7c-987cd88a4b63
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0062b8e6b6ce3961c937e9e5bece81cb24281049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-business-service-operations"></a>Schémas de message pour les opérations de Service d’entreprise
Un service d’entreprise Siebel est une collection de méthodes d’entreprise qui peuvent être appelées directement sur un système Siebel. Le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] met en évidence les méthodes de l’entreprise d’un service d’entreprise Siebel en tant qu’opérations.  
  
## <a name="message-schemas-for-siebel-business-service-method-operations"></a>Schémas de message pour des opérations Siebel Business Service (méthode)  
 Le tableau suivant présente les schémas de message pour les opérations de méthode du service d’entreprise Siebel exposées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
|Opération|Structure XML| Description|  
|---------------|-------------------|-----------------|  
|[Business_Service_METHOD_NAME]|Message de demande de méthode de Service Business :<br /><br /> `<[METHOD_NAME] xmlns="[VERSION]/BusinessServices/[Business Service]/Operation">   <[METHOD_NAME]RequestRecord>     <[I_PRM1_NAME]>value1</[I_PRM1_NAME]>     <[I_PRM2_NAME]>value2</[I_PRM2_NAME]>     …   </[METHOD_NAME]RequestRecord>   <[METHOD_NAME]InOutRecord>     <[IO_PRM1_NAME]>value1</[IO_PRM1_NAME]>     <[IO_PRM2_NAME]>value2</[IO_PRM2_NAME]>     …   </[METHOD_NAME]InOutRecord> </[METHOD_NAME]>`<br /><br /> [VERSION] = la chaîne de version de message ; par exemple, « http://Microsoft.LobServices.Siebel/2007/03 ».<br /><br /> [Business Service] = nom du service de l’entreprise ; par exemple, ExtractDataService.<br /><br /> [Nom_méthode] = nom de la méthode de service d’entreprise ; par exemple, ExecuteNext.<br /><br /> [I_PRM_NAME] = Paramètres noms de IN.<br /><br /> [IO_PRM_NAME] = les noms de dans les paramètres.<br /><br /> Message de réponse de méthode de Service d’entreprise :<br /><br /> `<[METHOD_NAME]Response xmlns="[VERSION]/BusinessServices/[Business Service]/Operation">   <[METHOD_NAME]Result>     <[O_PRM1_NAME]>value1</[O_PRM1_NAME]>     <[O_PRM2_NAME]>value2</[O_PRM2_NAME]>     …   </[METHOD_NAME]Result>   <[METHOD_NAME]InOutRecord>     <[IO_PRM1_NAME]>value1</[IO_PRM1_NAME]>     <[IO_PRM2_NAME]>value2</[IO_PRM2_NAME]>     …   </[METHOD_NAME]InOutRecord > </[METHOD_NAME]Response>`<br /><br /> [VERSION] = la chaîne de version de message ; par exemple, « http://Microsoft.LobServices.Siebel/2007/03 ».<br /><br /> [Business Service] = nom du service de l’entreprise ; par exemple, ExtractDataService.<br /><br /> [Nom_méthode] = nom de la méthode de service d’entreprise ; par exemple, ExecuteNext.<br /><br /> [O_PRM_NAME] = les paramètres de noms de sortie.<br /><br /> [IO_PRM_NAME] = Paramètres noms INOUT.<br /><br /> **Important :** les paramètres OUT IN et OUT sont toujours marquées comme facultatives dans les métadonnées, même s’ils requis par le système Siebel. Par conséquent, si un paramètre est marqué comme facultatif dans les métadonnées, mais il est requis par le système Siebel, l’adaptateur génère le `TargetSystemException` comme reçu de Siebel et non le `XmlReaderParsingException`.|La méthode de service d’entreprise Siebel est présentée comme un nom d’opération.<br /><br /> -DANS, dans paramètres OUT et OUT sont prises en charge.<br /><br /> -Types hiérarchiques sont exposés en tant que chaînes. L’adaptateur Siebel ne valide pas les valeurs passées pour ces chaînes. Si ces valeurs ne sont pas conformes aux schémas attendus par le système Siebel, une exception d’exécution est générée.|  
  
## <a name="message-actions-for-siebel-business-service-method-operations"></a>Actions de message pour des opérations Siebel Business Service (méthode)  
 Le tableau suivant présente la manière dont l’action SOAP pour une méthode de Service d’entreprise Siebel est constituée. Seul l’action du message de demande est affiché, l’action dans le pour le message de réponse est formé en ajoutant « / réponse » à l’action de message de demande. par exemple, « [VERSION] / BusinessServices/ExtractDataService/ExecuteNext/réponse ».  
  
|Opération|Action| Description|  
|---------------|------------|-----------------|  
|[Business_Service_METHOD_NAME]|[VERSION] /BusinessServices/ [Service métier] / [Business_Service_METHOD_NAME]|[VERSION] / BusinessServices/ExtractDataService/ExecuteNext|  
  
 [VERSION] = la chaîne de version de message ; par exemple, « http://Microsoft.LobServices.Siebel/2007/03 ».  
  
 [Business Service] = nom du service de l’entreprise ; par exemple, ExtractDataService.  
  
 [Business_Service_METHOD_NAME] = nom de la méthode de service d’entreprise ; par exemple, ExecuteNext.  
  
 Vous devez spécifier explicitement l’action du message lorsque vous consommez le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] dans une solution BizTalk Server ou en utilisant le modèle de canal WCF. Pour plus d’informations, consultez [développer vos applications Siebel](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md).  
  
## <a name="siebel-business-service-wcf-client-methods"></a>Méthodes de Client Siebel Business Service WCF  
 Le tableau suivant présente la [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] signature de méthode de modèle service qui est généré par le [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] pour Siebel des méthodes de services professionnels.  
  
|Opération|Méthode de modèle de Service WCF|  
|---------------|------------------------------|  
|[Business_Service_METHOD_NAME]|`[Business_Service_METHOD_NAME]ResponseRecord client.[Business_Service_METHOD_NAME]([Business_Service_METHOD_NAME]RequestRecord);`<br /><br /> [Business_Service_METHOD_NAME] = nom de méthode de service métier ; par exemple, ExecuteNext.|  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)