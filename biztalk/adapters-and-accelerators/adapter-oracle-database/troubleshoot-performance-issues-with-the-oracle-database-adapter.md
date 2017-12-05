---
title: "Résoudre les problèmes de performances de l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance issues, troubleshooting
- troubleshooting, performance issues
ms.assetid: 2035cd2e-ce87-419b-aada-61d257671623
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba487bcd5d6d245c979dec903613465ae54f8d9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="troubleshoot-performance-issues-with-the-oracle-database-adapter"></a>Résoudre les problèmes de performances de l’adaptateur de base de données Oracle
Cette section présente l’utilisation de techniques de dépannage pour résoudre les problèmes de performances que vous pouvez rencontrer lorsque vous utilisez [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)].  
  
## <a name="known-issue"></a>Problème connu  
 Voici le problème de performances courants que vous pouvez rencontrer en utilisant le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], ainsi que sa cause probable et de la résolution.  
  
##  <a name="BKMK_Slowdown"></a>Ralentissement ou blocage dans le débit lors de l’utilisation de l’adaptateur avec BizTalk Server  
 **Problème**  
  
 Lorsque vous utilisez la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le nombre de messages envoyés ou reçus par l’adaptateur de ralentissement ou est fourni à un blocage.  
  
 **Cause**  
  
 Le **EnableBizTalkCompatibilityMode** propriété de liaison n’est pas définie sur WCF-Custom d’envoi ou port de réception dans la console Administration de BizTalk Server.  
  
 **Résolution**  
  
 Définir le **EnableBizTalkCompatibilityMode** liaison de propriété à True. Pour plus d’informations sur cette propriété, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md). Pour obtenir des instructions sur la façon de définir une propriété de liaison, consultez [configurer les propriétés de liaison pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-binding-properties-for-oracle-database.md).  
  
### <a name="possible-memory-leak-on-a-64-bit-computer-when-using-the-oracle-database-adapter-to-perform-operations-involving-float-data-type"></a>Fuite de mémoire possible sur un ordinateur 64 bits lors de l’utilisation de l’adaptateur de base de données Oracle pour effectuer des opérations impliquant le type de données FLOAT  
 **Problème**  
  
 Vous pouvez rencontrer une fuite de mémoire lorsque vous utilisez le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] sur un ordinateur 64 bits pour effectuer des opérations qui impliquent des types de données FLOAT.  
  
 **Résolution**  
  
 Installez .NET \< *version* \> (x64) sur l’ordinateur 64 bits.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre les problèmes d’Oracle adapter.md de base de données](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)