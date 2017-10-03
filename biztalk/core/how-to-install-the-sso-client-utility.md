---
title: "Comment installer l’utilitaire Client SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, client utility
- client utility [SSO]
- SSO, installing
ms.assetid: e14d257e-2fde-46af-b90c-5dbc0884536b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4eba4e0747c9566c5303e04602d957173cc56052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-the-sso-client-utility"></a>Comment installer l’utilitaire Client SSO
L'utilitaire client SSO autonome (utilitaire de ligne de commande basé sur l'interface client) permet aux utilisateurs finaux de configurer leurs mappages clients dans la base de données SSO. Vous pouvez installer l'utilitaire client à partir d'un fichier à extraction automatique (SSOClientInstall.exe) qui est installé avec la fonctionnalité d'administration de l'authentification unique. Les administrateurs peuvent également mettre à la disposition des utilisateurs finaux le package d'installation en plaçant une copie de ce dernier sur un partage réseau.  
  
 Pour installer l'utilitaire client SSO, vous devez exécuter l'un des systèmes d'exploitation suivants sur l'ordinateur client :  
  
-   [!INCLUDE[btsPlatformsComApis](../includes/btsplatformscomapis-md.md)]  
  
-   [!INCLUDE[btsDotNetFramework3.5](../includes/btsdotnetframework3-5-md.md)] ou [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] (nécessaire uniquement si vous utilisez l'utilitaire client SSO basé sur l'interface utilisateur ou pour exploiter le composant d'interopérabilité géré de l'authentification unique de l'entreprise).  
  
 Après l’installation de l’utilitaire Client SSO, vous pouvez le lancer à partir de la **Démarrer** en cliquant sur **programmes**, **Microsoft Enterprise Single Sign-On**, puis **Utilitaire Client SSO**.  
  
### <a name="to-install-the-sso-client-utility"></a>Pour installer l'utilitaire client SSO  
  
1.  Double-cliquez sur le package d'installation SSOClientInstall.  
  
    > [!NOTE]
    >  Demandez à votre administrateur SSO de vous indiquer l'emplacement de ce fichier dans votre société.  
  
     Le **WinZip Self-Extractor** programme s’affiche.  
  
2.  Sélectionnez le dossier dans lequel vous souhaitez décompresser les fichiers, puis cliquez sur **Unzip**.  
  
     Il est recommandé de décompresser les fichiers dans un dossier temporaire.  
  
     Le **entreprise authentification Client d’installation unique** programme s’affiche.  
  
3.  Sur **la Bienvenue dans l’entreprise l’authentification Client unique** , cliquez sur **suivant**.  
  
4.  Dans la page Contrat de licence, cliquez sur **J’accepte les termes de ce contrat de licence**, puis cliquez sur **suivant**.  
  
5.  Sur le **informations utilisateur** page, tapez votre nom d’utilisateur, le nom de l’organisation, puis cliquez sur **suivant**.  
  
6.  Sur le **démarrer l’Installation** , cliquez sur **installer**.  
  
7.  Sur le **fin de l’entreprise seule l’authentification Client Assistant** , cliquez sur **Terminer**.  
  
8.  Spécifiez le serveur SSO en procédant de l'une des manières suivantes :  
  
    -   Ouvrez le composant logiciel enfichable MMC du Administration ENTSSO. Le **sélectionner le serveur SSO** boîte de dialogue apparaît. Accédez au serveur SSO auquel vous voulez vous connecter lors de l'exécution des opérations d'administration. Pour spécifier le serveur SSO pour tous les utilisateurs sur l’ordinateur, sélectionnez **définir le serveur d’authentification unique pour tous les utilisateurs**.  
  
         ou  
  
    -   À l’invite de commandes, tapez `ssomanage –server` pour spécifier le serveur SSO souhaité. Vous pouvez également taper `ssomanage -serverall` pour spécifier le serveur SSO auquel tous les utilisateurs de cet ordinateur se connectera lors des opérations d’administration.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment installer le composant Administration de l’authentification unique](../core/how-to-install-the-sso-administration-component.md)   
 [Configuration de l’authentification unique](../core/configuring-sso.md)   
 [L’installation de l’authentification unique](../core/installing-sso.md)