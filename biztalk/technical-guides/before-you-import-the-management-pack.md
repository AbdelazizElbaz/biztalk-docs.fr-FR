---
title: "Avant d’importer le Pack d’administration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e3c13dd-613a-4885-a5d2-ad3ee492ff25
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c11849c379a4654bed78a8e86ba263e6da428c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="before-you-import-the-management-pack"></a>Avant d’importer le Pack d’administration
Comme meilleure pratique, vous devez importer le Pack d’administration de Windows Server pour le système d’exploitation que vous utilisez. Avant d’importer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Pack d’administration, effectuez les actions suivantes :  
  
-   Assurez-vous qu’Operations Manager 2007 R2/2012 est installé.  
  
-   Vous devez être membre du groupe Administrateurs de SCOM ou sur le groupe auteurs de SCOM. Les administrateurs locaux sur le serveur d’administration SCOM ont tous les droits et les autorisations sont accordées au groupe Administrateurs de SCOM.  
  
-   Configurer vos serveurs BizTalk Server en tant qu’ordinateurs gérés dans Operations Manager en déployant des agents SCOM sur chaque serveur BizTalk Server que vous souhaitez gérer. Le déploiement de l’agent SCOM implique les tâches suivantes :  
  
    -   Installez l’agent SCOM.  
  
    -   Créer un compte d’agent BizTalk SCOM.  
  
    -   Configurer un **exécuter en tant que** compte. Ajoutez le compte d’identification aux groupes suivants :  
  
        -   Groupes BizTalk.  
  
        -   Administrateurs de BizTalk.  
  
        -   Administrateurs de l’authentification unique.  
  
        -   Administrateurs d’applications associées SSO.  
  
    -   Lancement de l’analyse.  
  
-   Dans la Console Operations Manager, les ordinateurs gérés sont dans un état sain.  
  
-   Configurer des comptes d’utilisateur qui doivent être définies, comme les comptes d’identification requises ou des profils. Ce pack d’administration inclut les profils d’identification nommées « Compte d’analyse de BizTalk Server » et « Compte de découverte de BizTalk Server » pour définir les informations d’identification spécifiques sur une base par l’agent. Vous devrez peut-être utiliser ce profil exécuter en tant que certains agents après avoir importé le Pack d’administration.  
  
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Fichiers dans ce pack d’administration](../technical-guides/files-in-this-management-pack.md)  
  
-   [Packs d’administration supplémentaires recommandés](../technical-guides/recommended-additional-management-packs.md)