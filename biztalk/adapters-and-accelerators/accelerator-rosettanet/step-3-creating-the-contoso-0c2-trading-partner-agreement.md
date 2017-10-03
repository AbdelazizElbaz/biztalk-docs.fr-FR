---
title: "Étape 3 : Création de l’accord de partenariat commercial 2 Contoso 0C | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agreements, creating
- creating, agreements
- double action tutorial, creating agreements
ms.assetid: b4267faa-5f10-4294-9890-169f1d5ad8f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85ff2722deb6ab8ba38bda34b6c68b62cb7dbccb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-creating-the-contoso-0c2-trading-partner-agreement"></a>Étape 3 : Création de l’accord de partenariat commercial 2 0C de Contoso
Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion. Vous créez un accord de partenariat commercial pour le C 0 2 processus PIP (Partner Interface).  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-the-0c2-trading-partner-agreement"></a>Pour créer le 0C accord de partenariat commercial de 2  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, cliquez sur **nouveau**, puis cliquez sur **accord**.  
  
2.  Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam_To_Contoso_0C2**.|  
    |**Configuration de processus**|Sélectionnez **STD_0C2_R01.02** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **Contoso** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **Fabrikam** dans la liste déroulante.|  
    |**Version de RNIF**|Sélectionnez **V02.00.01** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **Répondeur (récepteur)** dans la liste déroulante.|  
    |**Utilisation**|Sélectionnez **Test** dans la liste déroulante.|  
  
3.  Cliquez sur l'onglet **Ports** , puis procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
    |**URL de signal**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
    |**URL de synchronisation**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez sur le **Fabrikam_To_Contoso_0C2** accord, puis cliquez sur **activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Création de l’accord de partenariat commercial 4 Contoso 0C](../../adapters-and-accelerators/accelerator-rosettanet/step-4-creating-the-contoso-0c4-trading-partner-agreement.md)