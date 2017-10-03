---
title: Attribution des droits | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, assigning permissions
- security, user accounts
- document library, new messages
- document library, unparsed
- messages, document library
- privileges
- permissions
- unparsed document library
- security, permissions
ms.assetid: cee44240-aa00-4080-9e7f-728b2421102b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a980fde1a4aea5d2e741fa576e55e659c0835f9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assigning-rights"></a>Attribution des droits
Les autorisations suivantes doivent être accordées sur les bibliothèques de documents pour chaque groupe de sites créé dans la rubrique précédente :  
  
|Bibliothèque de documents|Groupes de sites|Autorisations de bibliothèque de documents personnalisés à appliquer|  
|----------------------|-----------------|--------------------------------------------------|  
|Bibliothèque de documents modèles|Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers|Afficher les éléments|  
|Non analysées (détails ci-dessous)|Payments_Repairers|Afficher, insérer, modifier et supprimer des éléments|  
|Nouveaux Messages de MT SWIFT (détails ci-dessous)|Payments_Creators|Afficher, insérer, modifier et supprimer des éléments|  
|Nouveaux Messages de MX SWIFT (détails ci-dessous)|Payments_Creators|Afficher, insérer, modifier et supprimer des éléments|  
|Payments_Repairers|Payments_Repairers|Afficher, insérer, modifier et supprimer des éléments|  
|Payments_Approvers|Payments_Approvers|Afficher, insérer, modifier et supprimer des éléments|  
|[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Outbox|Payments_Creators<br /><br /> Payments_Repairers<br /><br /> Payments_Approvers|Afficher, insérer, modifier et supprimer des éléments|  
  
## <a name="unparsed-document-library"></a>Bibliothèque de documents non analysée  
 Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] processus de réparation de Message traite les messages qui échouent à l’analyse d’une manière spéciale. Messages non analysées (les messages qui ne peut pas être convertis en XML) sont routées vers une bibliothèque de documents unique message non analysée. La bibliothèque de documents non analysée doit être limitée pour autoriser uniquement des personnes spécifiques, plutôt que des groupes entiers accéder au dossier. Cela garantit que le dossier non analysé est aussi sécurisé que possible.  
  
 Les utilisateurs qui disposent d’autorisations de réparer les messages non analysées ont besoin d’autorisations dans le rôle de réparation au moins un service défini dans la console de configuration MMC et vous devez également être inscrits dans le groupe NT [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe d’utilisateurs.  
  
## <a name="new-swift-mt-mx-messages-document-library"></a>Nouvelle MT SWIFT / bibliothèque de documents Messages de MX  
 Les bibliothèques de documents nouvelle SWIFT MT Messages et nouvelle SWIFT MX sont créés au moment du déploiement du site MRSR. Les bibliothèques de documents nouvelle SWIFT MT Messages et nouvelle SWIFT MX stockent de nouveaux modèles SWIFT XML ou des messages de « standard ». Vous pouvez utiliser ces messages pour créer nouveau SWIFT messages représentés au format XML d’InfoPath. Ces messages sont téléchargés dans les bibliothèques de documents de nouveaux Messages de MT SWIFT et nouveaux SWIFT MX Messages par l’utilisateur en cliquant sur le bouton Télécharger dans la bibliothèque de documents. Vous pouvez davantage distribuer les modèles de nouveau Message SWIFT pour restreindre l’accès à des utilisateurs donnés. Pour faire votre tout d’abord créer une nouvelle bibliothèque de documents, puis copiez les modèles XML requis pour la bibliothèque de documents.  
  
 Pour plus d’informations sur l’outil FormPublish, consultez [FormPublish outil](http://msdn.microsoft.com/en-us/09a6ed31-5917-4776-9a5e-955af440cdac) dans la section Outils.