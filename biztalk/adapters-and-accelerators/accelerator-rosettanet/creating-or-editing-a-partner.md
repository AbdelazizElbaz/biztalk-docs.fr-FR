---
title: "Création ou modification d’un partenaire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, trading partners
- trading partners
- modifying, trading partners
- trading partners, creating
- trading partners, modifying
- trading partners, about trading partners
ms.assetid: 63809035-65a5-472d-b2e5-359c8e9d9d8c
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6e42ba4711dafa3c27b0b19dbcfc83fe280d1f5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-or-editing-a-partner"></a>Création ou modification d’un partenaire
Cette rubrique décrit comment créer ou modifier un partenaire. La configuration du partenaire décrit classifie le partenaire, définit la non répudiation de la période d’origine, configure des certificats pour le partenaire et fournit des informations de contact.  
  
 Lorsque vous créez un partenaire, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] crée deux ports d’envoi à utiliser par ce partenaire, un asynchrone et l’autre synchrone. Ces ports sont nommés d’envoi \< *nom du partenaire*>. Port d’envoi asynchrone et \< *nom du partenaire*>. Port d’envoi de synchronisation. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]inscrit et démarre automatiquement ces en fonction de l’accord de partenariat de ports d’envoi. Vous pouvez afficher ces ports dans la Console Administration de BizTalk.  
  
 Les paramètres de partenaire sont comme indiqué dans le tableau suivant, organisé par onglet. Pour obtenir des instructions sur la façon de créer et modifier un partenaire, consultez les procédures après le tableau.  
  
|Onglet|Paramètre|Utilisation|  
|---------|-------------|-----------|  
|**Général**|**Nom**|Le nom pour le partenaire commercial.<br /><br /> Ce champ est obligatoire.<br /><br /> Longueur maximale : 255|  
|**Général**|**GBI**|Identificateur d’entreprise Global pour le partenaire. Cela doit être de neuf chiffres et doit correspondre au numéro DUNS.<br /><br /> Ce champ est obligatoire.|  
|**Général**|**Description**|Une description qui identifie le partenaire.|  
|**Général**|**Maintenez la touche jusqu'à ce que**|La date à laquelle [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] envoie un message à la table MessagesFromLOB. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]ne renverra pas ce message jusqu'à ce que le **contenir jusqu'à** date. Les partenaires doivent s’accorder sur cette date, selon un lorsque le partenaire destinataire sera prêt à recevoir le message. Ce paramètre peut être utile si un partenaire ne sera pas disponible pour traiter les messages, par exemple, pendant un jour férié.<br /><br /> La valeur par défaut est la date actuelle.|  
|**Général**|**Classification du partenaire**|Le type de l’organisation partenaire.<br /><br /> Peut être **support** (la valeur par défaut), **distributeur**, **utilisateur final**, **utilisateur final gouvernement**, **Financier**, **Fabricant**, **détaillant**, ou **client**.<br /><br /> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]inclut la valeur de ce champ dans l’en-tête de Service.<br /><br /> Vous pouvez entrer une autre valeur pour la classification du partenaire dans l’en-tête de service d’un message, la substitution de cette propriété, en entrant une propriété personnalisée PPCC dans l’onglet de propriétés personnalisées de l’accord. Pour plus d’informations, consultez [création ou modification d’un accord](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).|  
|**Général**|**Non répudiation d’origine**|Le nombre de jours [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] contiendra le format de transmission d’un message dans la base de données de la table MessageStorageIn ou MessageStorageOut de non-répudiation (prouver légalement qu’il l’a reçue). [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]Cette date marque sur chaque message entrant ou sortant.<br /><br /> La valeur par défaut est jours 2485.<br /><br /> Toutefois, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ne supprimera pas un message à partir de la base de données lors de l’expiration de cette période. Si vous souhaitez supprimer ces messages, développer un script SQL pour supprimer les anciens messages selon ce cachet de date/heure.|  
|**Général**<br /><br /> (**Certificats de clé publique** zone)|**Signature**|La clé publique du certificat qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utiliseront pour vérifier la signature du partenaire d’un message entrant. Ce certificat doit être stocké dans le magasin de certificats autres personnes dans le nœud certificats (ordinateur Local) dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.<br /><br /> La valeur par défaut est \<none >.|  
|**Général**<br /><br /> (**Certificats de clé publique** zone)|**Chiffrement**|Le chiffrement à clé publique du certificat qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] utilise pour chiffrer les messages sortants à un partenaire. Ce certificat doit être stocké dans le magasin de certificats autres personnes dans le nœud certificats (ordinateur Local) dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.<br /><br /> La valeur par défaut est \<none >.|  
|**Propriétés de contact**|**Nom du contact**|Le nom du contact du partenaire.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Adresse de messagerie**|L’adresse de messagerie du contact du partenaire.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Numéro de téléphone**|Le numéro de téléphone du contact du partenaire.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Numéro de télécopie**|Le numéro de télécopie du contact du partenaire.<br /><br /> Ce champ est obligatoire.|  
|**Propriétés de contact**|**Code de la chaîne logistique**|Le code de chaîne d’approvisionnement pour le partenaire. Par exemple, « Informatique » ou « Electronic Components ».<br /><br /> Ce champ est obligatoire.|  
  
### <a name="to-create-a-partner"></a>Pour créer un partenaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)].  
  
3.  Avec le bouton droit **partenaires**, pointez sur **nouveau**, puis cliquez sur **partenaire**.  
  
4.  Dans le **nouvelles propriétés de partenaire** boîte de dialogue le **général** et **propriétés Contact** onglets, les valeurs de type pour les paramètres. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-edit-a-partner"></a>Pour modifier un partenaire  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.  
  
2.  Dans la Console de gestion BTARN, développez [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur **partenaires**.  
  
3.  Cliquez sur le partenaire que vous souhaitez modifier, puis cliquez sur **propriétés**.  
  
4.  Dans le  **\<**  *partenaire*  **>**  boîte de dialogue des propriétés du **général** et  **Propriétés de contact** onglets, modifier les paramètres en fonction des besoins. Pour plus d'informations sur ces paramètres, consultez le tableau précédent.  
  
5.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer la configuration, les certificats, les bases de données et la sécurité](manage-configuration-certificates-databases-security.md)   
 [Administration de la Configuration de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/administering-the-btarn-configuration.md)