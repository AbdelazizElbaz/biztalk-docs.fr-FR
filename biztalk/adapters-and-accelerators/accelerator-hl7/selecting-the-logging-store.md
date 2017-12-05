---
title: "Sélection de la banque de journalisation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0518b536db16d641b77a61cfeb4851990a7bca0a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="selecting-the-logging-store"></a>Sélection de la banque de journalisation
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] vous offre l’option pour sélectionner une combinaison de journalisation de différents magasins, tel que [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], et [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements.  
  
 Vous utilisez la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration pour configurer le magasin de journalisation.  
  
 Utilisez les procédures suivantes pour ouvrir [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorateur de Configuration et sélectionnez le magasin de journalisation.  
  
### <a name="to-open-btahl7-configuration-explorer"></a>Pour ouvrir l’Explorateur de Configuration de BTAHL7  
  
-   Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis cliquez sur  **BTAHL7 L’Explorateur de Configuration**.  
  
### <a name="to-select-the--logging-store"></a>Pour sélectionner la banque de journalisation  
  
1.  Dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration, dans le **paramètres globaux** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**WMI**|Sélectionnez cette option si vous souhaitez générer des notifications de WMI pour BTAHL7.|  
    |**SQL**|Sélectionnez cette option si vous souhaitez utiliser [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] comme magasin de journalisation. **Remarque :** BTAHL7 crée automatiquement les tables requises pour la journalisation s’ils n’existent pas.|  
    |**SQL Server**|Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom. Cela est nécessaire lorsque vous sélectionnez le **SQL** option. La longueur maximale autorisée est de 64 caractères.<br /><br /> Le nom de serveur et de base de données par défaut est la base de données BTAHL7 configurée.|  
    |**Nom de la base de données**|Type de le [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] nom de la base de données. Cela est nécessaire lorsque vous sélectionnez le **SQL** option. La longueur maximale autorisée est de 128 caractères.|  
    |**Journal des événements**|Sélectionnez cette option si vous souhaitez utiliser le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] journal des événements en tant que votre banque de journalisation. Vous utilisez la [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Observateur d’événements pour afficher les messages d’événement.|  
  
2.  Cliquez sur **Enregistrer**.  
  
    > [!NOTE]
    >  Les paramètres régionaux des événements consignés par l’intermédiaire d’événements de journalisation varient selon les paramètres régionaux du compte de Service de journalisation.  
  
    > [!NOTE]
    >  Lorsque vous modifiez le mot de passe de compte de Service de journalisation, vous devez tout d’abord modifier le mot de passe [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsAD](../../includes/btsad-md.md)] service d’annuaire et redémarrez la journalisation du Service après avoir modifié le mot de passe du Service de journalisation sur chaque serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement par lots du message](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [Configuration de la journalisation](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)