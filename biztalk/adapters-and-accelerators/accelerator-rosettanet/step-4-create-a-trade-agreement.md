---
title: "Étape 4 : Créer un accord commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trade agreeements
- loopback tutorial, creating trade agreements
- agreements, creating
ms.assetid: 9bcb80b1-fefc-4f1c-ae03-fb736cdfd524
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b94acad2b71694223b0566f86edfcfa86610099
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-trade-agreement"></a>Étape 4 : Créer un accord commercial
Dans cette étape, vous créez un accord commercial entre le domicile et organisation du partenaire à l’aide du [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion.  
  
### <a name="to-create-a-trade-agreement"></a>Pour créer un accord commercial  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez **BizTalk \<version > Accelerator for RosettaNet**, avec le bouton droit **accords**, cliquez sur  **Nouvelle**, puis cliquez sur **accord**.  
  
2.  Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **échanges accord**.|  
    |**Configuration de processus**|Sélectionnez **STD_0C1_R01.02** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **accueil** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **partenaire** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **initiateur** dans la liste déroulante.|  
  
3.  Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **Ports** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **http://localhost/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de signal**|Type **http://localhost/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de synchronisation**|Laissez vide. URL de synchronisation n’est pas nécessaire pour le synchrone processus PIP (Partner Interface).|  
  
4.  Cliquez sur **appliquer**, puis cliquez sur **OK**.  
  
 Après avoir créé l’accord commercial, vous devez l’activer.  
  
### <a name="to-activate-the-trade-agreement"></a>Pour activer l’accord commercial  
  
-   Dans le [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], cliquez sur **accords**, avec le bouton droit **accord commercial** dans le volet de résultats, puis cliquez sur **activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 5 : Créer un accord de mise en miroir](../../adapters-and-accelerators/accelerator-rosettanet/step-5-create-a-mirror-agreement.md)