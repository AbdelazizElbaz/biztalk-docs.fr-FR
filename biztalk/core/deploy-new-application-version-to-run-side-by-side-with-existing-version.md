---
title: "Comment déployer une nouvelle Version d’une Application de s’exécuter côte à côte avec une Version existante | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1677c6a5-2c4c-4d70-ab83-f7e0bb3aaf6e
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 053145729546453b959dc35c7901932c1c8690c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-a-new-version-of-an-application-to-run-side-by-side-with-an-existing-version"></a>Déploiement de la nouvelle version d'une application devant s'exécuter à côté d'une version existante
Comment déployer une nouvelle version d’une application qui s’exécute côte à côte avec une version existante. 

## <a name="overview"></a>Vue d'ensemble
Cette procédure vous permet de déployer de manière échelonnée une mise à jour importante de l'application, par exemple en commençant par la rendre disponible à un sous-ensemble de partenaires commerciaux, plutôt qu'en la mettant à la disposition de l'ensemble des partenaires en une seule fois. Ainsi, vous pouvez continuer à exécuter l'application existante afin de desservir les utilisateurs qui n'utilisent pas encore la nouvelle version, jusqu'à-ce que vous soyez prêt à passer définitivement à la nouvelle version. Pour plus d’informations sur ce scénario, consultez [scénario : déploiement de deux Versions d’une Application](../core/scenario-deploying-two-versions-of-an-application.md).  
  
 Vous ne pouvez pas créer des versions d'une application de la même manière que vous créez des versions d'un assembly, c'est-à-dire en augmentant le numéro de version. Au lieu de cela, vous devez créer une nouvelle application portant un nom différent que l'application d'origine, et la compléter avec les nouvelles versions des artefacts de l'application.  
  
 Étant donné que de nombreux types d'artefacts, tout comme les assemblys, peuvent exister dans une seule application d'un groupe BizTalk, vous devez augmenter le numéro de version de tout assembly existant dans le groupe avant de pouvoir les déployer dans la nouvelle application. Pour plus d’informations, consultez [artefacts que doit être Unique dans une Application ou d’un groupe](../core/artifacts-that-must-be-unique-in-an-application-or-group.md).  

## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs. Votre compte doit également avoir l’autorisation de lecture/écriture sur le système de fichiers local et le global assembly cache. Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.  

Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
  
## <a name="deploy-a-new-version-of-an-application"></a>Déployer une nouvelle version d’une application  
  
1.  Dans Visual Studio, procédez aux modifications nécessaires des assemblys que vous voulez déployer dans la nouvelle version de l'application  
  
2.  Incrémentez le numéro de version de chaque assembly, de la façon suivante :  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
    2.  Cliquez sur le **Application** onglet si elle n’est pas active, puis cliquez sur **informations d’Assembly** bouton.  
  
    3.  Augmentez le numéro de version d’assembly, puis cliquez sur **OK**.  
  
    4.  Enregistrez le projet.  
  
    > [!NOTE]
    >  Utilisez le modèle objet du Concepteur de pipeline pour éviter tout conflit de schémas lors de l'incrémentation des versions d'assembly.  
  
3.  Dans les propriétés de déploiement de chaque projet dans la solution, procédez ainsi :  
  
    -   Modifiez le nom de l'application pour obtenir celui que vous voulez utiliser pour la nouvelle application.  
  
    -   Vérifiez que l'option d'installation des assemblys dans le Global Assembly Cache (GAC) est sélectionnée.  
  
     Pour obtenir des instructions, consultez [comment définir les propriétés de déploiement dans Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md). Lorsque vous déployez la solution, les assemblys sont déployés dans la nouvelle application et installés dans le GAC.  
  
4.  Déployez la ou les solutions contenant les assemblys. Pour obtenir des instructions, consultez [comment déployer un BizTalk Assembly à partir de Visual Studio](../core/how-to-deploy-a-biztalk-assembly-from-visual-studio.md).  
  
5.  Créez un nouveau port de réception et tout emplacement de réception nécessaire en spécifiant la ou les nouvelles URL auxquelles vos partenaires sont censés envoyer des messages. Pour obtenir des instructions, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md). Consultez également [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
6.  Créez les ports d’envoi approprié si nécessaire, comme décrit dans [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md).  
  
7.  Lier la nouvelle application à nouvellement créé de réception et ports d’envoi, comme décrit dans [comment configurer une Application](../core/how-to-configure-an-application.md).  
  
8.  Exporter l’application dans un fichier .msi à partir de votre environnement de test, comme décrit dans [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
    > [!NOTE]
    >  La suite de la procédure vous permet de tester l'application, ainsi que de la déployer dans votre environnement de production. Pour plus d’informations sur les tâches de déploiement d’application dans le développement, test, intermédiaire et de production, consultez [tâches de déploiement d’Application](../core/application-deployment-tasks.md).  
  
9. Importer le fichier .msi d’application dans le groupe BizTalk dans votre environnement de production, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Si l’application nécessite des références, vous pouvez les ajouter lors de l’utilisation de l’Assistant MSI d’importation ou version ultérieure, comme décrit dans [comment ajouter une référence à une autre Application](../core/how-to-add-a-reference-to-another-application.md).  
  
10. Installez l’application sur chaque instance d’hôte qui sera exécuté, comme décrit dans [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md). Vérifiez que chaque assembly mis à jour a été installé dans le GAC sur chaque ordinateur hébergeant l'assembly. Si nécessaire, installez les assemblys dans le GAC, comme décrit dans [comment installer un Assembly dans le GAC](../core/how-to-install-an-assembly-in-the-gac.md).  
  
11. Effectuer un démarrage complet de l’application, comme décrit dans [comment démarrer et arrêter une Application BizTalk](../core/how-to-start-and-stop-a-biztalk-application.md).  
  
12. Informez vos partenaires qu'ils peuvent commencer à envoyer des messages aux nouvelles URL. Ainsi, l'application commence à traiter les messages des partenaires spécifiés.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md)