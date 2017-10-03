---
title: Importer et exporter la Configuration de BizTalk Server | Documents Microsoft
description: "Étapes à appliquer, importer, exporter ou annuler la configuration des composants et mettre à jour les bases de données et les comptes de service dans BizTalk Server"
ms.custom: 
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6206ed8-d087-44cc-8ab5-da5d8a28e09a
caps.latest.revision: "40"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d0d2ae3f94c0ced65c65fd36dc3499c93ce40b0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="import-and-export-biztalk-server-configuration"></a>Importation et exportation de la configuration de BizTalk Server
La configuration de BizTalk Server fournit un niveau d'analyse très détaillé sur l'état de la configuration des composants installés en local sur votre ordinateur. Il vous permet de configurer et d'annuler la configuration de composants, de configurer les paramètres de sécurité et d'importer et exporter des configurations.  
  
## <a name="prerequisites-to-use-the-biztalk-server-configuration"></a>Configuration requise pour utiliser la configuration de BizTalk Server  
   
-   Le compte que vous êtes connecté en tant que doit être membre du groupe Administrateurs local et disposer des droits d’administrateur système sur SQL Server.  
  
-   Les comptes par défaut générés par BizTalk Server et répertoriés dans la configuration de BizTalk Server sont des groupes locaux. Dans un environnement multiserveur, remplacez ces groupes locaux avec des groupes de domaine.  
  
-   Le compte que vous êtes connecté en tant que doit être un membre du groupe Administrateurs OLAP sur l’ordinateur OLAP, si la configuration.  
  
    > [!NOTE]
    >  Si vous modifiez l’appartenance de groupe de l’utilisateur connecté actuel, et le groupe est également un membre du domaine, être sûr de se déconnecter et se reconnecter après des modifications. La sortie et à la connexion si vous ne vous connectez pas, vous pouvez refuser l’accès comme nouvelle appartenance de groupe n’est pas reflétée par la connexion actuelle.  
  
## <a name="apply-the-configuration"></a>Appliquer la configuration  
  
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Appliquer la configuration**.  
  
2.  Dans l’écran **Résumé**, passez en revue la configuration, puis cliquez sur **Suivant**.  
  
3.  Dans la page **Achèvement**, cliquez sur **Terminer**.  
  
## <a name="import-configuration"></a>Importer la configuration

> [!IMPORTANT]
> Lorsque vous importez un fichier de configuration, vérifiez que le fichier de configuration ne configure pas un composant qui n’a pas été installé sur le serveur BizTalk que vous configurez. Tenter de configurer un composant qui n'existe pas sur BizTalk Server peut entraîner une situation de blocage. Dans ce cas, annulez la configuration de composants qui dépendent du composant qui tente de configurer le fichier de configuration. Toutefois, essayez d’annuler la configuration des composants dépendants peut-être nécessiter que le composant manquant est présent et configuré. Pour résoudre ce problème, vous devez modifier le fichier de configuration pour supprimer les références aux composants désinstallés ou appliquer le fichier de configuration à une installation compatible de BizTalk Server.  
> 
>  Les mots de passe et les emplacements des fichiers de sauvegarde ne sont pas enregistrées dans le fichier de configuration que vous importez, sauf si vous avez modifié manuellement le fichier. Si les composants sont déjà configurés, ils ne sont pas importés.  
  
  
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Importer la configuration**.  
  
2.  Dans la boîte de dialogue **Ouvrir**, sélectionnez le fichier de configuration à importer, puis cliquez sur **Ouvrir**.  
  
3.  Dans la **configuration de BizTalk Server**, cliquez sur **Appliquer la configuration**.  
  
4.  Dans l’écran **Résumé**, passez en revue la configuration, puis cliquez sur **Suivant**.  
  
5.  Dans la page **Achèvement**, cliquez sur **Terminer**.  

Vous pouvez importer des fichiers de configuration de BizTalk Server à l’aide de l’infrastructure de Configuration de BizTalk Server. Pour plus d’informations sur l’utilisation de ces fichiers, consultez la rubrique [Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md).  
  
## <a name="export-configuration"></a>Configuration de l’exportation

> [!NOTE]
>  Les mots de passe ne sont pas enregistrés dans le fichier de configuration.    
 
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Exporter la configuration**.  
  
2.  Dans la boîte de dialogue **Enregistrer sous**, tapez le nom du fichier à enregistrer, puis cliquez sur **Enregistrer**.  

 Vous pouvez exporter des configurations de BizTalk Server à l’aide de l’infrastructure de Configuration de BizTalk Server. Pour plus d’informations sur l’utilisation de ces fichiers, consultez [utilisation de l’infrastructure de Configuration](../install-and-config-guides/working-with-the-configuration-framework.md)  
  
## <a name="unconfigure-features"></a>Annuler la configuration des fonctionnalités  
 Vous pouvez annuler la configuration des composants BizTalk Server sur l'ordinateur en les supprimant dans la configuration de BizTalk Server.  
  
> [!NOTE]
>  La console Administration de BizTalk Server doit être fermée avant l'annulation de la configuration des composants.  
  
 
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Annuler la configuration des composants**.  
  
2.  Dans la boîte de dialogue **Annuler la configuration des composants**, sélectionnez les composants à supprimer, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Une boîte de dialogue s'ouvre, vous avertissant de l'annulation imminente de la configuration des composants sélectionnés. Pour continuer, cliquez sur **Oui**.  
  
3.  Dans l’écran **Résumé**, passez en revue la configuration, puis cliquez sur **Suivant**.  
  
4.  Dans la page **Achèvement**, cliquez sur **Terminer**.  
  
## <a name="update-databases"></a>Mettre à jour des bases de données  
 Vous pouvez modifier les serveurs de bases de données et les bases de données associés aux composants BizTalk Server en les modifiant dans la configuration de BizTalk Server.  
  
> [!NOTE]
>  La configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur des instances par défaut SQL Server et des instances nommées est prise en charge.  
> 
>  Cet outil vous permet de modifier les bases de données en bloc.  
  
 
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Afficher**, puis sur **Bases de données**.  
  
2.  Dans la boîte de dialogue **Bases de données**, sélectionnez le composant à modifier, puis cliquez sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Bases de données**, tapez le nom du serveur de base de données et de la base de données à utiliser, puis cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Bases de données**, cliquez sur **Fermer**.  
  
## <a name="update-service-accounts"></a>Mettre à jour des comptes de service  
 Vous pouvez modifier les comptes de service associés aux composants BizTalk Server en les modifiant dans la configuration de BizTalk Server.  
  
> [!NOTE]
>  Cet outil vous permet de modifier les comptes en bloc.  
  
1.  Dans la **configuration de BizTalk Server**, cliquez sur **Afficher**, puis sur **Comptes de service**.  
  
2.  Dans la boîte de dialogue **Comptes de service**, sélectionnez le composant à modifier, puis cliquez sur **Modifier**.  
  
3.  Dans la boîte de dialogue **Informations d’identification de l’utilisateur**, tapez le nom d’utilisateur et le mot de passe à utiliser, puis cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Comptes de service**, cliquez sur **Fermer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Utilisation de Configuration Framework](../install-and-config-guides/working-with-the-configuration-framework.md)   