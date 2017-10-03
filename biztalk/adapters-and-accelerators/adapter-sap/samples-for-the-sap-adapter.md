---
title: "Exemples de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- samples, Data Provider for SAP
- samples, migration
- samples, BizTalk
- samples, WCF service model
- samples, WCF channel model
- samples
ms.assetid: 4654c458-83be-417f-ae54-5c3a8f6ab81f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0374aada037282a68e7575136b8671bba5ca181d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="samples-for-the-sap-adapter"></a>Exemples de l’adaptateur SAP
Exemples de [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] sont classés ainsi :  
  
-   Les exemples [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]  
  
-   Exemples de modèle de service WCF  
  
-   Exemples de modèle de canal WCF  
  
-   Les exemples [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)]  
  
-   Exemples de migration  
  
 Les exemples sont disponibles au [http://go.microsoft.com/fwlink/?LinkID=196854](http://go.microsoft.com/fwlink/?LinkID=196854).  
  
 La liste suivante contient les noms et descriptions des exemples pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="biztalk-server-samples"></a>Exemples de BizTalk Server  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|IDOCSend|Montre comment envoyer un IDOC à un système SAP.|  
|ReceiveIDOC|Montre comment recevoir un IDOC à partir d’un système SAP.|  
|ReceiveIDOC_SYSREL|Montre comment recevoir un IDOC à partir d’un système SAP. L’IDOC reçu a le numéro de version inférieur à la SYSREL SAP.|  
|RFCServer|Montre comment recevoir un appel de serveur RFC à partir du système SAP.|  
|SAPTransaction|Montre comment effectuer des transactions dans un système SAP à l’aide.|  
|tRFCClient|Montre comment effectuer des appels de client tRFC sur un système SAP.|  
  
## <a name="wcf-service-model-samples"></a>Exemples de modèle de Service WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|SapIdocStringClientSM|Montre comment envoyer un IDOC à un système SAP en appelant l’opération SendIdoc.|  
|SapRfcServerSM|Montre comment recevoir un appel de serveur RFC à partir d’un système SAP.|  
|SapBapiTxClientSM|Montre comment appeler des interfaces BAPI à l’intérieur d’une transaction sur un système SAP.|  
|SapTrfcClientSM|Montre comment appeler les appels du client tRFC sur un système SAP.|  
  
## <a name="wcf-channel-model-samples"></a>Exemples de modèle de canal WCF  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|SapIdocReceiveCM|Montre comment recevoir des IDOC à partir d’un système SAP|  
|SapRfcServerCM|Montre comment recevoir un appel de serveur RFC à partir du système SAP.|  
  
## <a name="data-provider-for-sap-samples"></a>Fournisseur de données pour obtenir des exemples SAP  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|SAP ado|Montre comment utiliser le [!INCLUDE[adoprovidersaplong](../../includes/adoprovidersaplong-md.md)].|  
  
## <a name="migration-samples"></a>Exemples de migration  
  
|Exemple de nom de répertoire| Description|  
|---------------------------|-----------------|  
|SAP_RFC_Migration|Montre comment utiliser un projet BizTalk créé à l’aide de la version précédente de l’adaptateur SAP et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le projet BizTalk contient une orchestration pour appeler le RFC SD_RFC_CUSTOMER_GET.|  
|SendIDOC_Migration|Montre comment utiliser un projet BizTalk créé à l’aide de la version précédente de l’adaptateur SAP et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le projet BizTalk contient une orchestration pour envoyer un IDOC à un système SAP.|  
|ReceiveIDOC_Migration|Montre comment utiliser un projet BizTalk créé à l’aide de la version précédente de l’adaptateur SAP et qu’il fonctionne avec la base de WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le projet BizTalk contient une orchestration pour appeler la réception un IDOC à partir d’un système SAP.|  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SAP](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)