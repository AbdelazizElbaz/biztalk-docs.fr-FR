---
title: "Création ou modification d’une organisation d’origine | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- home organizations, about home organizations
- home organizations, modifying
- creating, home organizations
- modifying, home organizations
- home organizations
- home organizations, creating
ms.assetid: b54afb84-2f16-4516-8701-b03301476362
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bc8a298686772d354c934d76fbcb7dbbb8146f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-or-editing-a-home-organization"></a>Création ou modification d’une organisation d’origine
Cette rubrique décrit comment créer ou modifier une organisation d’origine. La configuration de l’organisation d’origine décrit classifie l’organisation, définit la non répudiation de la période d’origine et fournit des informations de contact.  
  
 La configuration de l’organisation d’origine n’inclut pas de signature et de certificats de déchiffrement, comme la configuration du partenaire ne. Vous configurez le certificat de signature pour le groupe BizTalk dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration. Vous configurez le certificat de déchiffrement pour les hôtes BizTalk (BizTalkServerApplication et BizTalkServerIsolatedHost) dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Console d’Administration.  
  
 Vous pouvez créer deux organisations accueil dans une entreprise unique ou un déploiement. Un exemple de ce peut être une instance dans laquelle vous souhaitez créer la gestion de priorité des messages, dans lequel les messages destinés à une organisation est une priorité supérieure à celle de messages destinés à un autre. Lorsque vous créez plusieurs organisations d’origine, vous devez fournir chaque organisation d’origine avec un numéro DUNS séparé pour les identifier de façon unique. Le numéro DUNS est ce que définit la connexion RosettaNet.  
  
 Les paramètres dans la description de l’organisation d’origine sont comme indiqué dans le tableau suivant, organisé par onglet. Pour obtenir des instructions sur la façon de créer et modifier une organisation d’origine, reportez-vous aux procédures après le tableau.  
  
|Onglet|Paramètre|Utilisation|  
|---------|-------------|-----------|  
|**Général**|**Nom**|Le nom de l’organisation d’origine.<br /><br /> Ce champ est obligatoire.<br /><br /> Longueur maximale : 255|  
|**Général**|**GBI**|Identificateur d’entreprise Global pour l’organisation d’origine. Cela doit être de neuf chiffres et doit correspondre au numéro DUNS.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Description**|Une description qui vous aide à identifier l’organisation d’origine.|  
|**Général**|**Classification de l’organisation d’origine**|La nature de l’organisation.<br /><br /> Peut être **utilisateur final**, **utilisateur final gouvernement**, **Financier**, **fabricant**, **détaillant**,  **Client**, **redirecteur de transport**, ou **Marketplace**.<br /><br /> Vous pouvez entrer une autre valeur pour la classification de l’organisation d’origine dans l’en-tête de service d’un message, la substitution de cette propriété, en entrant une propriété personnalisée HPCC dans l’onglet de propriétés personnalisées de l’accord. Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).|  
|**Propriétés de contact**|**Nom du contact**|Le nom du contact de l’organisation d’origine.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Adresse de messagerie**|L’adresse de messagerie du contact de l’organisation d’origine.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Numéro de téléphone**|Le numéro de téléphone du contact de l’organisation d’origine.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Numéro de télécopie**|Le numéro de télécopie du contact de l’organisation d’origine.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Code de la chaîne logistique**|Le code de chaîne d’approvisionnement pour l’organisation d’origine.<br /><br /> Ce champ est obligatoire.|  
  
### <a name="to-create-a-home-organization-definition"></a>Pour créer une définition de l’organisation d’origine  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Avec le bouton droit **accueil organisations**, pointez sur **nouveau**, puis cliquez sur **organisation d’origine**.  
  
4.  Dans la boîte de dialogue Nouvelle accueil propriétés de l’organisation, sur le **général** et **propriétés Contact** onglets, entrez les valeurs de paramètres. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-edit-a-home-organization"></a>Pour modifier une organisation d’origine  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Cliquez sur **aux organisations d’accueil**.  
  
4.  Avec le bouton droit de l’organisation d’origine vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
5.  Dans le  *\<organisation d’accueil >* boîte de dialogue des propriétés du **général** et **propriétés Contact** onglets, modifier les paramètres en fonction des besoins. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
6.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)   
 [Administration de la Configuration de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)