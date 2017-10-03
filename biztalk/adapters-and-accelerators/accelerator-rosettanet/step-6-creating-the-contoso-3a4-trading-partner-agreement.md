---
title: "Étape 6 : Création d’échanges de 3 a 4 Contoso accord de partenariat | Documents Microsoft"
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
ms.assetid: a20e40d8-7e3b-4930-8921-056ffddd08ea
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e2a5513d9df725ca1f67cec728dffad552047f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-creating-the-contoso-3a4-trading-partner-agreement"></a>Étape 6 : Création de l’accord de partenariat commercial Contoso 3 a 4
Dans cette étape, vous créez un accord de partenariat commercial entre Contoso et Fabrikam à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion. Vous créez un accord de partenariat commercial pour les 3 a 4 processus PIP (Partner Interface).  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-the-3a4-trading-partner-agreement"></a>Pour créer l’accord de partenariat commercial 3 a 4  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord** .  
  
2.  Dans la boîte de dialogue Propriétés du nouvel accord, sous l'onglet **Général** , procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Type **Fabrikam_To_Contoso_3A4**.|  
    |**Configuration de processus**|Sélectionnez **STD_3A4_V02.02** dans la liste déroulante.|  
    |**Mon organisation**|Sélectionnez **Contoso** dans la liste déroulante.|  
    |**Organisation du partenaire**|Sélectionnez **Fabrikam** dans la liste déroulante.|  
    |**Version de RNIF**|Sélectionnez **V02.00.01** dans la liste déroulante.|  
    |**Rôle de base**|Sélectionnez **vendeur (récepteur)** dans la liste déroulante.|  
    |**Utilisation**|Sélectionnez **Test** à partir de la liste déroulante.|  
  
3.  Sur le **Ports** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL d’action**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
    |**URL de signal**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
    |**URL de synchronisation**|Type **https://<fabrikam_machine>/BTARNApp/RNIFReceive.aspx**|  
  
4.  Cliquez sur **OK**.  
  
5.  Cliquez sur le **Fabrikam_To_Contoso_3A4** accord, puis cliquez sur **activer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 7 : Création et déploiement de l’exemple du Kit de développement DoubleAction](../../adapters-and-accelerators/accelerator-rosettanet/step-7-building-and-deploying-the-doubleaction-sdk-sample.md)