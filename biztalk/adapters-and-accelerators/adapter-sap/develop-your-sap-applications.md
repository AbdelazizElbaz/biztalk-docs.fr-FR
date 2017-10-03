---
title: "Développer vos applications SAP à l’aide de l’adaptateur dans BizTalk | Documents Microsoft"
description: "Créer mes applications SAP à l’aide de WCF, BizTalk Server ou ADO.NET avec le Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, use adapters
- adapters, working with
- working with adapters
ms.assetid: e8315c0d-923b-433e-9d11-4e8a53e0a1d9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50e8501249c460285f6f8dd429f8990d39e810e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-your-sap-applications"></a>Développer vos applications SAP

## <a name="overview"></a>Vue d'ensemble
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] est un [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] liaison personnalisée. Les applications clientes peuvent consommer le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour appeler des opérations sur les artefacts SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] peuvent être utilisés :  
  
-   Via une liaison de port physique dans un [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] solution.  
  
-   En appelant des méthodes sur une instance d’un proxy client.  
  
-   Un service WCF hébergé.  
  
-   En envoyant des messages SOAP via une instance de canal dans le code qui utilise le modèle de canal WCF.  
  
-   Via l’interface ADO.NET.  

## <a name="biztalk-vs-wcf-service-vs-wcf-channel-vs-adonet"></a>Vs pour le service WCF BizTalk vs WCF de canal et ADO.NET
  
 Le tableau suivant :  
  
-   Répertorie les différentes opérations qui peuvent être effectuées sur un système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Indique laquelle des approches ([!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], WCF service model, modèle de canal WCF ou interface ADO.NET) peut être utilisé pour effectuer les opérations.  
  
-   Fournit des liens vers plus d’informations sur l’exécution de la tâche à l’aide de l’approche choisie.  
  
|Tâche|BizTalk Server|Modèle de Service WCF|Modèle de canal WCF|Interface ADO.NET|  
|----------|--------------------|-----------------------|-----------------------|-----------------------|  
|Appel de RFC dans un système SAP|[Appeler les RFC dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)|[Appeler les RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-the-wcf-service-model.md)|[Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)|[Appeler les RFC et BAPI à l’aide de la commande EXEC dans SAP](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-and-bapis-using-the-exec-command-in-sap.md)|  
|Recevoir des appels RFC entrants à partir d’un système SAP|[Recevoir des appels de RFC entrants à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)|[Recevoir des appels entrants de RFC dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-in-sap-using-the-wcf-service-model.md)|[Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|L’appel de tRFCs dans un système SAP|[Appeler tRFCs dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)|[Appeler tRFCs dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-the-wcf-service-model.md)|[Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Recevoir des appels entrants tRFC d’un|[Réception entrant tRFC appelle à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)|[Réception entrant tRFC appelle dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-in-sap-using-the-wcf-service-model.md)|[Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  
|Exécution de transactions sur un système SAP|[Exécutez BAPI Transactions dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)|[Appeler les BAPI dans SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/invoke-bapis-in-sap-using-the-wcf-service-model.md)|[Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Envoyer un IDOC à un système SAP|[Envoyer des IDOC à SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)|[Envoyer des IDOC à SAP à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-the-wcf-service-model.md)|[Appeler des opérations sur le système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/invoke-operations-on-the-sap-system-using-the-wcf-channel-model.md)||  
|Réception d’un IDOC à partir d’un système SAP|[Recevoir des IDOC SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)||[Opérations entrantes de réception à partir du système SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)||  

## <a name="next-steps"></a>Étapes suivantes

 Les rubriques suivantes fournissent des informations sur les procédures et des exemples pour développer des applications qui consomment le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] dans les deux [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], et [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] programmation de solutions. 

- [Créer une connexion au système SAP](create-a-connection-to-the-sap-system.md)
- [Obtenir les métadonnées pour les opérations de SAP dans Visual Studio](get-metadata-for-sap-operations-in-visual-studio.md)
- [Utilisez les propriétés de liaison](read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md)
- [Diffusion en continu et l’adaptateur SAP](streaming-and-the-sap-adapter.md)
- [Développer des applications BizTalk à l’aide de l’adaptateur SAP](develop-biztalk-applications-using-the-sap-adapter.md)
- [Développer des applications à l’aide du modèle de Service WCF](develop-sap-applications-using-the-wcf-service-model.md)
- [Développer des applications à l’aide du modèle de canal WCF](develop-sap-applications-using-the-wcf-channel-model.md)
- [Obtenir les métadonnées par programme](get-metadata-programmatically-from-sap.md)
- [Utiliser le fournisseur de données .NET Framework pour mySAP](use-the-net-framework-data-provider-for-mysap-business-suite.md)
- [Utilisez l’adaptateur SAP avec SharePoint](use-the-sap-adapter-with-sharepoint.md)
- [Exemples](samples-for-the-sap-adapter.md)
- [Utiliser svcutil.exe](use-the-servicemodel-metadata-utility-with-the-sap-adapter-in-biztalk.md) 
 
  
## <a name="see-also"></a>Voir aussi  
 [Créer l’URI de connexion au système SAP](create-the-sap-system-connection-uri.md)