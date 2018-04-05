---
title: Onglet Paramètres globaux | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.globalsettings
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- Global Settings tab [Configuration Explorer]
- auditing, configuring
ms.assetid: 057189f7-9072-4841-950f-371ba1f73a15
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022ad14cc93b55c7ad928c06358f2714531b40b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="global-settings-tab"></a>Onglet Paramètres généraux
Vous utilisez la **paramètres globaux** tab pour configurer le magasin de journalisation utilisé par [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].  
  
 Dans le **BTAHL7 Configuration Explorer** boîte de dialogue le **paramètres globaux** onglet, procédez comme suit :  
  
|Utiliser|Pour effectuer cette opération|  
|--------------|----------------|  
|**WMI**|Sélectionnez cette option si vous souhaitez générer [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] notifications Management Instrumentation (WMI) pour BTAHL7.|  
|**SQL**|Sélectionnez cette option si vous souhaitez utiliser [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] comme magasin de journalisation pour BTAHL7. **Remarque :** BTAHL7 crée automatiquement les tables requises pour la journalisation s’ils n’existent pas.|  
|**SQL Server**|Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom. Cela est nécessaire lorsque vous sélectionnez le **SQL** option. La longueur maximale autorisée est de 64 caractères.<br /><br /> Le nom de serveur et de base de données par défaut est la base de données BTAHL7 configurée.|  
|**Nom de la base de données**|Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom de la base de données. Cela est nécessaire lorsque vous sélectionnez le **SQL** option. La longueur maximale autorisée est de 128 caractères.|  
|**Journal des événements**|Sélectionnez cette option si vous souhaitez utiliser le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements en tant que la banque de journalisation pour BTAHL7. Vous utilisez la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour afficher les messages d’événement.|