---
title: "Options d’Installation standard de l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, SSO
- SSO, installing
ms.assetid: 59aeb503-f369-4145-8a3c-ab60e9ed31a8
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26441ca5d63ebdb4cba807173f7e7068ff846bdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="standard-sso-installation-options"></a>Options d’Installation standard de l’authentification unique
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] tire parti des fonctionnalités de l'authentification unique de l'entreprise pour stocker des informations d'identification de manière sécurisée à des fins d'autorisation de scénarios d'authentification unique.  
  
 BizTalk Server fait également appel à l'authentification unique pour stocker en toute sécurité des données de configuration personnalisées associées à des adaptateurs. Pour ce faire, les composants d'exécution et d'administration de BizTalk Server installent SSO en tant que composant dépendant. L'installation par défaut de BizTalk Server comporte l'authentification unique de l'entreprise.  
  
> [!NOTE]
>  Après avoir installé l'authentification unique de l'entreprise (composant serveur), vous devez la configurer. La première étape de la configuration d'un système SSO consiste à paramétrer le serveur de secret principal. Il est recommandé de configurer un serveur de secret principal autonome. Cette opération peut être réalisée en sélectionnant uniquement l'authentification unique de l'entreprise dans l'arborescence des fonctionnalités personnalisées du programme d'installation de BizTalk Server.  
>   
>  Il est également recommandé que chaque ordinateur exécutant l'authentification unique de l'entreprise dispose d'un service de synchronisation d'heure en cours d'exécution. Cela permet de synchroniser l'heure d'un ordinateur avec le reste du système, une condition nécessaire au bon fonctionnement des services d'émission de tickets SSO.  
  
 **Liste des options d’installation**: exécuter la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] programme d’installation. Sélectionnez **Installation personnalisée**, puis sélectionnez l’option appropriée dans la liste suivante :  
  
-   **Administration de l’authentification unique de l’entreprise :** outils d’Administration et de client pour le mappage et de la connexion aux Services d’authentification unique de l’entreprise.  
  
-   **Entreprise seule l’authentification serveur de secret principal :** joue le rôle du serveur de secret principal dans le système d’authentification unique. Il s'agit du premier serveur qui doit être déployé dans le système SSO mais aussi celui qui vous permet de créer la base de données SSO.  
  
 À l'aide de l'utilitaire Ajout/Suppression de programmes, vous pouvez également ajouter les composants suivants après l'installation :  
  
-   **Serveur Runtime :** Core services pour activer l’authentification unique et à stocker ou accéder aux données de configuration en toute sécurité.  
  
-   **Administration de l’authentification unique de l’entreprise :** outils d’Administration et de client pour le mappage et de la connexion aux Services d’authentification unique de l’entreprise.  
  
-   **Seule l’authentification Services d’entreprise avec synchronisation de mot de passe :** Services pour activer la fonctionnalité de synchronisation de mot de passe dans le système d’authentification unique de l’entreprise. Ces services s'intègrent également au service de notification de modification de mot de passe. Après avoir installé les principaux services de l'authentification unique de l'entreprise, vous pouvez installer la fonctionnalité de synchronisation de mot de passe à partir du package BizTalk Server. Pour ce faire, exécutez \Platform\SSO\Setup.exe, puis sélectionnez la fonctionnalité Synchronisation de mot de passe.  
  
-   **Kit de développement logiciel** informations de référence et de programmation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment installer le composant Administration de l’authentification unique](../core/how-to-install-the-sso-administration-component.md)  
  
-   [Comment installer l’utilitaire Client SSO](../core/how-to-install-the-sso-client-utility.md)