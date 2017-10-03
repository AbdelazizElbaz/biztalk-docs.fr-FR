---
title: "Configuration d’A4SWIFT utilisateurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, user accounts
- creating, user accounts
- user accounts, creating
ms.assetid: 45dcbece-ec8d-410a-8320-79bfbc4c779d
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79c3b63cd77bb34545f4c4093796310aa7720563
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a4swift-users"></a>Configuration d’A4SWIFT utilisateurs
Lors de l’installation de [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], le programme de configuration d’A4SWIFT crée des profils de partenaire commercial par défaut et des accords et inscrit le serveur BizTalk. A4SWIFT crée également des bibliothèques de documents utilisées par le composant de Message Repair et New Submission.  
  
 A4SWIFT crée les dossiers de document suivants lors de l’installation :  
  
-   Bibliothèque de documents boîte d’envoi  
  
-   Bibliothèque de documents modèles  
  
-   Bibliothèque de documents non analysée  
  
-   Nouvelle bibliothèque de documents SWIFT MT Message  
  
-   Nouvelle bibliothèque de documents Messages de MX SWIFT  
  
 Pour chaque service créé, l’administrateur A4SWIFT doivent configurer manuellement les groupes de sites pour les services correspondants et rôles définis par l’A4SWIFT. Chaque département/rôle dispose d’une boîte de réception créé automatiquement par le Client(PWC) Web de profil.  
  
 Une fois le programme de configuration d’A4SWIFT le programme d’installation est terminé, l’administrateur de A4SWIFT configure les flux de travail pour chaque service de l’organisation. Lors de la configuration de Message Repair et New Submission, via le Client Web du profil, les boîtes de réception correspondants sont créés pour chaque combinaison de département/rôle. Par exemple, lors de la configuration de PWC A4SWIFT administrateur crée un service nommé paiements et attribue ensuite les rôles des créateurs, réparateurs et les approbateurs à un service appelé paiements. Bibliothèques de documents sur le site MRSR sont créés avec les noms de la boîte de réception, comme indiqué dans les exemples dans le tableau suivant :  
  
|Nom du service|Nom du rôle|Nom de la boîte de réception|  
|---------------------|---------------|----------------|  
|Paiements|Créateurs|Payments_Creator|  
|Paiements|Réparateurs|Payments_Repairers|  
|Paiements|Approbateurs|Payments_Approvers|