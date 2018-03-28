---
title: Installer et configurer Microsoft BizTalk ESB Toolkit | Documents Microsoft
description: Par étapes des instructions pour installer et configurer la boîte à outils ESB dans BizTalk Server
caps.latest.revision: ''
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 698843f7-8361-4d02-9278-0e66f2a9f472
ms.author: mandia
ms.openlocfilehash: 33805fe58298e4f4729161a62742d3b204996b00
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="install-and-configure-the-microsoft-biztalk-esb-toolkit"></a>Installer et configurer Microsoft BizTalk ESB Toolkit
En commençant par BizTalk Server 2013 et les versions plus récentes, [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est intégré à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le programme d’installation. Cette rubrique vous montre comment installer et configurer [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]et inclut également un lien écrit par la Communauté pour mettre à niveau ESB Toolkit.  
  
> [!IMPORTANT]
>  Vous devez avoir installé BizTalk Server avant de commencer à installer [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
## <a name="install"></a>Installation 
  
1.  Exécutez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] du fichier setup.exe en tant qu’administrateur. Dans le programme d’installation, sélectionnez **installer [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** .  
  
2.  Acceptez le contrat de licence, puis sélectionnez **suivant**.  
  
3.  Dans **Installation des composants**, sélectionnez les composants à installer, puis **Suivant**.  
  
4.  Dans le **Résumé**, passez en revue vous avez choisi, puis sélectionnez **installer**.  
  
5.  Sélectionnez **Terminer** pour fermer l’Assistant Installation.  

Un fichier journal d’installation est créé, semblable à « C:\Users\yourUserName\AppData\Local\Temp\Setup(081017 175042).htm ». 
  
## <a name="configure"></a>Configurer 
  
> [!IMPORTANT]
>  Vous devez configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] avant de configurer [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
1.  À partir de la **Démarrer** menu, sélectionnez **Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]** , puis sélectionnez **outil de Configuration ESB**.  
  
    > [!IMPORTANT]
    >  Exécutez l’outil de Configuration ESB en tant qu’administrateur.  
  
2.  Dans la configuration, sélectionnez **serveur de base de données**. Entrez le nom du serveur de base de données qui héberge la [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] bases de données.   
  
3.  Dans **Services Web IIS**, entrez le compte d’utilisateur et un mot de passe qui exécute les applications IIS créées par le [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]. Ensuite, entrez le site Web IIS qui héberge les applications.  
  
4.  Le **groupes d’utilisateurs BizTalk** répertorie les groupes d’utilisateurs par défaut généralement utilisés pour la configuration ESB.  
  
    > [!IMPORTANT]
    >  À ce stade, vous pouvez sélectionner **appliquer la Configuration** pour configurer le [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] avec ces paramètres par défaut. Toutefois, si vous souhaitez effectuer une configuration personnalisée, effectuez les étapes restantes. Les valeurs de Rhe que vous entrez dans les étapes suivantes sont prioritaires sur les valeurs par défaut.  
  
5.  Dans le volet gauche, développez **Configuration ESB**, développez ** Exception Management **, puis :  
  
    -   Si vous ne souhaitez pas configurer une base de données de gestion d’exception, puis sélectionnez **base de données**et désactivez la **activer Exception d’administration de base de données**.
  
    -   Si vous souhaitez utiliser une base de données existante au lieu de créer une nouvelle base de données, puis sélectionnez **base de données**, puis sélectionnez le **utiliser une base de données existante**. Entrez le nom du serveur de base de données et le nom de la base de données.  
  
    -   Si vous ne souhaitez pas configurer le service web d’exception, puis sélectionnez **Exception Web Services**, puis décochez **activer les Services d’Exception**.  Si vous souhaitez exécuter ces services sous un autre site Web, vous pouvez le saisir ici.  
  
6.  Dans le volet gauche, développez **les composants centraux ESB**, puis :  
  
    -   Si vous ne souhaitez pas configurer une base de données d’itinéraire, puis sélectionnez **base de données de la feuille de route**, puis décochez **base de données de la feuille de route** .  
  
    -   Si vous souhaitez utiliser une base de données d’itinéraire existant, puis sélectionnez **base de données de la feuille de route**, puis sélectionnez **utiliser une base de données existante**. Entrez le nom du serveur de base de données et le nom de la base de données.  
  
    -   Si vous ne souhaitez pas configurer ces services web, puis sélectionnez **Services Web principaux**, puis décochez **activer les Services principaux**. Si vous souhaitez exécuter ces services sous un autre site Web, vous pouvez le saisir ici.
  
7.  Dans le volet gauche, sélectionnez **Configuration**.  
    Si vous installez et configurez le [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] dans un environnement de serveur unique, sélectionnez **fichier de Configuration Source**. Si vous configurez un déploiement sur plusieurs ordinateurs, sélectionnez le **SSO Configuration Source**, puis entrez les éléments suivants :  
  
    -   **Serveur d’authentification unique**: entrez le nom du serveur SSO
  
    -   **Fichier de configuration**: sélectionnez les points de suspension **(...)** , puis accédez au fichier esb.config (\Program Files (x86) \Microsoft BizTalk ESB Toolkit)
  
    -   **Nom de l’application**: entrez un nom pour l’application SSO. Par exemple, entrez `ESB Toolkit`.  
  
    -   **Les informations de contact**: entrez une adresse de messagerie valide les informations de contact appropriées dans le format suivant : `someone@example.com`.  
  
    -   **Nom du groupe administrateur**: sélectionnez les points de suspension **(...)** , puis accédez au groupe d’administration approprié  
  
    -   **Nom du groupe d’utilisateurs**: sélectionnez les points de suspension **(...)** , puis accédez au groupe approprié  

8.  Sélectionnez **appliquer la Configuration**. En ouvrant IIS, vous remarquez que les applications requises pour [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)] sont désormais créées sous le site Web spécifié lors de la configuration [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)].  
  
9. Dans le **outil de Configuration ESB**, sélectionnez **ESB BizTalk Applications**, puis :  
  
    -   Sélectionnez **activer les composants centraux ESB dans BizTalk Server** pour créer l’application dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Sélectionnez **utilisation de liaison par défaut** pour lier cette application à l’hôte par défaut. Sélectionnez **n’utilisent pas de liaison par défaut** si vous ne souhaitez pas lier l’application à l’hôte par défaut. Dans ce scénario, vous devez lier explicitement l’application sur un ordinateur hôte une fois que l’application est créée.  
  
    -   Sélectionnez **activer les composants ESB JMS/WMQ dans BizTalk Server** pour créer l’application dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Sélectionnez **utilisation de liaison par défaut** pour lier cette application à l’hôte par défaut. Sélectionnez **n’utilisent pas de liaison par défaut** si vous ne souhaitez pas lier l’application à l’hôte par défaut. Dans ce scénario, vous devez lier explicitement l’application sur un ordinateur hôte une fois que l’application est créée.  
  
    -   Sélectionnez **appliquer la Configuration** pour créer les applications que vous avez sélectionné. Vérifiez que les applications sont créées dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="upgrade-esb-toolkit--community-addition"></a>Mise à niveau d’ESB Toolkit : ajout de la Communauté  
 [Mise à niveau d’ESB Toolkit 2.1 vers 2.2 place](http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html) ()http://www.brianloesgen.com/blog/2013/10/10/in-place-upgrade-of-esb-toolkit-21-to-22.html)

## <a name="see-also"></a>Voir aussi
[Dépanner des problèmes d’installation et courantes erreurs & résolutions](troubleshooting-the-biztalk-esb-toolkit.md)