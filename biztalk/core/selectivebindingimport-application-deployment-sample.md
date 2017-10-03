---
title: "SelectiveBindingImport (exemple de déploiement d’Application) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- examples, applications
- binding files, examples
- examples, importing
- applications, binding files
- applications, examples
- applications, importing
- deploying, scripts
- examples, binding files
ms.assetid: 963bfc80-8cc4-4d90-96b4-e85ae04405cf
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fff8a48a05f310db2d11eeddd5a0082132bbe193
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="selectivebindingimport-application-deployment-sample"></a>SelectiveBindingImport (exemple de déploiement d'application)
Cette rubrique décrit l'utilisation de l'exemple SelectiveBindingImport. Cet exemple de script permet d'appliquer plusieurs liaisons à une application lorsque vous importez celle-ci dans différents environnement de destination. Vous pouvez utiliser cette approche pour importer les liaisons des fichiers de liaison stockés sur un partage réseau.  
  
> [!NOTE]
>  Si vous ne devez pas importer automatiquement les fichiers de liaison d'un partage réseau lors de l'importation de l'application, vous pouvez ajouter à l'application plusieurs fichiers de liaison dans lesquels différents environnements de destination sont spécifiés. Lorsque vous importez l'application, vous pouvez spécifier l'environnement, de sorte que les liaisons pour cet environnement sont appliquées automatiquement. Pour plus d’informations, consultez [déploiement d’applications et des fichiers de liaison](../core/binding-files-and-application-deployment.md).  
  
 Les applications BizTalk sont généralement déplacées entre les environnements de développement, de test, intermédiaire et de production. Les liaisons utilisées au sein de ces environnements sont généralement différentes. Cet exemple permet d'appliquer les liaisons pour différents environnements comme suit :  
  
1.  en plaçant les fichiers de liaison à utiliser dans un partage réseau.  
  
2.  en ajoutant un script de post-traitement à l'application qui importera depuis cet emplacement le fichier de liaison correct pour l'environnement de destination particulier lors de l'importation de l'application. Le script détecte l'environnement en lisant la variable d'environnement %ENVIRONMENT% que vous définissez sur l'ordinateur local,  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre l'importation sélective de fichiers de liaison d'un partage réseau à l'aide d'un script de post-traitement contenu dans un fichier .msi d'application BizTalk.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 Vous pouvez rechercher les dossiers et les fichiers sous  *\<exemples de chemin >*\Application Deployment\SelectiveBindingImport :  
  
-   Develop (dossier)  
  
    -   Dev.xml  
  
-   Production (dossier)  
  
    -   Production.xml  
  
-   Staging (dossier)  
  
    -   Staging.xml  
  
-   Test (dossier)  
  
    -   Test.xml  
  
-   SelectiveBindings.bat  
  
## <a name="how-to-use-this-sample"></a>L’utilisation de cet exemple  
 Les procédures suivantes permettent d'exécuter l'exemple.  
  
### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Exécutez **Build.Bat à partir de la  *\<exemples de chemin >*\Application Deployment\CreateApp** active. Cette opération crée les fichiers suivants dans le  *\<exemples de chemin >*\Application Deployment\CreateApp\Dlls dossier : Schemas.dll, Maps.dll et Orchestrations.dll.  
  
2.  **Créer l’application.** Dans la console Administration de BizTalk Server, créez une application, comme décrit dans [la création d’une Application](../core/how-to-create-an-application.md).  
  
3.  **Ajouter à l’application les fichiers .dll créés dans la première étape.** Pour obtenir des instructions, consultez [l’ajout d’un BizTalk Assembly à une Application](../core/how-to-add-a-biztalk-assembly-to-an-application.md).  
  
4.  **Créez la variable d’environnement, comme suit :**  
  
    1.  Dans le menu Démarrer, cliquez sur **poste** et cliquez sur **propriétés**.  
  
    2.  Sur le **avancé** , cliquez sur **Variables d’environnement**.  
  
    3.  Dans le **variables utilisateur** , cliquez sur **nouveau**.  
  
    4.  Dans **nom de la Variable**, type **environnement**.  
  
    5.  Dans **valeur de la Variable**, type sur des valeurs suivantes pour l’environnement : **développer**, **Production**, **intermédiaire**, ou **Test**. Ces valeurs respectent la casse.  
  
5.  Cliquez sur **OK** trois fois.  
  
6.  **Copiez les fichiers de liaison vers un emplacement sur votre système de fichiers.** Copiez les fichiers .xml de liaison des dossiers Develop, Test, Staging et Production dans un emplacement de votre système de fichiers.  
  
7.  **Modifiez le script de post-traitement.** Modifiez le fichier SelectiveBindings.bat comme suit :  
  
    1.  **Spécifiez l’emplacement de fichier de liaison.** Dans la ligne contenant BINDINGS_LOC, supprimez REM et indiquez le chemin d'accès à l'emplacement dans lequel vous avez copié les fichiers de liaison.  
  
         Exemple :  
  
         BINDINGS_LOC=C:\MyBindings  
  
    2.  **Spécifiez le nom de l’application.** Dans la ligne contenant APPLICATION_NAME, supprimez REM et indiquez le nom de l'application dans laquelle importer les liaisons.  
  
         Exemple :  
  
         APPLICATION_Name=SelectiveBindingImport  
  
8.  **Ajoutez le script à l’application en tant que script de post-traitement.** Pour obtenir des instructions, consultez [Ajout antérieur à la version ou un Script de post-traitement à une Application](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md).  
  
9. **Exportez l’application.** Pour obtenir des instructions, consultez [comment exporter une Application BizTalk](../core/how-to-export-a-biztalk-application.md).  
  
10. **Supprimer l’application.** Pour obtenir des instructions, consultez [comment supprimer une Application BizTalk du groupe BizTalk](../core/how-to-delete-a-biztalk-application-from-the-biztalk-group.md).  
  
11. **Importez l’application.** Pour obtenir des instructions, consultez [comment importer une Application BizTalk](../core/how-to-import-a-biztalk-application.md). Il n'est pas nécessaire de spécifier un environnement de destination.  
  
12. **Vérifiez que le fichier de liaison approprié a été appliqué.** Pour ce faire, vérifiez le champ de description des emplacements de réception comme suit :  
  
    1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
    2.  Dans l'arborescence de la console, développez successivement le groupe BizTalk, l'application BizTalk, puis le dossier Emplacements de réception.  
  
    3.  Dans le volet droit, consultez la description des emplacements de réception.  
  
13. **Installer l’application.** Pour obtenir des instructions, consultez [comment installer une Application BizTalk](../core/how-to-install-a-biztalk-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement d’applications (dossier d’exemples BizTalk Server)](../core/application-deployment-biztalk-server-samples-folder.md)   
 [Déploiement d’Applications BizTalk](../core/deploying-biztalk-applications.md)