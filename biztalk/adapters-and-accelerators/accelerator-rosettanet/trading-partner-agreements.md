---
title: Accords de partenariat commercial | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- trading partners, agreements
- agreements, trading partners
ms.assetid: 846466d2-db39-42ba-8be1-ecca83a55a02
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26c8ac38e9b3dd0c32b496f3f7750fa0dcd982a1
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="trading-partner-agreements"></a>Accords de partenariat commercial
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] traite l’échange de messages avec un partenaire à un accord de partenariat commercial (TPA). Le TPA définit les caractéristiques de traitement des messages et la validation entre les deux partenaires. Il définit comment les partenaires implémentent le pertinentes processus PIP (Partner Interface), qui spécifie le contenu du message pour toutes les implémentations d’un type de message spécifique. Le TPA définit également les caractéristiques de la manière dont les partenaires échangent des messages via Internet.  
  
## <a name="trading-partner-agreement-contents"></a>Contenu d’accord partenaire commercial  
 Chaque accord de partenariat commercial comprend les informations suivantes :  
  
-   Les identités des partenaires commerciaux  
  
-   Traite les public, tel que défini par la version de Framework RNIF (RosettaNet Implementation) : chaque TPA fait référence à un seul processus public pour lancer ou de répondre aux actions de PIP  
  
-   Le profil de configuration de processus, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implémentation du PIP  
  
-   Paramètres ASPX, y compris l’action, le signal et l’URL synchrones  
  
-   Protocoles de codage et de chiffrement  
  
-   Propriétés personnalisées  
  
 Pour créer un accord de partenariat commercial, vous devez utiliser le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion pour créer une configuration de processus. En général de la base cette configuration sur un PIP RosettaNet, mais vous pouvez également la baser sur un schéma personnalisé. Vous devez également utiliser la console pour créer une organisation d’origine et d’un partenaire. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne prend pas en charge l’échange de messages entre des parties inconnues. Après avoir créé la configuration et l’organisation, vous pouvez ensuite utiliser la Console de gestion pour créer un accord de partenariat.  
  
### <a name="process-configuration"></a>Configuration du processus  
 Ces paramètres déterminent comment [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] traite les messages contenu. Ils spécifient le PIP RosettaNet et indiquent comment [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] implémentera le PIP. Pour ce faire, ils fournissent des valeurs spécifiques pour les paramètres de comportement que le PIP Spécifie, par exemple, les valeurs de délai d’attente, puis réessayez. Par conséquent, deux ensembles de partenaires différents, ou le même jeu de partenaires, peut implémenter même PIP de deux manières différentes.  
  
 Ces paramètres spécifient également standard (RosettaNet ou CIDX) et les aspects généraux des rôles d’organisation et partenaire domestiques. Vous pouvez également créer une configuration de processus pour le contenu non RosettaNet. Pour ce faire, vous devez créer un schéma pour que le contenu et ensuite créer la configuration en fonction de ce schéma. Pour le contenu non RosettaNet, vous devez entrer des valeurs pour le Message standard, version Standard et les paramètres d’ID de liaison de charge utile les **général** onglet dans le **les paramètres de Configuration de processus** boîte de dialogue. Vous pouvez uniquement transport contenu non RosettaNet à l’aide de RNIF 2.0.  
  
 Pour plus d’informations sur la définition de ces propriétés, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).  
  
### <a name="home-organization"></a>Organisation d'origine  
 Ces paramètres définissent l’organisation d’origine qui exécutera les messages. Les paramètres incluent une Global Business identificateur GBI (), qui est le numéro DUNS est l’identificateur unique de l’entreprise, et les informations qui sont nécessaire pour certaines opérations de contact. Pour plus d’informations sur la définition de ces propriétés, consultez [création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md).  
  
### <a name="partner-organization"></a>Organisation partenaire  
 Ces paramètres définissent le partenaire qui recevra et répondre aux messages. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] valide que chaque message RNIF entrant provenance d’une partie valide disposant d’un accord avec l’organisation d’origine. Si ce n’est pas le cas, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne pourront pas s’authentifier et pas traiter le message. Pour plus d’informations sur la définition de ces propriétés, consultez [création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md).  
  
### <a name="agreements-trading-partner-agreement-variables"></a>Contrats (commercial partenaire accord Variables)  
 Le contrat spécifie tous les aspects de la relation de partenaire commercial. Il spécifie le code de l’affichage des paramètres de configuration de processus, tel que défini dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion. Il spécifie également la version RNIF, URL de port, les paramètres de protocole (encodage et chiffrement) et d’autres variables. Pour plus d’informations sur la définition de ces propriétés, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).  
  
 Pour plus d’informations sur la console de gestion, consultez [gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md). Vous pouvez également accéder en lecture seule par programmation à ces paramètres via les classes et interfaces dans le Namespace Microsoft.Solutions.BTARN.ConfigurationManager dans la référence du développeur.  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk Accelerator for RosettaNet ajoutée à BizTalk Server](../../adapters-and-accelerators/accelerator-rosettanet/what-biztalk-accelerator-for-rosettanet-adds-to-biztalk-server.md)   
 [Pipelines RNIF](../../adapters-and-accelerators/accelerator-rosettanet/rnif-pipelines.md)   
 [Comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)   
 [Création ou modification d’une organisation d’origine](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)   
 [Création ou modification d’un partenaire](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)   
 [Création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)