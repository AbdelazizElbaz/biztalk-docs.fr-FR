---
title: "Résoudre les problèmes de performances de l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance
- performance, troubleshooting
ms.assetid: 7e8e9fec-0edf-4c67-837c-0e271b2ffe68
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef9e18a2f26af993da36a13d389f2aff2ad2f60a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-sap-adapter"></a>Résoudre les problèmes de performances de l’adaptateur SAP
Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)].  
  
##  <a name="BKMK_SAPSlowdown"></a>Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server  
 **Problème**  
  
 Lorsque vous utilisez la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.  
  
 **Cause**  
  
 Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la Console Administration de BizTalk Server.  
  
 **Résolution**  
  
 Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True. Pour plus d’informations sur cette propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
##  <a name="BKMK_SAPMemLeak"></a>Fuite de mémoire possible lors de l’utilisation de valeurs NULL pour les paramètres  
 **Problème**  
  
 Vous pouvez observer mémoire fuite si vous ne spécifiez pas les valeurs des paramètres d’entrée ou de table lors de l’appel des artefacts dans le système SAP.  
  
 **Résolution**  
  
 Assurez-vous que vous spécifiez des valeurs pour tous les paramètres d’entrée et de table lors de l’appel d’un artefact dans le système SAP.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)