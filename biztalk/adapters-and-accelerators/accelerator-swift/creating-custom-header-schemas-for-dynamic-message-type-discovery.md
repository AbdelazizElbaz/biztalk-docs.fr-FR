---
title: "Création de schémas d’en-tête personnalisé pour la découverte de Type dynamique Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, dynamic resolution
- schemas, message types
- schemas, custom headers
- header schemas
ms.assetid: 0c936c57-b533-47ca-9258-576b021fd016
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: befed0c7e7f5754cdf901e91698ed7269621d4b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-custom-header-schemas-for-dynamic-message-type-discovery"></a>Création de schémas d’en-tête personnalisé pour la détection de Type de Message dynamique
Dans la plupart des scénarios, vous devez spécifier le schéma d’en-tête SWIFT par défaut (Microsoft.Solutions.FinancialServices.SWIFT.RuntimeSchemas.HeaderSchema) pour la propriété de configuration de schéma d’en-tête SWIFT désassembleur SWIFT de. Le désassembleur SWIFT utilise le schéma d’en-tête SWIFT par défaut pour analyser les en-têtes de message qui se conforment à la spécification standard SWIFT et a nécessaires promu des propriétés pour faciliter la résolution de schéma dynamique (et la résolution de sous-type de « type double » Messages SWIFT tels que MT574_IRSLST et MT574_W8BENO). Pour plus d’informations sur le schéma d’en-tête SWIFT par défaut et pour comprendre comment le désassembleur SWIFT effectue la résolution de schéma, consultez [dynamique découverte de Type de Message et la résolution de schéma](../../adapters-and-accelerators/accelerator-swift/dynamic-message-type-discovery-and-schema-resolution.md).  
  
 Pour d’autres scénarios où les messages contiennent les données d’en-tête standard de non-SWIFT, vous pouvez utiliser un schéma d’en-tête personnalisé pour l’analyse des en-têtes et la découverte de type de message dynamique. Pour créer et utiliser un schéma d’en-tête personnalisé pour la résolution de schéma dynamique, procédez comme suit :  
  
1.  Créer un schéma personnalisé qui permet le désassembleur SWIFT structurellement analyser le format de données d’en-tête attendue.  
  
2.  Identifiez les champs dans le schéma contiendront les valeurs indiquant le type de message.  
  
3.  Ajoutez le schéma de propriété A4SWIFT (Microsoft.Solutions.A4SWIFT.Property.PropertySchema) à la « liste de schémas de propriété » du schéma d’en-tête personnalisé et promouvoir les champs appropriés qui indiquent le type de message à l’aide de ce qui suit [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] propriétés :  
  
    -   **A4SWIFT_MessageType**  
  
    -   **A4SWIFT_MessageType2** (facultatif si **A4SWIFT_MessageTypes** est utilisé)  
  
    -   **A4SWIFT_SecondaryMessageType** (facultatif)  
  
4.  Générez et déployez le schéma d’en-tête personnalisé.  
  
5.  La propriété de configuration de schéma d’en-tête SWIFT désassembleur SWIFT (dans votre projet de pipeline de réception) de la valeur du schéma d’en-tête personnalisé.  
  
 Pour plus d’informations sur ces autres propriétés promues et, consultez [propriétés promues A4SWIFT_ *](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md). Pour plus d’informations sur l’utilisation de l’Éditeur BizTalk pour créer et modifier des schémas, promouvoir des propriétés à l’aide d’un schéma de propriété, générer et déployer des projets de schéma, consultez [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de SWIFT désassembleur et assembleur](../../adapters-and-accelerators/accelerator-swift/working-with-the-swift-disassembler-and-assembler.md)