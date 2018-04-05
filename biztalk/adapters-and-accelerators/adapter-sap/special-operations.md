---
title: Opérations spéciales | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- operations, special operations surfaced by the SAP adapter
ms.assetid: 8725fe63-6ff4-49c8-b386-d4c67e2be440
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe2472d905e9e726b827d44da79bdfe840233354
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="special-operations"></a>Opérations spéciales
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expose plusieurs opérations spéciales. Ces opérations ne sont pas basées sur les artefacts du système SAP. Elles sont signalées pour fournir des fonctionnalités pour les applications clientes de carte. Les opérations spéciales sont :  
  
-   **RfcGetAttributes**. Cette opération est exposée en surface sous le nœud RFC et expose les fonctionnalités du SDK RFC. Il fournit les informations suivantes sur la connexion RFC :  
  
    -   L’ID du système  
  
    -   La page de codes du partenaire  
  
    -   La langue  
  
     Pour plus d’informations sur l’opération RfcGetAttributes y compris son schéma de message, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).  
  
-   **RfcConfirmTransID**. Cette opération est exposée en surface sous le nœud TRFC et expose les fonctionnalités du SDK RFC. Cette opération vous permet de confirmer l’ID de transaction de SAP sur le système SAP.  
  
     Pour plus d’informations sur la façon d’utiliser l’opération RfcConfirmTransID et son schéma de message, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
-   **chaîne SapAdapterUtilities.ConvertGuidToTid(Guid)**. Il s’agit d’une méthode publique exposée par l’assembly d’adaptateur SAP. (Il n’est pas une opération par l’adaptateur.) Il retourne la transaction SAP ID (TID) mappé sur le GUID spécifié.  
  
     En interne, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] mappe la transaction SAP ID (TID) qui identifie une unité logique de travail (LUW) sur le système SAP sur un GUID. Ce GUID est exposé aux clients de la carte, afin qu’ils peuvent s’engager un tRFC (LUW) en appelant l’opération RfcConfirmTransID pour confirmer son TID sur le système SAP.  
  
     Toutefois, pour certains scénarios, vous devrez peut-être le TID est associé à un tRFC. Par exemple, vous souhaiterez identifier le LUW sur le système SAP pour résoudre un problème. Pour ces scénarios, vous pouvez appeler **ConvertGuidToTid**. Pour utiliser **ConvertGuidToTid** dans votre code, vous devez ajouter une référence à l’assembly d’adaptateur SAP à votre projet.  
  
     Pour plus d’informations sur l’appel de tRFCs, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). L’exemple suivant montre comment appeler **ConvertGuidToTid**.  
  
    ```  
    // messageGuid is the GUID associated with a tRFC or IDOC  
  
    string tid = SapAdapterUtilities.ConvertGuidToTid(messageGuid);  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)