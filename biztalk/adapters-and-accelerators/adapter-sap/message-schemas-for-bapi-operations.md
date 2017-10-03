---
title: "Schémas de message pour des opérations BAPI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAPI operations, message schemas for
- BAPI operations, message structure for
- BAPI operations, message actions for
ms.assetid: ef4d88e8-f31a-4b68-a303-6885b6f8c083
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 999e60a7e2cac827031ea2a19f9482d9da0baaa6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-bapi-operations"></a>Schémas de message pour des opérations BAPI
Les sections suivantes décrivent les schémas de message et les actions de message utilisées pour appeler des interfaces BAPI sur le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] en tant que méthodes d’objets métier. Vous pouvez également appeler des interfaces BAPI en tant qu’opérations RFC sur la carte. Pour plus d’informations sur les messages utilisés pour appeler les RFC, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md). Quelle que soit la façon dont vous appelez un BAPI sur la carte, l’adaptateur appelle toujours BAPI comme RFC sur le système SAP. Pour une vue d’ensemble de la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge BAPI, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
## <a name="message-structure-for-business-object-operations"></a>Structure du message pour les opérations d’objet métier  
 Le tableau suivant présente les schémas de message utilisées pour appeler une commande BAPI comme une méthode d’objet métier.  
  
|Opération|Structure XML| Description|  
|---------------|-------------------|-----------------|  
|[BUSOBJ_METHOD]|`<[BUSOBJ_METHOD] xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]>`|Appeler une méthode d’objet métier sur un système SAP.<br /><br /> Importation, la modification et les paramètres table sont pris en charge.|  
|[BUSOBJ_METHOD] Réponse|`<[BUSOBJ_METHOD]Response xmlns="[VERSION]/Bapi/[BUSOBJ]/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[BUSOBJ_METHOD]Response>`|Réponse de méthode d’objet métier.<br /><br /> Exporter, modifier, et les paramètres table sont pris en charge.<br /><br /> **Remarque** par défaut, les paramètres de la table ne sont pas signalées dans le message de réponse. Si vous avez besoin des paramètres de la table dans le message de réponse, vous devez passer les paramètres de table vide dans le message de demande.|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [BUSOBJ_METHOD] = le nom d’une méthode d’objet métier ; par exemple, CREATEFROMDAT2.  
  
 [IN_PARAM_NAME] = le nom d’un paramètre d’importation BAPI.  
  
 [OUT_PARAM_NAME] = le nom d’un paramètre d’exportation BAPI.  
  
 [INOUT_PARAM_NAME] = le nom d’une commande BAPI la modification du paramètre.  
  
 [TABLE_PARAM_NAME] = nom du paramètre de table BAPI.  
  
 [STRUCT_PARAM_NAME] = le nom d’un paramètre de structure BAPI.  
  
## <a name="message-actions-for-business-object-operations"></a>Actions de message pour les opérations d’objet métier  
 Le tableau suivant répertorie les actions de message qui sont utilisées pour appeler des interfaces BAPI en tant que méthodes d’objet métier.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|[BUSOBJ_METHOD]|[VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME]|http://Microsoft.LobServices.SAP/2007/03/BAPI/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2|  
|[BUSOBJ_METHOD] Réponse|[VERSION] /Bapi/ [BUSOBJ_NAME] / [BUSOBJ_METHOD] / [BAPI_RFC_NAME] / réponse|http://Microsoft.LobServices.SAP/2007/03/BAPI/BUS2032/CREATEFROMDAT2/BAPI_SALESORDER_CREATEFROMDAT2/Response|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [BUSOBJ_NAME] = nom de l’objet métier ; par exemple, BUS2032.  
  
 [BUSOBJ_METHOD] = la méthode de l’objet métier ; par exemple, CREATEFROMDAT2.  
  
 [BAPI_RFC_NAME] = nom de la RFC pour BAPI ; par exemple, BAPI_SALESORDER_CREATEFROMDAT2.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)