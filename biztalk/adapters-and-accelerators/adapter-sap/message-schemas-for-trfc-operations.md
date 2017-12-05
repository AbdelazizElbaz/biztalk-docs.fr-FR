---
title: "Schémas de message pour des opérations tRFC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tRFC operations, message structure for
- tRFC operations, message schemas for
- tRFC operations, message actions for
ms.assetid: 0e269555-f0a1-40ae-a1b5-d8c4981e730f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5667d2f6a9f18bbccbdebc0d5dc36ad73e4867ec
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-schemas-for-trfc-operations"></a>Schémas de message pour des opérations tRFC
Appels de fonction distants Transactiostructnal (tRFCs) sont utilisés pour exécuter des appels RFC dans une unité logique de travail (LUW). Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge plusieurs tRFCs par LUW pour les appels entrants tRFC. Pour les appels tRFC sortant (client), l’adaptateur peut prendre en charge uniquement un seul tRFC un LUW ; Il donc pour crée un LUW sur SAP pour chaque appel du client tRFC. Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les opérations tRFC, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). Cette section décrit les schémas de message et les actions pour les opérations tRFC.  
  
## <a name="message-structure-for-trfc-operations"></a>Structure de message pour des opérations tRFC  
 Chaque opération tRFC se compose d’un message de demande et un message de réponse (réponse). Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] associe un GUID de la transaction du système SAP ID (TID) qui identifie le LUW sur le système SAP. Ce GUID peut être présent dans les tRFC demande et réponse de messages dans la \<TransactionalRfcOperationIdentifier\> élément.  
  
-   Pour les appels sortants tRFC, vous pouvez passer un GUID à l’adaptateur dans le message de demande tRFC. Si vous ne fournissez pas un GUID, l’adaptateur génère un pour vous. L’adaptateur retourne toujours le GUID dans le message de réponse tRFC. Vous passez ce GUID dans l’opération RfcConfirmTransID pour confirmer le TID sur le système SAP.  
  
-   Pour les appels entrants tRFC, l’adaptateur transmet un GUID qu’il a généré et mappée au TID SAP dans le message de demande tRFC. Vous pouvez éventuellement retourner ce GUID dans le message de réponse.  
  
> [!IMPORTANT]
>  Dans certains scénarios, par exemple, pour résoudre un problème sur le système SAP, vous devrez peut-être la valeur réelle du TID SAP qui identifie le tRFC sur le système SAP. Vous pouvez obtenir la valeur du TID SAP qui est associé à un GUID en appelant le **ConvertGuidToTid** (méthode). Pour plus d’informations sur **ConvertGuidToTid**, consultez [des opérations spéciales](../../adapters-and-accelerators/adapter-sap/special-operations.md).  
  
 Le tableau suivant présente les schémas de message utilisés pour les opérations tRFC et pour l’opération RfcConfirmTransID. L’opération RfcConfirmTransID apparaissent par l’adaptateur afin que vous puissiez confirmer le TID SAP dans les appels client tRFC.  
  
|Opération|Structure XML| Description|  
|---------------|-------------------|-----------------|  
|tRFC<br /><br /> ([RFC_NAME])|`<[RFC_NAME] xmlns="[VERSION]/Trfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Trfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   …   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]>`|Appelle un tRFC sur le système SAP.<br /><br /> -Permet d’importer, modifier, et les paramètres table sont pris en charge.<br /><br /> -Permet d’importer et modification des paramètres peut être de TYPES DE STRUCTURE de SAP, les TYPES de tables SAP ou les types de données simples de SAP.<br /><br /> -appels de client tRFC n’ont pas de valeurs retournées dans la partie de la sortie. SAP exécute de manière asynchrone les avec uniquement les valeurs d’entrée côté.<br /><br /> Le \<TransactionalRfcOperationIdentifier\> élément :<br /><br /> -Pour les appels sortants tRFC, vous pouvez éventuellement spécifier un GUID qui doit être mappé sur le TID SAP par l’adaptateur de cet élément. Si un GUID n’est pas spécifié, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] génère un et le mappe le TID SAP pour le tRFC.<br /><br /> -Pour les appels entrants tRFC, l’adaptateur transmet le GUID qui est mappé sur le TID SAP dans cet élément.|  
|Réponse de tRFC<br /><br /> (Réponse [RFC_NAME])|`<[RFC_NAME]Response xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </[RFC_NAME]Response>`|Indique que la demande de modification a été envoyé au système SAP.<br /><br /> -appels de client tRFC n’ont pas de valeurs retournées dans la partie de la sortie. SAP exécute de manière asynchrone les avec uniquement les valeurs d’entrée côté.<br /><br /> Le \<TransactionalRfcOperationIdentifier\> élément :<br /><br /> -Pour les appels sortants tRFC, l’adaptateur envoie le GUID associé avec le TID SAP pour le tRFC dans cet élément.<br /><br /> -Pour les appels entrants tRFC, vous pouvez éventuellement retourner le GUID qui a été envoyé par l’adaptateur dans le message de demande.|  
|RfcConfirmTransID<br /><br /> (RfcConfirmTransID)|`<RfcConfirmTransID xmlns="[VERSION]/Trfc/">   <TransactionalRfcOperationIdentifier>GUID   </TransactionalRfcOperationIdentifier> </RfcConfirmTransID>`|L’opération RfcConfirmTransID confirme le TID utilisé dans une opération tRFC sortant sur le système SAP.<br /><br /> Le \<TransactionalRfcOperationIdentifier\> élément contient le GUID qui est mappé sur le TID associé à l’appel sortant tRFC. Vous devez le définir à la valeur du GUID qui a été retourné par l’adaptateur dans le message de réponse tRFC.<br /><br /> Pour plus d’informations sur l’opération RfcConfirmTransID, consultez [des opérations spéciales](../../adapters-and-accelerators/adapter-sap/special-operations.md).|  
|RfcConfirmTransIDResponse<br /><br /> (RfcConfirmTransIDResponse)|`<RfcConfirmTransIDResponse xmlns="[VERSION]/Trfc/"> </RfcConfirmTransIDResponse>`|Indique que le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] a confirmé le TID sur le système SAP.|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [RFC_NAME] = nom de la RFC ; par exemple, RFC_CUSTOMER_GET.  
  
 [IN_PARAM_NAME] = le nom du paramètre RFC importation.  
  
 [INOUT_PARAM_NAME] = le nom d’un paramètre RFC la modification.  
  
 [TABLE_PARAM_NAME] = le nom d’un paramètre de la Table de RFC.  
  
 [STRUCT_PARAM_NAME] = le nom d’un paramètre de Structure de RFC.  
  
 GUID = un GUID qui identifie le TID SAP associé à le tRFC.  
  
## <a name="message-actions-for-trfc-operations"></a>Actions de message pour des opérations tRFC  
 Le tableau suivant répertorie les actions de message qui sont utilisées pour les opérations tRFC.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|[RFC_NAME]|[VERSION] /Trfc/ [RFC_NAME]|http://Microsoft.LobServices.SAP/2007/03/Trfc/RFC_CUSTOMER_GET|  
|[RFC_NAME] Réponse|[VERSION] /Trfc/ [RFC_NAME] / réponse|http://Microsoft.LobServices.SAP/2007/03/Trfc/RFC_CUSTOMER_GET/Response|  
|RfcConfirmTransID|[VERSION] / Trfc/RfcConfirmTransID|http://Microsoft.LobServices.SAP/2007/03/Trfc/RfcConfirmTransID|  
|Réponse de RfcConfirmTransID|[/ Trfc/RfcConfirmTransID/réponse de la VERSION|http://Microsoft.LobServices.SAP/2007/03/Trfc/RfcConfirmTransID/Response|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [RFC_NAME] = nom de la RFC à appeler ; par exemple, RFC_CUSTOMER_GET.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)