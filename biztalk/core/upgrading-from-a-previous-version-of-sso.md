---
title: "La mise à niveau à partir d’une Version précédente de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading, SSO
- SSO, upgrading
ms.assetid: 78b99d99-9a10-4453-9db5-ae1bacd7de50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf36c33b9480c0e8658089fdc9d996b3701d7660
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="upgrading-from-a-previous-version-of-sso"></a>La mise à niveau à partir d’une Version précédente de l’authentification unique
Si vous installez la fonctionnalité Enterprise Single Sign-on et que vous disposez déjà d’une version précédente est déployée sur votre ordinateur (par exemple, à partir de Microsoft BizTalk Server 2009), vous devez effectuer les étapes ci-dessous.  
  
1.  Sauvegardez la base de données SSO dans un emplacement sécurisé.  
  
2.  Sauvegardez la clé de secret principal sur le serveur de secret principal.  
  
3.  Mettre à jour le serveur de secret principal en exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le programme d’installation en choisissant **Installation personnalisée**, puis en sélectionnant **Enterprise Single Sign-On**.  
  
4.  Après avoir sélectionné **activer Enterprise Single Sign-on sur cet ordinateur**, sélectionnez **joindre un système SSO existant**.  
  
 La mise à jour des autres serveurs SSO (serveurs de secret non principaux) de votre installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas nécessaire. Toutefois, si vous souhaitez que les nouvelles fonctionnalités d'authentification unique de l'entreprise soient disponibles sur ces serveurs, vous devez les mettre à jour en suivant la procédure précédente.  
  
> [!NOTE]
>  Ces considérations s’appliquent également si vous installez Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur un ordinateur avec une installation existante de Host Integration Server 2009 Enterprise Single Sign-On et que vous souhaitez mettre à jour les serveurs.  
  
 Si vous installez Host Integration Server sur un ordinateur sur lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est déjà installé, ne sélectionnez pas la fonctionnalité d'authentification unique de l'entreprise.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation de l’hôte initiée par les fonctionnalités de l’authentification unique](../core/using-host-initiated-sso-functionality.md)  
  
-   [Serveurs de traitement pour l’authentification unique](../core/processing-servers-for-sso.md)