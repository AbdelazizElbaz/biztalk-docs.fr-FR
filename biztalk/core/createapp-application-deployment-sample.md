---
title: "CreateApp (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, examples
- deploying, .msi file
- deploying, exporting
- .msi files, deploying
- examples, deploying
ms.assetid: 825627ee-21d0-4505-9df4-1dadc51335b6
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 842683d2eec04d77bad2b7726af0d687fae12884
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="createapp-application-deployment-sample"></a>CreateApp (exemple de déploiement d'application)
Cette rubrique explique l'utilisation de l'exemple CreateApp qui illustre l'utilisation de l'outil de ligne de commande BTSTask pour déployer et annuler le déploiement d'une application BizTalk. Vous pouvez utiliser des scripts, tels que ceux inclus dans cet exemple, pour automatiser votre processus de génération nocturne pour déployer et annuler le déploiement d'applications BizTalk.  
  
> [!IMPORTANT]
>  Vous devez toujours écrire vos scripts de déploiement pour une exécution en mode silencieux. Si vous ne le faites pas, des boîtes de dialogue s'affichent et nécessitent des saisies de l'utilisateur. Cela arrête le processus de déploiement jusqu'à la fermeture manuelle de la boîte de dialogue, ce qui peut bloquer le processus d'importation.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 L'exemple inclut des scripts qui automatisent les tâches de déploiement d'applications. Pour effectuer ces tâches, vous exécutez un script qui génère le projet et les fichiers BizTalk. Ensuite, vous exécutez un script qui génère deux fichiers .msi d'application BizTalk : l'un contient tous les artefacts dans une application, l'autre contient uniquement un assembly dans l'application. Puis, vous exécutez un script qui utilise un fichier .msi pour importer une application dans un groupe BizTalk et installer l'application sur l'ordinateur local. Lors de l'installation, un script de pré-traitement inclus dans l'application crée des dossiers utilisés par l'application et consigne ses actions dans un fichier. Enfin, vous exécutez un script qui supprime et désinstalle l'application. Lors de la désinstallation, un script de pré-traitement inclus dans l'application supprime les fichiers et dossiers créés durant l'installation et consigne ses actions dans un fichier.  
  
 Les scripts suivants sont inclus dans cet exemple :  
  
-   **Build.bat.** Génère un fichier de clé, crée le projet dans Visual Studio et signe les fichiers .dll.  
  
-   **CreateFullAndPartialMSI.bat.** Effectue les actions suivantes, dans l'ordre :  
  
    1.  Utilise l’outil BTSTask [commande AddApp](../core/addapp-command.md) pour créer une application.  
  
    2.  Utilise l’outil BTSTask [commande AddResource](../core/addresource-command.md) à ajouter à l’application trois assemblys BizTalk ainsi que d’autres ressources qui ont été générées par Build.bat.  
  
    3.  Utilise l’outil BTSTask [commande ExportApp](../core/exportapp-command.md) pour exporter les artefacts de l’application dans un fichier .msi nommé CreateApplicationSample.msi.  
  
    4.  Utilise l’outil BTSTask [commande ListApp](../core/listapp-command.md) pour générer un manifeste d’application nommé AppManifest.xml, qui répertorie tous les artefacts contenus dans l’application.  
  
    5.  Utilise l’outil BTSTask [commande ExportApp](../core/exportapp-command.md) pour exporter uniquement l’assembly d’orchestrations dans un fichier .msi nommé CreateApplicationSamplePartial.msi. Pour ce faire, ResourceSpecPartial.xml est fourni pour le paramètre ResourceSpec. ResouceSpecPartial.xml est une version modifiée de ResourceSpecComplete.xml qui a été fourni avec cet exemple. Ce fichier a été modifié afin de contenir une référence à l'assembly d'orchestrations uniquement. Lorsqu'il est fourni avec ce paramètre, BTSTask exporte uniquement les artefacts répertoriés dans le fichier ResourceSpecPartial.xml, en l'occurrence l'assembly d'orchestrations.  
  
    6.  Supprime l'application de la base de données de gestion BizTalk pour le groupe.  
  
-   **CreateNewAppFromMSI.bat.** Utilise CreateApplicationSample.msi généré par CreateFullAndPartialMSI.bat pour installer une application nommée CreateApplicationSample sur l’ordinateur local ainsi que pour importer l’application dans le groupe BizTalk. Pendant l’installation, PreProcScript.bat s’exécute automatiquement, comme décrit plus loin.  
  
-   **RemoveApp.bat.** Effectue les actions suivantes, dans l'ordre :  
  
    1.  Utilise l’outil BTSTask [commande RemoveApp](../core/removeapp-command.md) pour supprimer l’application CreateApplicationSample de la base de données de gestion BizTalk pour le groupe.  
  
    2.  Utilise l’outil BTSTask [commande UninstallApp](../core/uninstallapp-command.md) pour désinstaller l’application CreateApplicationSample de l’ordinateur local. Pendant l'installation, PreProcScript.bat s'exécute automatiquement, comme décrit ultérieurement.  
  
-   **PreProcScript.bat.** Effectue les actions suivantes :  
  
    -   À chaque exécution, définit le jeton de clé publique pour l'assembly fourni par l'utilisateur.  
  
    -   Lors de l'installation de l'application, crée les dossiers suivants qui sont utilisés par l'application CreateApplicationSample pour contenir des messages :  
  
         C:\CreateApplicationSample\Out  
  
         C:\CreateApplicationSample\In  
  
    -   Lors de la désinstallation de l'application, supprime les fichiers et dossiers créés au cours de l'installation. Désinstalle également du Global Assembly Cache tout assembly installé dans le GAC lors de l'installation et consigne ses actions dans un fichier. Pour désinstaller les assemblys du Global Assembly Cache, il renvoie au jeton de clé publique fourni par l'utilisateur.  
  
    -   Pendant l'installation et la désinstallation, crée un fichier journal à l'emplacement suivant :  
  
         C:\ScriptLog.txt  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Vous trouverez des exemples de fichiers dans les dossiers suivants sous  *\<exemples de chemin\>*\Application déploiement\\:  
  
-   CreateApp (dossier)  
  
    -   Build.bat  
  
    -   CreateFullAndPartialMSI.bat  
  
    -   CreateNewAppFromMSI.bat  
  
    -   RemoveApp.bat  
  
-   CreateApp\Bindings (dossier)  
  
    -   CreateApplicationSampleBindings.xml  
  
-   CreateApp\Dlls (dossier)  
  
    -   Vide  
  
-   CreateApp\ResourceSpecs (dossier)  
  
    -   ResourceSpecPartial.xml  
  
    -   ResourceSpecComplete.xml  
  
-   CreateApp\Scripts (dossier)  
  
    -   PreProcScript.bat  
  
-   CreateApp\HelloApplicationDeployment (dossier)  
  
    -   HelloApplicationDeployment.suo  
  
    -   HelloApplicationDeployment.sln  
  
-   CreateApp\HelloApplicationDeployment\Maps (dossier)  
  
    -   POToInvoice.btm  
  
    -   Maps.btproj  
  
-   CreateApp\HelloApplicationDeployment\Orchestrations (dossier)  
  
    -   Orchestrations.btproj  
  
    -   HelloOrchestration.odx  
  
-   CreateApp\HelloApplicationDeployment\Schemas (dossier)  
  
    -   Schemas.btproj  
  
    -   POSchema.xsd  
  
    -   InvoiceSchema.xsd  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 La procédure suivante permet d'utiliser l'exemple.  
  
### <a name="to-use-the-sample"></a>Pour utiliser l'exemple  
  
1.  Exécutez Build.bat. Cela génère un fichier de clé, crée les projets sous le dossier HelloApplicationDeployment, signe les fichiers .dll obtenus et met les fichiers .dll dans le dossier Dlls.  
  
2.  Ouvrez le fichier PreProcScript.bat, qui se trouve dans le dossier CreateApp\Scripts. Dans la ligne de code suivante, supprimez REM et indiquez le jeton de clé publique pour l'assembly :  
  
     **REM définie PublicKeyToken =**  
  
     Exemple :  
  
     **définir PublicKeyToken = 1234a5b6c1234567**  
  
3.  Exécutez CreateFullAndPartialMSI.bat. Cela crée deux fichiers .msi d'application, CreateApplicationSample.msi et CreateApplicationSamplePartial.msi.  
  
4.  Exécutez CreateNewAppFromMSI.bat. Cela importe l'application CreateApplicationSample dans le groupe BizTalk et l'installe sur l'ordinateur local.  
  
5.  Consultez le fichier journal du script (C:\ScriptLog.txt) pour vérifier que le script a bien consigné ses actions d'installation.  
  
6.  Assurez-vous que l'application CreateApplicationSample apparaît bien dans la console Administration de BizTalk Server et dans Ajout/Suppression de programmes.  
  
7.  Exécutez RemoveApp.bat. Cela supprime CreateApplicationSample de la base de données de gestion BizTalk et le désinstalle de l'ordinateur local.  
  
8.  Consultez le fichier journal du script (C:\ScriptLog.txt) pour vérifier que le script a bien consigné ses actions de désinstallation. Elles doivent figurer après les actions d'installation consignées précédemment, au cours de l'installation.  
  
9. Assurez-vous que l'application CreateApplicationSample n'apparaît plus dans la console Administration de BizTalk Server ni dans Ajout/Suppression de programmes.  
  
10. Vérifiez que les dossiers créés pendant l'installation ont été supprimés.  
  
11. Vérifiez que les assemblys ont été désinstallés du Global Assembly Cache.  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Déploiement des applications BizTalk](../core/deploying-biztalk-applications.md)