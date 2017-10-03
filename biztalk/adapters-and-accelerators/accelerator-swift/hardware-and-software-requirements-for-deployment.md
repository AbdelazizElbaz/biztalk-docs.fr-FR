---
title: "Configurations matérielle et logicielle requise pour le déploiement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, hardware requirements
- deploying, software requirements
ms.assetid: 1dd9c4bb-b724-4195-8496-eff95cd1548a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0888fed8c554857a577e254f26e33be104da24e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hardware-and-software-requirements-for-deployment"></a>Configurations matérielle et logicielle requise pour le déploiement
Le tableau suivant répertorie les recommandations matérielles et logicielles et la configuration requise pour chaque serveur dans l’architecture de déploiement prescrites. Pour plus d’informations sur la configuration logicielle requise, consultez [déploiement de vos serveurs](../../adapters-and-accelerators/accelerator-swift/deploying-your-servers.md).  
  
 Pour tous les types de serveur, choisissez l’espace sur le disque dur, la vitesse d’horloge de processeur et la quantité de mémoire vive (RAM) basé sur les spécifications techniques actuelle et prévues (comme décrit dans [étape 1 : installation de la plate-forme de Base de](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)).  
  
|Server|Recommandations matérielles|Configuration logicielle requise|  
|------------|------------------------------|---------------------------|  
|Contrôleurs de domaine|-1 carte réseau|-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2012 R2 ou 2012<br />-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)] Serveur<br />-Serveur de nom domaine (DNS)|  
|Serveurs Microsoft SQL Server|-2 cartes réseau<br />-Facultatif : Pour les disques réseau de zone de stockage (SAN), choisissez l’espace disque requis pour le débit moyen, débit de pointe et des heures de débit de pointe plus la taille de message moyenne. Le réseau SAN doit être partitionné en trois lecteurs : données, les journaux de transaction et quorum.|-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2012 R2 ou 2012<br />-   [!INCLUDE[SQLServer2008or2005](../../includes/sqlserver2008or2005-md.md)]|  
|Serveurs BizTalk de la messagerie|-2 cartes réseau|-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2012 R2 ou 2012<br />-   [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]|  
|Ou les serveurs frontaux HTTP BizTalk (site MRSR)|-2 cartes réseau|-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2012 R2 ou 2012<br />-Internet Information Services (IIS)<br />-Le service message Queuing avec routage activé<br />-   [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]|  
|Serveurs BizTalk pour les orchestrations|-1 carte réseau|-   [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]Windows Server 2012 R2 ou 2012<br />-   [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]<br />-   [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]|