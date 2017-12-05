---
title: "Modèle (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, examples
- scripts, deploying
- deploying, scripts
- examples, deploying
ms.assetid: 7e77ff8e-b2bc-4d38-b5fd-329d6d54221f
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315a685f0e289d60e3db9dfbe77bae5a7e2b19f0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="template-application-deployment-sample"></a>Modèle (exemple de déploiement d'une application)
Cette rubrique décrit l'utilisation de l'exemple de modèle pour le déploiement d'une application.  
  
 Vous pouvez créer et utiliser les deux types de scripts de déploiement pour personnaliser le déploiement d’applications BizTalk : scripts de pré-traitement et de scripts de post-traitement. Les scripts de pré-traitement sont appelés avant le début de l'installation et de l'importation de l'application, ainsi qu'une fois la désinstallation terminée. Les scripts de post-traitement sont appelés après la fin de l'installation et de l'importation de l'application, ainsi qu'avant le début de la désinstallation.  
  
 Vous pouvez écrire de tels scripts pour qu'ils soient appelés pour chacune de ces opérations. Vous pouvez également les configurer de manière à ce qu'ils soient exécutés uniquement après l'une d'entre elles. Pour plus d’informations sur l’écriture de scripts, consultez [à l’aide de Scripts de pré-traitement et post-traitement pour personnaliser le déploiement Application](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).  
  
 Cette rubrique illustre l'écriture et le déploiement d'un script de façon à ce qu'il soit appelé avant ou après une seule opération. Pour ce faire, écrivez un script chargé de vérifier les valeurs de trois variables d'environnement pour déterminer le contexte de l'opération au sein duquel le script est appelé. En fonction de ce contexte, le script continue ou interrompt l'exécution.  
  
 Cette rubrique présente les étapes suivantes :  
  
1.  Définition de l'emplacement du fichier journal, de manière à pouvoir générer un fichier journal des opérations du script.  
  
    > [!NOTE]
    >  Il est recommandé de toujours générer un fichier journal pour vérifier les opérations de script et résoudre les problèmes éventuels.  
  
2.  Création d'une application BizTalk et ajout des exemples de scripts à celle-ci.  
  
3.  Export d'un fichier .msi contenant les artefacts de l'application.  
  
4.  Suppression de l'application dans le groupe BizTalk, de manière à y importer de nouveau le fichier .msi et l'installer à partir de ce fichier.  
  
5.  Importation de l'application et vérification du fichier journal pour s'assurer de la réussite de l'opération.  
  
6.  Installation de l'application et vérification du fichier journal pour s'assurer que le journal d'installation y a bien été ajouté.  
  
7.  Affichage des fichiers journaux et consignation de la nature et de l'heure des opérations réalisées par les scripts.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Deux fichiers .bat fournis avec cet exemple contiennent les valeurs des variables d'environnement pour les opérations d'importation, d'installation et de désinstallation. Le fichier SamplePreProcessing.bat inclut les variables d'un script de pré-traitement. Le fichier SamplePostProcessing.bat inclut les variables d'un script de post-traitement. Les fichiers présentent également la méthode d'enregistrement des messages à partir de scripts. Vous pouvez copier les sections appropriées dans vos scripts.  
  
> [!IMPORTANT]
>  Certains commentaires contenus dans les fichiers de script sont incorrects, à savoir :  
>   
>  Dans le fichier SamplePreProcessing.bat, le commentaire de script « Pré-désinstallation du script appelée pour une application existante » devrait plutôt afficher « Post-désinstallation du script appelée pour une application existante ».  
>   
>  Dans le fichier SamplePostProcessing.bat, le commentaire de script « Post-désinstallation du script appelée pour une application existante » devrait plutôt afficher « Pré-désinstallation du script appelée pour une application existante ».  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 L'exemple se trouve dans le dossier d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], comme suit :  
  
 *\<Exemples de chemin d’accès\>*\Application Deployment\Template  
  
 Comme indiqué précédemment, l'exemple inclut les deux fichiers suivants :  
  
-   SamplePreProcessing.bat  
  
-   SamplePostProcessing.bat  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Pour exécuter l'exemple, procédez comme suit.  
  
### <a name="to-set-the-logging-location"></a>Pour définir l'emplacement des journaux  
  
-   Ouvrez les exemples de scripts et modifiez la variable LogFile de sorte qu'elle renvoie à l'emplacement dans lequel les fichiers journaux doivent être générés. Vous devez indiquer le chemin d'accès complet, y compris le nom de fichier. Si elle comprend des espaces, vous devez placer le chemin d’accès entre guillemets doubles («).  
  
     Exemple :  
  
     définir le fichier journal = «*\<exemples de chemin\>*\ApplicationDeployment\Templates\SampleLogOut.txt »  
  
### <a name="to-create-a-new-application"></a>Pour créer une application  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l'arborescence de la console, développez successivement la [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], puis le groupe BizTalk.  
  
3.  Avec le bouton droit **Applications** puis cliquez sur **nouveau**.  
  
4.  Dans **nom de l’Application**, type `SamplesTemplate`, puis cliquez sur **OK**.  
  
### <a name="to-add-the-scripts-to-the-application"></a>Pour ajouter les scripts à l'application  
  
1.  Développez le dossier de l’application SamplesTemplate que vous venez de créer et cliquez sur **ressources** dans le volet gauche.  
  
2.  Pointez sur **ajouter** et cliquez sur **Scripts de pré-traitement**.  
  
3.  Cliquez sur **ajouter** et accédez au fichier SamplePreProcessing.bat.  
  
4.  Sélectionnez le fichier et cliquez sur **ouvrir**.  
  
5.  Dans **type de fichier**, cliquez sur **System.BizTalk : preprocessingscript**, puis cliquez sur **OK**.  
  
     Le fichier SamplePreProcessing.bat est ajouté à l'application, et affiché dans le dossier Ressources associé.  
  
6.  Ressources avec le bouton droit à nouveau, pointez sur **ajouter**, puis cliquez sur **Scripts de post-traitement**.  
  
7.  Cliquez sur **ajouter** et accédez au fichier SamplePostProcessing.bat.  
  
8.  Sélectionnez le fichier et cliquez sur **ouvrir**.  
  
9. Dans **type de fichier**, cliquez sur **System.BizTalk : postprocessingscript**, puis cliquez sur **OK**.  
  
     Le fichier SamplePostProcessing.bat est ajouté à l'application, et affiché dans le dossier Ressources associé.  
  
### <a name="to-export-an-msi-file"></a>Pour exporter un fichier .msi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur l’application SamplesTemplate, pointez sur **exporter**, puis cliquez sur **fichier MSI**.  
  
2.  Dans la page d’accueil de l’Assistant Exportation, cliquez sur **suivant**.  
  
3.  Dans la page Sélectionner les ressources, cliquez sur **suivant**.  
  
4.  Dans la page spécifier les hôtes IIS, cliquez sur **suivant**.  
  
5.  Dans la page dépendances, cliquez sur **suivant**.  
  
6.  Dans la page de Destination, dans **nom de l’application Destination**, tapez le nom de l’application.  
  
7.  Dans **fichier MSI à générer**, tapez le chemin d’accès complet pour le fichier MSI, puis cliquez sur **exporter**. Exemple : C:\MSI\SamplesTemplate.msi  
  
8.  Dans la page Résumé, cliquez sur **Terminer**.  
  
### <a name="delete-the-application"></a>Pour supprimer l'application  
  
-   Dans la console Administration de BizTalk Server, cliquez sur l’application SamplesTemplate, puis cliquez sur **supprimer**.  
  
### <a name="to-import-the-msi-file"></a>Pour importer le fichier .msi  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur **Applications**, pointez sur **importation**, puis cliquez sur **fichier MSI**.  
  
2.  Sur la page d’accueil de l’Assistant Importation, dans **fichier MSI à importer**, tapez le chemin d’accès du fichier .msi que vous exportées, puis cliquez sur **suivant**. Si nécessaire, vous pouvez rechercher le fichier MSI en cliquant sur le **(...)** bouton.  
  
3.  Dans la page Paramètres de l’Application, dans le **nom de l’Application** liste déroulante, sélectionnez le nom de l’application.  
  
4.  Dans **applications disponibles auxquelles ajouter des références aux**, sélectionnez les applications auxquelles ajouter des références, éventuellement, puis cliquez sur **suivant**.  
  
5.  Dans la page Paramètres d’environnement Application cible, cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Il est inutile de spécifier un environnement cible dans le cadre de cet exemple. Pour plus d’informations sur cette fonctionnalité, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md). Pour obtenir des instructions sur l’ajout de fichiers de liaison, consultez [l’ajout d’un fichier de liaison à une Application](../core/how-to-add-a-binding-file-to-an-application2.md).  
  
6.  Dans la page Résumé d’importation, vérifiez que les informations de résumé sont correctes, puis cliquez sur **importation**.  
  
7.  Dans la page de résultats, cliquez sur **Terminer**.  
  
8.  Ouvrez le fichier journal créé lors de l'exécution des scripts, puis vérifiez que l'opération d'importation y a été consignée.  
  
### <a name="to-install-the-application"></a>Pour installer l'application  
  
1.  Double-cliquez sur le fichier .msi, puis exécutez l'Assistant Installation.  
  
2.  Ouvrez le fichier journal, puis vérifiez que l'opération d'installation y a été consignée.  
  
### <a name="to-verify-that-the-scripts-functioned-correctly"></a>Pour vérifier le bon fonctionnement des scripts  
  
-   Ouvrez les fichiers journaux, puis vérifiez qu'ils ont été exécutés lors des opérations spécifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Déploiement des applications BizTalk](../core/deploying-biztalk-applications.md)