---
title: "Opérations sur les documents RFC dans SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, operations on RFCs
- adapters, operations on IDOCs
- RFC, receiving inbound RFC calls from an SAP system
- RFCs, invoking RFCs on an SAP system
- adapters, operations on BAPIs
- RFC client
- adapters, operations on tRFCs
- RFC server
ms.assetid: ca1b7b00-a9cf-41bc-b87c-2e7ce8cff65c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd4ebbb33e9f9791589a3ef271412c8ae20090f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="operations-on-rfcs-in-sap"></a>Opérations sur les documents RFC dans SAP
Vous pouvez utiliser la[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] à la fois en tant que RFC client et un serveur RFC. Dans les scénarios de client RFC, votre application appelle les RFC sur le système SAP en effectuant des opérations RFC sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Dans des scénarios de serveur RFC SAP système appelle les RFC sur le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], qui appelle à son tour, le document RFC sous forme d’opération sur votre application.  
  
## <a name="rfc-operations"></a>Opérations RFC  
 RFC sont signalées par un nom en tant qu’opérations sous le nœud de catégorie de métadonnées RFC par la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. (Vous pouvez parcourir ou rechercher les RFC sous le **RFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] ou [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].)  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peuvent apparaître uniquement ces documents RFC pour lequel il peut récupérer les métadonnées à partir du système SAP. L’adaptateur utilise le SDK RFC pour récupérer ces métadonnées, afin qu’il ne peut pas surface RFC qui contiennent des paramètres avec des types de données qui ne sont pas pris en charge par le SDK RFC. Par exemple, l’adaptateur ne peut pas surface RFC qui contiennent des structures de type ITAB II ou tables.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge les éléments suivants sur les normes RFC :  
  
-   Paramètres d’importation  
  
-   Paramètres d’exportation  
  
-   MODIFICATION des paramètres  
  
 Pour plus d’informations sur les structures de message et les actions de SOAP utilisées pour les RFC par l’adaptateur, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).  
  
## <a name="invoking-rfcs-on-an-sap-system"></a>Appel de RFC sur un système SAP  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence les RFC en tant qu’opérations individuelles qui prennent le nom de la RFC sur le système SAP. Pour appeler une commande RFC sur le système SAP, vous appelez l’opération RFC nommée de façon appropriée sur la carte.  
  
 Pour plus d’informations sur :  
  
-   Appel d’une commande RFC à l’aide de BizTalk Server, consultez [RFC de code non managé à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).  
  
-   Appel d’une demande de changement en utilisant le modèle de service WCF, consultez [appeler les RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md).  
  
-   Appel d’une commande RFC à l’aide du modèle de canal WCF, consultez [appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md).  
  
## <a name="receiving-inbound-rfc-calls-from-an-sap-system"></a>Appels entrants RFC réception à partir d’un système SAP  
 Il est possible pour SAP agir comme un client et appeler des modules de fonction sur un serveur RFC externe. Cette fonctionnalité permet de :  
  
-   SAP pour des notifications push vers des systèmes externes sans les systèmes externes devoir interroger continuellement SAP pour les notifications en appelant les RFC.  
  
-   L’implémentation de la logique métier en dehors du système SAP. Le système SAP peut ensuite appeler le programme externe sur le serveur RFC.  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut agir comme un serveur RFC pour recevoir ces RFC les appels entrants à partir du système SAP. Lorsque l’adaptateur reçoit un appel RFC à partir de SAP, il appelle cette opération RFC sur votre application.  
  
 Pour l’adaptateur comme un serveur RFC :  
  
-   Le document RFC doit être déclaré dans le système SAP. Il s’agit donc de l’adaptateur peut récupérer les métadonnées qui décrivent la RFC à partir du système SAP. Le document RFC est réellement implémenté dans votre application.  
  
-   L’adaptateur doit inscrire avec une destination RFC sur la passerelle SAP. L’inscription est basée sur un nom logique est appelé un ID de programme. Vous fournissez des paramètres dans l’URI pour spécifier l’ID de programme, passerelle SAP et de SAP de serveur pour cet enregistrement de connexion.  
  
 L’exemple suivant montre le code ABAP requis pour appeler une commande RFC via l’ID de programme, MYDEST.  
  
```  
CALL FUNCTION ‘ABC’ DESTINATION ‘MYDEST’  
```  
  
 Pour plus d’informations sur :  
  
-   Réception d’un appel de serveur RFC à l’aide de BizTalk Server, consultez [recevoir des appels RFC entrant par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md).  
  
-   Réception d’un appel de serveur RFC à l’aide du modèle de service WCF, consultez [recevoir des appels RFC entrant dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md).  
  
-   Réception d’un appel de serveur RFC à l’aide du modèle de canal WCF, consultez [de réception des opérations de trafic entrant à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).  
  
## <a name="special-rfc-operations"></a>Opérations RFC spéciaux  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peut également effectuer certaines opérations RFC spéciale sur le système SAP. Une telle opération est RfcGetAttributes.  
  
-   **RfcGetAttributes**. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise cette opération pour obtenir des informations sur les paramètres de connexion RFC comme ID système, page de codes de partenaire et language. Cette opération n’est disponible sous la **RFC** nœud lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] et [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 Pour plus d’informations sur la structure de message et l’action SOAP pour l’appel d’une opération RfcGetAttributes sur le système SAP, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Quelles opérations peuvent être effectuées à l’aide de la carte ?](https://msdn.microsoft.com/library/cc185219(v=bts.10).aspx)