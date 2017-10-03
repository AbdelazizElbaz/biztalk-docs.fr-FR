---
title: "Résoudre les problèmes de performances de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- troubleshooting, performance issues
- performance, troubleshooting
ms.assetid: fe413b15-f703-4148-99df-17b5be3c74c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6443dd8b96b19b3cf42f6444ba1ae6c16f2b4ee6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-performance-issues-with-the-siebel-adapter"></a>Résoudre les problèmes de performances de l’adaptateur Siebel
Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].  
  
## <a name="known-issues"></a>Problèmes connus  
  
###  <a name="slowdown-or-stall-in-throughput-when-using-the-adapter-with-biztalk-server"></a>Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server  
 **Problème**  
  
 Lorsque vous utilisez la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.  
  
 **Cause**  
  
 Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la console Administration de BizTalk Server.  
  
 **Résolution**  
  
 Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True. Pour plus d’informations sur cette propriété, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de Siebel](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md). Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-the-binding-properties-for-siebel.md).  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)