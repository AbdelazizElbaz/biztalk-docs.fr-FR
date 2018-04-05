---
title: Paramètre des CIDX chem échange de messages | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- CIDX, configuring message exchange
ms.assetid: 90468459-cef7-436b-8c0b-3a7455a091c3
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c4606dfc4b912d884a997bb65acb26cb4352448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-cidx-estandards-message-exchange"></a>Paramètre des CIDX chem échange de messages
Cette rubrique décrit comment configurer l’échange de messages chem chimiques données Exchange (CHEMICAL). CIDX nécessite que vous définissez les trois propriétés suivantes :  
  
-   `Standard`propriété dans les paramètres de configuration de processus **CIDX**  
  
-   `Is Single Action`propriété dans les paramètres de configuration de processus`True`  
  
-   `0A1 agreement`propriété dans l’accord de partenariat commercial à **aucune 0 a 1**  
  
 Pour plus d’informations sur les différences entre CIDX et RosettaNet, consultez [prise en charge CIDX](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md).  
  
### <a name="to-set-up-cidx-message-exchange"></a>Pour configurer l’échange de messages CIDX  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Cliquez avec le bouton droit sur **Paramètres de configuration du processus**, pointez sur **Nouveau**, puis cliquez sur **Configuration du processus**.  
  
4.  Dans la boîte de dialogue nouvelles propriétés de Configuration de processus sur le **général** onglet, pour le **Standard** propriété, sélectionnez **CIDX**.  
  
5.  Sur le **activité** onglet, pour le **est la seule Action** propriété, sélectionnez **True**.  
  
6.  Entrez les autres paramètres de configuration de processus en fonction des besoins. Pour plus d’informations sur ces paramètres, consultez le tableau dans [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
7.  Cliquez sur **OK**.  
  
8.  Avec le bouton droit **accords**, pointez sur **nouveau**, puis cliquez sur **accord**.  
  
9. Sur le **général**, **Ports**, **protocole**, et **propriétés personnalisées** onglets, entrez les valeurs pour les différents paramètres. Pour plus d’informations sur ces paramètres, consultez le tableau dans [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
10. Dans la boîte de dialogue Propriétés de l’accord sur le **général** onglet, pour le **0 a 1 accord** propriété, sélectionnez **aucun 0 a 1**.  
  
11. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)   
 [Création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)