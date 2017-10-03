---
title: "La gestion des ordinateurs hôtes et les comptes de Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, managing
- managing [user accounts]
- service accounts, security
- managing [hosts], security
- security, hosts
- managing [Windows groups]
- hosts, security
- security, service accounts
- Windows groups, managing
- user accounts, managing
ms.assetid: 25797571-f1f9-42a4-8fff-5b03076bbe36
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0099e683fba7c5f4e2400ad2f9ce005928b0a2aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-hosts-and-service-accounts"></a>Gestion des hôtes et des comptes de service
Après avoir configuré BizTalk Server, vous devez gérer les groupes et les comptes d'utilisateur Windows. Cette section fournit des informations sur la gestion de ces comptes pour BizTalk Server.  
  
> [!NOTE]
>  Pour une installation multiserveur de BizTalk Server, vous devez utiliser un groupe global de domaine. Pour une installation monoserveur de BizTalk Server, vous pouvez utiliser soit un groupe global de domaine soit un groupe local.  
  
 Vous devez être un administrateur Windows pour effectuer les tâches suivantes :  
  
-   créer un groupe d'hôtes Windows ;  
  
-   créer des comptes de service pour chaque instance d'hôte ;  
  
-   ajouter les comptes de service au groupe d'hôtes Windows ;  
  
-   modifier le groupe Windows associé à l'hôte.  
  
 Pour une liste complète et une description des groupes et leurs comptes d’utilisateur associés dans BizTalk Server, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
 Pour plus d’informations des droits de l’utilisateur de sécurité minimales pour les tâches administratives, consultez [autorisations de sécurité minimales](../core/minimum-security-user-rights.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Service de créer des comptes pour les nouveaux ordinateurs hôtes et les Instances d’hôte](../core/how-to-create-service-accounts-for-new-hosts-and-host-instances.md)  
  
-   [Comment modifier les comptes de Service et les mots de passe](../core/how-to-change-service-accounts-and-passwords.md)