---
title: "Schémas de message pour des opérations RFC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RFC operations, message structure for
- RFC operations, message actions for
ms.assetid: 50cd9b28-2e66-4c76-9d19-f0da6e7b8e10
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9d1dfe3ff3cef27269facfe89d3aea8f43cb10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-schemas-for-rfc-operations"></a>Schémas de message pour des opérations RFC
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] surfaces SAP appels RFC (Remote Function) en tant qu’opérations. Cette rubrique contient des informations sur les schémas de message et les actions de message utilisées pour les opérations de RFC. La structure du message est le même pour les opérations de RFC entrantes et sortantes. Pour une vue d’ensemble des opérations RFC qui prend en charge de l’adaptateur, consultez [opérations sur les documents RFC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).  
  
 Vous pouvez également appeler des interfaces BAPI en tant qu’opérations RFC sur la carte. Un exemple de la structure du message pour un appel de ce type est inclus dans cette rubrique.  
  
## <a name="message-structure-for-rfc-operations"></a>Structure de message pour des opérations RFC  
 Le tableau suivant présente les schémas de message RFC. Chaque opération RFC se compose d’un message de demande et un message de réponse (réponse).  
  
|Message|Structure de Message XML| Description|  
|-------------|---------------------------|-----------------|  
|RFC<br /><br /> ([RFC_NAME])|`<[RFC_NAME] xmlns="[VERSION]/Rfc/">   <IN1_PARAM_NAME>v1</IN1_PARAM_NAME>   <IN2_PARAM_NAME>v2</IN2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME xmlns="[VERSION]/Types/Rfc/">     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]>`|Appeler une commande RFC sur le système SAP.<br /><br /> -Permet d’importer, modifier, et les paramètres table sont pris en charge.<br /><br /> -Permet d’importer et modification des paramètres peut être de TYPES DE STRUCTURE de SAP, les TYPES de tables SAP ou les types de données simples de SAP.|  
|RFC réponse (réponse [RFC_NAME])|`<[RFC_NAME]Response xmlns="[VERSION]/Rfc/">   <OUT1_PARAM_NAME>v1</OUT1_PARAM_NAME>   <OUT2_PARAM_NAME>v2</OUT2_PARAM_NAME>   …   <INOUT1_PARAM_NAME>v3</INOUT1_PARAM_NAME>   <INOUT2_PARAM_NAME>v4</INOUT2_PARAM_NAME>   …   <TABLE1_PARAM_NAME>     <STRUCT1_PARAM_NAME>       <[FIELD1_NAME]>value1</[FIELD1_NAME]>       <[FIELD2_NAME]>value2</[FIELD2_NAME]>       …     </STRUCT1_PARAM_NAME>     …   </TABLE1_PARAM_NAME>   … </[RFC_NAME]Response>`|RFC retournée.<br /><br /> -Permet d’exporter, modifier, et les paramètres table sont pris en charge.<br /><br /> **Remarque :** par défaut, les paramètres de la table ne sont pas signalées dans le message de réponse. Si vous avez besoin des paramètres de la table dans le message de réponse, vous devez passer les paramètres de table vide dans le message de demande.<br /><br /> -Permet d’importer et modification des paramètres peut être de TYPES DE STRUCTURE de SAP, les TYPES de tables SAP ou les types de données simples de SAP.|  
|RfcGetAttributes<br /><br /> (RfcGetAttributes)|`<RfcGetAttributes> </RfcGetAttributes>`|RfcGetAttributes est une opération d’API du Kit de développement logiciel RFC qui est visible par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. L’opération RfcGetAttributes permet à un programme client récupérer la langue, l’ID du système et la page de codes du partenaire qui sont associés à la connexion RFC.|  
|Réponse de RfcGetAttributes<br /><br /> (RfcGetAttributesResponse)|`<RfcGetAttributesResponse>   <Language>lang</Language>   <SysId>id</SysId>   <PartnerCodePage>pnrcp</PartnerCodePage> </RfcGetAttributesResponse>`|La réponse à l’opération RfcGetAttributes renvoie la langue, l’ID du système et la page de codes du partenaire qui sont associés à la connexion RFC.|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.SAP/2007/03.  
  
 [RFC_NAME] = nom de la RFC ; par exemple, RFC_CUSTOMER_GET.  
  
 [IN_PARAM_NAME] = nom du paramètre d’importation de RFC.  
  
 [OUT_PARAM_NAME] = le nom d’un paramètre RFC exporter.  
  
 [INOUT_PARAM_NAME] = le nom d’un paramètre RFC la modification.  
  
 [TABLE_PARAM_NAME] = le nom d’un paramètre de la Table de RFC.  
  
 [STRUCT_PARAM_NAME] = le nom d’un paramètre de Structure de RFC.  
  
## <a name="message-actions-for-rfc-operations"></a>Actions de message pour des opérations RFC  
 Le tableau suivant répertorie les actions de message pour des opérations RFC.  
  
|Opération|Action du message|Exemple|  
|---------------|--------------------|-------------|  
|[RFC_NAME]|[VERSION] /Rfc/ [RFC_NAME]|http://Microsoft.LobServices.SAP/2007/03/RFC/RFC_CUSTOMER_GET|  
|[RFC_NAME] Réponse|[VERSION] /Rfc/ [RFC_NAME] / réponse|http://Microsoft.LobServices.SAP/2007/03/RFC/RFC_CUSTOMER_GET/Response|  
|RfcGetAttributes|[VERSION] / RfcGetAttributes|http://Microsoft.LobServices.SAP/2007/03/RfcGetAttributes|  
|Réponse de RfcGetAttributes|[/ RfcGetAttributes/réponse de la VERSION|http://Microsoft.LobServices.SAP/2007/03/RfcGetAttributes/Response|  
  
 [VERSION] = la chaîne de version de message ; par exemple, http://Microsoft.LobServices.Sap/2007/03.  
  
 [RFC_NAME] = nom de la RFC à appeler ; par exemple, RFC_CUSTOMER_GET.  
  
## <a name="invoking-a-bapi-as-an-rfc-operation"></a>Appel d’une commande BAPI sous forme d’opération RFC  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des interfaces BAPI comme opérations RFC et en tant que méthodes d’objets métier. En tant qu’opérations de RFC, BAPI sont signalées par nom. Pour plus d’informations sur l’appel des interfaces BAPI à l’aide de l’interface d’objet métier, consultez [opérations sur les BAPI dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-bapis-in-sap.md).  
  
 Le code XML suivant montre la structure de message pour un BAPI (BAPI_CUSTOMER_GETDETAIL2) qui est appelé dans une demande de changement. L’action du message pour cette opération est : http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_CUSTOMER_GETDETAIL2.  
  
```  
<BAPI_CUSTOMER_GETDETAIL2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <COMPANYCODE>1001</COMPANYCODE>  
  <CUSTOMERNO>0000001001</CUSTOMERNO>  
  <CUSTOMERBANKDETAIL>  
    <BAPICUSTOMER_02 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <CUSTOMER />  
      <BANK_CTRY />  
      <BANK_KEY />  
      <BANK_ACCT />  
      <CTRL_KEY />  
      <PARTNER_BK />  
      <COLL_AUTH />  
      <BANK_REF />  
    </BAPICUSTOMER_02>  
  </CUSTOMERBANKDETAIL>  
</BAPI_CUSTOMER_GETDETAIL2>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)