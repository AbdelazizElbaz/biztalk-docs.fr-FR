---
title: "Installer le composant d’Administration SSO | Documents Microsoft"
description: "Effectuer une installation personnalisée pour obtenir l’Administration de l’authentification unique et permet d’entrer le nom du serveur dans BizTalk Server ssomanage ou l’administration de l’authentification unique"
ms.custom: 
ms.date: 09/27/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 096839e2-7129-498d-92ee-5afeea8dbe0d
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab2bb01defe700408a551a144eae67d0405565f4
ms.sourcegitcommit: 5355a25d120d094778fb8f68ea14cab55c68d292
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2017
---
# <a name="how-to-install-the-sso-administration-component"></a>Comment installer le composant Administration de l’authentification unique

## <a name="overview"></a>Vue d'ensemble
Vous pouvez installer le composant Administration de l’authentification unique de l’entreprise comme une fonctionnalité autonome. Ceci est utile si vous devez gérer le système d'authentification unique à distance. Les conditions matérielles et logicielles sont les mêmes que pour une installation classique des services d'exécution de l'authentification unique de l'entreprise.  
  
 Après avoir installé le composant d’administration, vous entrez le serveur d’authentification unique à utiliser pour la gestion. Pour cela, l’outil de ligne de commande (ssomanage.exe), soit le composant logiciel enfichable MMC du Administration SSO. Les deux procédures sont répertoriées dans cette rubrique.  
  
 L'installation de l'utilitaire d'administration de l'authentification unique (ssomanage.exe) ne crée pas de raccourcis dans le menu Démarrer permettant d'accéder aux utilitaires de ligne de commande. Pour exécuter les utilitaires d’administration de l’authentification unique après l’installation, vous devez ouvrir une invite de commandes et accédez au répertoire de l’authentification unique à `Program Files\Common Files\Enterprise Single Sign-On`.  
  
 Le composant Administration de l’authentification unique d’entreprise inclut également un composant logiciel enfichable MMC. MMC 3.0 doit être installé sur votre ordinateur pour le composant logiciel enfichable de la fonction.  
  
 Pour ouvrir le composant logiciel enfichable MMC de l’authentification unique d’entreprise à partir de la **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez **Microsoft Enterprise Single Sign-On**, puis **SSO Administration**.  
  
## <a name="install-the-enterprise-single-sign-on-administrative-component"></a>Installer le composant d’administration Enterprise Single Sign-On  
  
-   Effectuez une installation personnalisée de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], puis sélectionnez uniquement la fonctionnalité d’Administration de l’authentification unique de l’entreprise. Pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], cette information est répertoriée sous **des logiciels supplémentaires**.  
  
## <a name="enter-the-server-using-the-mmc-snap-in"></a>Entrez le serveur à l’aide du composant logiciel enfichable MMC  
  
1.  Après l'installation du composant d'administration sur un ordinateur, ouvrez le composant logiciel enfichable Administration de l'authentification unique.  
  
     Dans le **Démarrer** menu, sélectionnez **tous les programmes**, sélectionnez **Microsoft Enterprise Single Sign-On**, puis sélectionnez **Administration SSO**.  
  
2.  Dans la console MMC enfichable sous le **racine de la Console**, avec le bouton droit **Enterprise Single Sign-On**, puis cliquez sur **sélectionnez**.  
  
     Le **sélectionner le serveur SSO** boîte de dialogue s’affiche.  
  
3.  Entrez le nom du serveur d'authentification unique souhaité ou accédez-y. Pour spécifier le serveur d’authentification unique pour tous les utilisateurs sur l’ordinateur, sélectionnez **définir le serveur d’authentification unique pour tous les utilisateurs**.  
  
4.  Cliquez sur **OK**.  
  
## <a name="enter-the-server-using-the-command-line-tool"></a>Entrez le serveur à l’aide de l’outil de ligne de commande  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est `\Program Files\Common Files\Enterprise Single Sign-On`.  
  
3.  Entrez le serveur d’authentification unique en sélectionnant une des options suivantes :  
  
    1.  Type **ssomanage – server** à entrer le serveur SSO que vous souhaitez vous connecter lorsque vous effectuez des opérations d’administration.  
  
         \- - OU -  
  
    2.  Type **ssomanage - serverall** pour entrer le serveur d’authentification unique se connectera à tous les utilisateurs de cet ordinateur lors de l’exécution des opérations d’administration.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment installer l’utilitaire Client SSO](../core/how-to-install-the-sso-client-utility.md)   
 [Configuration de l’authentification unique](../core/configuring-sso.md)   
 [L’installation de l’authentification unique](../core/installing-sso.md)
