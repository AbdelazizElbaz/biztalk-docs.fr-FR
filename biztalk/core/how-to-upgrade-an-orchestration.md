---
title: "La mise à niveau d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef3f032f-28a1-4d52-9d85-d5748c9e9682
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edd9fa8e98b62ec92b1313cc1028efc5320ce17e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-upgrade-an-orchestration"></a>Mise à niveau d'une orchestration
La mise à jour d’une orchestration qui s’exécute dans un environnement de production lorsque l’orchestration gère des transactions à long terme ou attend une réponse à partir d’un port de sollicitation-réponse.

## <a name="overview"></a>Vue d'ensemble
 Lorsqu’une orchestration ne gère pas les transactions à long terme, vous pouvez mettre à jour comme décrit dans [liste de vérification : mise à jour les artefacts dans une Application BizTalk](../core/checklist-update-the-artifacts-in-a-biztalk-application.md). Lorsqu'une orchestration gère des transactions à long terme, cependant, vous ne pouvez pas mettre immédiatement en service sa version mise à jour. Vous devez permettre à la version d'origine de terminer le traitement de ses messages, afin qu'ils ne soient pas perdus. Pour ce faire, vous déployez l'orchestration mise à jour dans l'application utilisée par l'orchestration d'origine. Vous arrêtez ensuite la version d'origine et démarrez la version mise à jour afin qu'elle reçoive tous les nouveaux messages tandis que l'ancienne version continue de traiter les éventuels messages en vol. Une fois que l'orchestration d'origine a fini de traiter tous ses messages, vous annulez son déploiement dans l'application BizTalk dans laquelle elle a été déployée.  
  
 Pour plus d’informations sur ce scénario, consultez [scénario : mise à jour des artefacts de l’Application](../core/scenario-updating-application-artifacts.md).  
  
> [!IMPORTANT]
>  Si plusieurs orchestrations sont liées au même port de réception et qu'elles sont toutes démarrées ou inscrites, vous créez des messages en double dans le système.  
  
> [!NOTE]
>  Lorsque vous mettez à niveau vers une nouvelle orchestration, des instances d'orchestration peuvent prendre l'état Suspendu (peut être repris) sous forte sollicitation, du fait de la condition d'engorgement entre l'ancienne orchestration et la nouvelle pendant la mise à niveau. Pour reprendre manuellement ces instances d’orchestration, consultez [comment reprendre les Instances d’Orchestration suspendues](../core/how-to-resume-suspended-orchestration-instances.md).

## <a name="prerequisites"></a>Conditions préalables  
Connectez-vous avec un compte qui est membre de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs. Votre compte doit également avoir l’autorisation de lecture/écriture sur le système de fichiers local et le global assembly cache. Le compte des administrateurs de l'ordinateur local dispose de cette autorisation.  

Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md), et [de sécurité minimales ](https://social.technet.microsoft.com/wiki/contents/articles/24590.minimum-security-rights-for-biztalk-server-2006-to-2016.aspx). 
 
## <a name="update-an-orchestration"></a>Mise à jour d’une orchestration  
  
1.  Modifiez l'orchestration en fonction de vos besoins.  
  
2.  Incrémentez le numéro de version de l'assembly, de la façon suivante :  
  
    1.  Dans l’Explorateur de solutions, cliquez sur le projet BizTalk, puis cliquez sur **propriétés** pour lancer le Concepteur de projet pour le projet.  
  
    2.  Cliquez sur le **Application** onglet si elle n’est pas déjà active, puis cliquez sur **informations de l’Assembly**.  
  
    3.  Dans le volet droit, augmentez le numéro de version de l'assembly. Vous ne devez augmenter que le numéro de version majeure ou mineure. Le numéro de version majeure est le premier chiffre de la séquence (**0**.0.0.0).) ; le numéro de version mineure est le deuxième chiffre de la séquence (0. **0**. 0.0). BizTalk Server ne reconnaît pas une modification de numéro de version plus loin dans la séquence, telles que 0.0. **0**.0 ou 0.0.0. **0**.  
  
    4.  Cliquez sur **OK** pour fermer la **informations d’Assembly** boîte de dialogue.  
  
    5.  Enregistrez le projet.  
  
3.  Déployez l'assembly à partir de Visual Studio dans une application BizTalk. Pour obtenir des instructions, consultez [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md). Veillez à bien sélectionner l'option de déploiement permettant d'installer l'assembly dans le GAC.  
  
4.  Testez l'assembly contenant l'orchestration.  
  
5.  Exportez l’assembly à partir de l’application dans votre environnement de test dans un fichier .msi, comme décrit dans [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
    > [!NOTE]
    >  La suite de la procédure vous permet de tester l'assembly, ainsi que de le déployer dans votre environnement de production. Pour plus d’informations sur les tâches de déploiement d’application dans le développement, test, intermédiaire et de production, consultez [tâches de déploiement d’Application](../core/application-deployment-tasks.md).  
  
6.  Importer le fichier .msi dans l’application BizTalk dans votre environnement de production qui contient l’orchestration que vous souhaitez mettre à jour, comme décrit dans [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md).  
  
7.  Liez l’orchestration mise à jour avec les mêmes liaisons que l’orchestration d’origine, comme décrit dans [comment configurer les liaisons d’une Orchestration](../core/how-to-configure-bindings-for-an-orchestration.md).  
  
8.  Désinscrivez l'orchestration d'origine, puis démarrez l'orchestration mise à jour. Pour éviter toute suppression de messages, vous devez le faire par programme, comme décrit dans [déploiement et démarrage d’une nouvelle Version d’une Orchestration par programme](../core/deploying-and-starting-a-new-version-of-an-orchestration-programmatically.md). Ou bien, vous pouvez effectuer ces étapes manuellement, comme décrit dans [comment désinscrire une Orchestration](../core/how-to-unenlist-an-orchestration.md), [comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md), et [comment démarrer une Orchestration](../core/how-to-start-an-orchestration.md).  
  
9. Surveillance du système pour les instances de la version d’orchestration d’origine à l’aide de concentrateur du groupe page Affichage de la requête, comme décrit dans [comment afficher les informations d’Instance pour une Orchestration](../core/how-to-view-instance-information-for-an-orchestration.md).  
  
10. Lorsque toutes ses instances actives, mises en attente et suspendues sont terminées, annuler le déploiement de l’orchestration d’origine à partir de l’application, comme décrit dans [comment supprimer une Orchestration à partir d’une Application](../core/how-to-remove-an-orchestration-from-an-application.md).  
  
11. Si vous le souhaitez désinstaller la version d’origine de l’assembly du GAC sur chaque ordinateur qui exécute l’application, comme décrit dans [comment désinstaller un Assembly du GAC](http://msdn.microsoft.com/library/464706a8-f902-4d05-a724-19169facd2b4).  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md)   
 [La gestion des Orchestrations](../core/managing-orchestrations.md)