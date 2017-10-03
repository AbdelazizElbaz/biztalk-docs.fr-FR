---
title: "Résoudre les problèmes avec le fournisseur de données pour Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Provider for Siebel, troubleshooting
- troubleshooting, Data Provider for Siebel
ms.assetid: 2bfe69a2-d6de-466d-9f36-f11c386c771c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6e100635b1cb2db5c78ff713c8e6ad32d4e7d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshoot-issues-with-the-data-provider-for-siebel"></a>Résoudre les problèmes avec le fournisseur de données pour Siebel
Cette section présente l’utilisation de techniques de dépannage pour résoudre les erreurs que vous pouvez rencontrer lorsque vous utilisez la [!INCLUDE[adoprovidersiebellong](../../includes/adoprovidersiebellong-md.md)] ([!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]).  
  
## <a name="known-issues"></a>Problèmes connus  
  
### <a name="data-provider-for-siebel-may-give-component-datareader-source-380-error"></a>Fournisseur de données pour Siebel peut provoquer l’erreur de « composant « DataReader Source' (380) »  
 **Problème**  
  
 Lors de l’exécution d’une requête SELECT sur un composant d’entreprise Siebel, le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] peut provoquer une erreur « composant « DataReader Source' (380) ».  
  
 **Cause**  
  
 Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] génère cette erreur si la valeur reçue à partir du système Siebel pour un paramètre dépasse la propriété maxLength pour le paramètre.  
  
## <a name="see-also"></a>Voir aussi  
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)