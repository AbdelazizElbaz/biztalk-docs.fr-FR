---
title: 'Étape 6 : Création d’échanges de 3 a 4 Fabrikam accord de partenariat | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating agreements
ms.assetid: 6ccd2414-a1d4-460e-9529-65b2d30cfca6
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 802d3648d0f7709fdfbed70c3e29a4abc565a51c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-6-creating-the-fabrikam-3a4-trading-partner-agreement"></a>Étape 6 : Création de l’accord de partenariat commercial Fabrikam 3 a 4
Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion. Vous créez un accord de partenariat commercial pour les 3 a 4 processus PIP (Partner Interface).  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version\> Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-the-3a4-trading-partner-agreement"></a>Pour créer l’accord de partenariat commercial 3 a 4  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .  
  
2.  Dans le **nouvelles propriétés de l’accord** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam_To_Contoso_3A4**.|  
    |**Configuration de processus**|Sélectionnez **STD_3A4_V02.02** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **Fabrikam** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **Contoso** dans la liste déroulante.|  
    |**Version de RNIF**|Sélectionnez **V02.00.01** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **acheteur (initiateur)** dans la liste déroulante.|  
    |**Utilisation**|Sélectionnez **Test** dans la liste déroulante.|  
  
3.  Sur le **Ports** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de signal**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
    |**URL de synchronisation**|Type **https://<contoso_machine>/BTARNApp/RNIFReceive.aspx**.|  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez sur le **Fabrikam_To_Contoso_3A4** accord, puis cliquez sur **activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 7 : Création et déploiement de l’exemple du SDK LOBWebApplication](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-lobwebapplication-sdk-sample.md)