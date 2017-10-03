---
title: "À l’aide de la Console de gestion BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- agreements, activating
- activating agreements
- BTARN Management Console, Scope pane
- tracking
- creating, trading partners
- BTARN Management Console, agreements
- process configuration
- agreements, modifying
- BTARN Management Console, home organizations
- agreements, creating
- BTARN Management Console, trading partners
- agreements, deleting
- deleting, agreements
- BTARN Management Console
- agreements, listing
- modifying, trading partners
- creating, agreements
- trading partners, creating
- modifying, agreements
- BAM tracking
- Scope pane [BTARN Management Console]
- trading partners, modifying
- trading partners, deleting
- BTARN Management Console, process configurations
- deleting, trading partners
- BTARN Management Console, about BTARN Management Console
- home organizations
ms.assetid: 000ee93d-eb1d-4ff8-a9cf-0547beff027d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 39157aa2454690a77ffbb1a5c2492bc07404c602
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-btarn-management-console"></a>À l’aide de la Console de gestion BTARN
Cette rubrique décrit comment administrer [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] à partir de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.  
  
 Ouvrez le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion en cliquant sur **Démarrer**, en pointant sur **programmes**, en pointant sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis en cliquant sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
 Le volet d’étendue (gauche) de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion inclut toutes les [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] nœuds de configuration. Le volet de résultats (à droite) inclut toutes les instances spécifiques des éléments de configuration que vous avez sélectionné dans le volet d’étendue.  
  
## <a name="operations-in-the-scope-pane"></a>Opérations dans le volet d’étendue  
 Vous pouvez effectuer les opérations suivantes sur les nœuds dans le volet d’étendue :  
  
-   Définir le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoyer et recevoir des pipelines que vous souhaitez utiliser pour les ports d’envoi partenaire. Pour plus d’informations, consultez [paramètre BTARN d’envoi et les Pipelines de réception](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md).  
  
-   Activer le suivi de l’analyse BAM (Business Activity). Pour plus d’informations, consultez [l’activation de suivi BAM](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md).  
  
-   Assurez-vous que toutes les configurations qui vient d’être importées sont visibles dans la console en double-cliquant sur le nœud de configuration dans le volet d’étendue, puis en cliquant sur **Actualiser**.  
  
-   Afficher des colonnes supplémentaires dans le volet de résultats en cliquant sur le **les paramètres de Configuration de processus** ou **accord** nœud dans le volet d’étendue, en pointant sur **vue**, puis en cliquant sur **Ajout/Suppression de colonnes**. Déplacer des colonnes entre les colonnes disponibles et les colonnes affichées à l’aide de la **ajouter ou supprimer des** bouton. Cette commande est particulièrement utile pour les contrats qui ont beaucoup de colonnes disponibles que [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] n’affiche pas par défaut.  
  
## <a name="process-configurations"></a>Configurations de processus  
 Vous pouvez effectuer les opérations suivantes sur une configuration de processus :  
  
-   Ajouter une nouvelle configuration de processus en double-cliquant sur le **les paramètres de Configuration de processus** noeud d’étendue, en pointant sur **nouveau**, puis en cliquant sur **Configuration du processus**. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
-   Modifier une configuration de processus existante en double-cliquant sur la configuration de processus dans le volet de résultats, puis en cliquant **propriétés**, ou en double-cliquant sur la configuration de processus. Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
-   Supprimer une configuration de processus existante en double-cliquant sur la configuration de processus dans le volet de résultats, puis en cliquant **supprimer**.  
  
-   Créer une nouvelle configuration de processus basée sur une configuration de processus existante en cliquant sur la configuration dans le volet de résultats que vous souhaitez baser la nouvelle configuration sur, puis en cliquant **nouvelle Configuration du processus de copie**. Ceci affichera un nouveau **propriétés de Configuration de processus** boîte de dialogue renseignée avec les paramètres de la configuration existante. Entrez un nouveau **affiche un code**, puis cliquez sur **OK** pour créer la nouvelle configuration. Pour plus d’informations, consultez [à l’aide de la spécification PIP pour créer une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).  
  
-   Afficher une liste de tous les accords associé à une configuration de processus en double-cliquant sur la configuration spécifique dans le volet de résultats, puis en cliquant **afficher les contrats**. Il déplace le focus vers le **accords** nœud dans le volet d’étendue et d’afficher les contrats associés dans le volet de résultats. Vous pouvez revenir à une liste complète des accords en double-cliquant sur le **accords** nœud dans le volet d’étendue, puis en cliquant sur **afficher tout**.  
  
## <a name="home-organizations"></a>Organisations domestiques  
 Vous pouvez effectuer les opérations suivantes sur une organisation d’origine :  
  
-   Ajouter une nouvelle organisation d’origine en cliquant sur le **domestique organisations** noeud d’étendue, en pointant sur **nouveau**, puis en cliquant sur **organisation d’origine**. Pour plus d’informations, consultez [création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
-   Modifier une organisation d’origine existante en double-cliquant sur l’organisation d’origine dans le volet de résultats et puis en cliquant sur **propriétés**, ou en double-cliquant sur l’organisation d’origine. Pour plus d’informations, consultez [création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
-   Supprimer une organisation d’origine existante en double-cliquant sur l’organisation d’origine dans le volet de résultats et puis en cliquant sur **supprimer**.  
  
## <a name="partners"></a>Partenaires  
 Vous pouvez effectuer les opérations suivantes sur un partenaire :  
  
-   Ajouter un nouveau partenaire en double-cliquant sur le **partenaires** noeud d’étendue, en pointant sur **nouveau**, puis en cliquant sur **partenaire**. Pour plus d’informations, consultez [création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
-   Modifier un partenaire existant en double-cliquant sur le partenaire dans le volet de résultats et puis en cliquant sur **propriétés**, ou en double-cliquant sur le partenaire. Pour plus d’informations, consultez [création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
-   Supprimez un partenaire existant du partenaire dans le volet de résultats, puis en cliquant sur **supprimer**.  
  
## <a name="agreements"></a>Accords  
 Vous pouvez effectuer les opérations suivantes sur un accord :  
  
-   Ajoutez un nouveau contrat en cliquant sur le **accords** noeud d’étendue, en pointant sur **nouveau**, puis en cliquant sur **accord**. Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
-   Modifier un accord existant en double-cliquant sur l’accord, dans le volet de résultats et puis en cliquant sur **propriétés**, ou en double-cliquant sur l’accord. Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
-   Supprimer un accord existant en double-cliquant sur l’accord, dans le volet de résultats et puis en cliquant sur **supprimer**.  
  
-   Activation d’un accord en double-cliquant sur l’accord désactivé dans le volet de résultats et puis en cliquant sur **activer**. Cette opération activera les messages associés à l’accord pour être envoyé ou reçu. Vous pouvez également désactiver un accord afin d’éviter les messages associés à l’accord d’envoyé ou reçu.  
  
-   Revenir à une liste complète des accords, après l’affichage d’une liste des accords uniquement associé à une configuration de processus, en cliquant sur le **accords** nœud dans le volet d’étendue, puis en cliquant sur **afficher tout** .  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de BTARN envoi et de Pipelines de réception](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md)   
 [L’activation de suivi BAM](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)   
 [Comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)