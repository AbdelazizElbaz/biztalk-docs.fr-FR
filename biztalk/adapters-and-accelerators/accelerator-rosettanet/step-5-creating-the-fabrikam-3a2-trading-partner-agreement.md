---
title: 'Étape 5 : Création de la négociation de Fabrikam 3A2 accord de partenariat | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: a5fafdc6-e9dd-4d15-98a2-8b603901308c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c0c2de5e4d44ce591eaca1b1e46130132436bf6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-5-creating-the-fabrikam-3a2-trading-partner-agreement"></a>Étape 5 : Création de l’accord de partenariat commercial Fabrikam 3A2
Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion. Vous créez un accord de partenariat commercial pour le 3A2 processus PIP (Partner Interface).  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-the-3a2-trading-partner-agreement"></a>Pour créer l’accord de partenariat commercial 3A2  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .  
  
2.  Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam_To_Contoso_3A2**.|  
    |**Configuration de processus**|Sélectionnez **STD_3A2_R02.00.00A** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **Fabrikam** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **Contoso** dans la liste déroulante.|  
    |**Version de RNIF**|Sélectionnez **V02.00.01** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **client (initiateur)** dans la liste déroulante.|  
    |**Utilisation**|Sélectionnez **Test** dans la liste déroulante.|  
  
3.  Cliquez sur l'onglet **Ports** , puis procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de signal**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de synchronisation**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez sur le **Fabrikam_To_Contoso_3A2** accord, puis cliquez sur **activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 6 : Création de l’accord de partenariat commercial Fabrikam 3A4](../../adapters-and-accelerators/accelerator-rosettanet/step-6-creating-the-fabrikam-3a4-trading-partner-agreement.md)