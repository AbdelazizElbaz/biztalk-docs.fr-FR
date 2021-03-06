---
title: 'Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: a99c2cd1-0d42-4fae-a380-a53d77cd87d0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb980ae879f06beaf468ba9b526ddc4ba83b5b06
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-creating-the-fabrikam-0c4-trading-partner-agreement"></a>Étape 4 : Création de l’accord de partenariat commercial 4 Fabrikam 0C
Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion. Vous allez créer un accord de partenariat commercial pour le processus PIP (Partner Interface Process) 0C4.  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-the-0c4-trading-partner-agreement"></a>Pour créer l'accord de partenariat commercial 0C4  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .  
  
2.  Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Tapez **Fabrikam_To_Contoso_0C4**.|  
    |**Configuration de processus**|Sélectionnez **STD_0C4_R01.02** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **Fabrikam** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **Contoso** dans la liste déroulante.|  
    |**Version de RNIF**|Sélectionnez **V02.00.01** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **initiateur (initiateur)** dans la liste déroulante.|  
    |**Utilisation**|Sélectionnez **Test** dans la liste déroulante.|  
  
3.  Cliquez sur l'onglet **Ports** , puis procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de signal**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de synchronisation**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez avec le bouton droit sur l'accord **Fabrikam_To_Contoso_0C4** , puis cliquez sur **Activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 5 : Création de l’accord de partenariat commercial Fabrikam 3A2](../../adapters-and-accelerators/accelerator-rosettanet/step-5-creating-the-fabrikam-3a2-trading-partner-agreement.md)