---
title: "Développer des applications BizTalk à l’aide de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk applications, developing
- developing, BizTalk applications
ms.assetid: 4aa10897-a08e-4fc3-9c1f-40485d204273
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75e70a52f12227b1bde3a43f9330c6fe373ac5a3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sap-adapter"></a>Développer des applications BizTalk à l’aide de l’adaptateur SAP
Développement d’applications BizTalk implique la création d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma XML. Une fois que vous avez généré le schéma, vous pouvez utiliser le routage basé sur le contenu (CBR) ou créer des orchestrations BizTalk pour envoyer et recevoir des messages conformes au schéma généré.  
  
 CBR peut être utilisé dans les scénarios où les messages envoyés au système SAP nécessitent un traitement intensif. Par exemple, si vous savez que le port de réception recevra les messages uniquement d’un certain type, vous pouvez ajouter un filtre au port d’envoi pour acheminer les messages correspondant à l’expression de filtre pour le port d’envoi.  
  
 Dans les orchestrations BizTalk, vous créez envoi et ports de réception pour envoyer et recevoir des messages vers et depuis le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)], qui à son tour envoie des messages à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Cette section fournit des informations sur l’utilisation des orchestrations BizTalk pour effectuer des opérations sur le système SAP en utilisant le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à son tour utilise le [!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)] adaptateur qui peut interagir avec une liaison WCF.  
  
> [!IMPORTANT]
>  Pour utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez toujours définir la **EnableBizTalkCompatibilityMode** liaison de propriété **True**. Pour plus d’informations sur la définition des propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Conditions préalables pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/prerequisites-to-create-sap-applications.md)
  
-   [Blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)
  
-   [Appeler les RFC dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)  
  
-   [Recevoir des appels de RFC entrants à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-rfc-calls-from-sap-using-biztalk-server.md)  
  
-   [Appeler tRFCs dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md)  
  
-   [Réception entrant tRFC appelle à partir de SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-inbound-trfc-calls-from-sap-using-biztalk-server.md)  
  
-   [Exécutez BAPI Transactions dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/run-bapi-transactions-in-sap-using-biztalk-server.md)  
  
-   [Envoyer des IDOC à SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/send-idocs-to-sap-using-biztalk-server.md)  
  
-   [Recevoir des IDOC SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-using-biztalk-server.md)  
  
-   [Recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md)  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SAP](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)