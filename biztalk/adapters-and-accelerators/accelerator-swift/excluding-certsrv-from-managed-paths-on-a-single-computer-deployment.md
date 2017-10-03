---
title: "À l’exclusion de CertSrv à partir des chemins d’accès sur un déploiement sur un seul ordinateur gérés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed paths
- certificate server (CertSrv)
- certificates, certificate server (CertSrv)
ms.assetid: 39916663-b80e-49d8-ba9b-49276eb564fc
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c77fc1733859cd903bafcebc26162323feff82d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="excluding-certsrv-from-managed-paths-on-a-single-computer-deployment"></a>À l’exclusion de CertSrv à partir de chemins d’accès gérés sur un déploiement sur un seul ordinateur
Si vous avez déployé [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] sur un seul ordinateur et également installé le serveur de certificats sur le même ordinateur, vous devez exclure le serveur de certificats (CertSrv) les chemins d’accès gérés dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Administration centrale de SharePoint Server.  
  
### <a name="to-exclude-certsrv-from-the-managed-paths"></a>Pour exclure les chemins d’accès gérés de CertSrv  
  
1.  cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Administration centrale de SharePoint**.  
  
2.  Dans la fenêtre Administration centrale, dans le **Configuration du serveur virtuel** , cliquez sur **configurer les paramètres du serveur virtuel**.  
  
3.  Dans la fenêtre liste des serveurs virtuels, cliquez sur **Site Web par défaut**.  
  
4.  Dans la fenêtre des paramètres du serveur virtuel, dans le **gestion du serveur virtuel** , cliquez sur **définir les chemins d’accès gérés**.  
  
5.  Dans la fenêtre Définir les chemins d’accès gérés, dans le **ajouter un nouveau chemin** section, entrez **CertSrv** dans les **chemin d’accès** zone de texte. Dans le **Type** , cliquez sur **chemin d’accès exclu**. Cliquez sur **OK**.  
  
6.  Fermez la fenêtre Définir les chemins d’accès gérés.