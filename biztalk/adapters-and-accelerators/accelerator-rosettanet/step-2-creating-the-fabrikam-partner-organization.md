---
title: "Étape 2 : Création de l’organisation partenaire Fabrikam | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- double action tutorial, creating partner organizations
- trading partners, partner organization
ms.assetid: 4d2ddc4c-2275-4faf-9a36-8a912cc06527
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3133f5e2ae7b3a234bef276af67afda391c1f7cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-creating-the-fabrikam-partner-organization"></a>Étape 2 : Création de l’organisation partenaire Fabrikam
Dans cette étape, vous utilisez la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Console de gestion pour créer un nouveau partenaire commercial. Le partenaire commercial pour ce didacticiel est de l’organisation de Fabrikam.  
  
### <a name="to-start-the-btarn-management-console"></a>Pour démarrer la console de gestion BTARN  
  
-   Sur l’ordinateur Contoso, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk \<version > Accelerator for RosettaNet**, puis Cliquez sur  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Console de gestion.  
  
### <a name="to-create-fabrikam-as-a-trading-partner"></a>Pour créer le partenaire commercial Fabrikam  
  
1.  Dans le  **[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]**  Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], avec le bouton droit **partenaires**, pointez sur **nouveau**, puis cliquez sur **partenaire**.  
  
2.  Dans la boîte de dialogue Propriétés du nouveau partenaire, sous l'onglet **Général** , procédez comme suit**:**  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom**|Tapez **FABRIKAM**.|  
    |**GBI**|Tapez **987654321**. **Remarque :** si vous avez exécuté le didacticiel de bouclage sur le même ordinateur, vous devez entrer une valeur pour GBI est différent de « 987654321 ».|  
    |**Classification du partenaire**|Sélectionnez **Acheteur** dans la liste déroulante.|  
    |**Certificat de signature**|Sélectionnez **Fabrikam Signature [Thumbprint]** dans la liste déroulante.|  
    |**Certificat de chiffrement**|Sélectionnez **Fabrikam chiffrement [Thumbprint]** dans la liste déroulante.|  
  
3.  Cliquez sur l'onglet **Propriétés du contact** , puis procédez comme suit :  
  
    |Propriété|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom du contact**|Tapez **Jane Doe**.|  
    |**E-mail Address**|Type  **jdoe@fabrikam.com** .|  
    |**Numéro de téléphone**|Tapez **555-555-5555**.|  
    |**Numéro de télécopie**|Tapez **555-555-5555**.|  
    |**Code de la chaîne logistique**|Tapez **Electronic Components**.|  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Création de l’accord de partenariat commercial 2 0C de Contoso](../../adapters-and-accelerators/accelerator-rosettanet/step-3-creating-the-contoso-0c2-trading-partner-agreement.md)