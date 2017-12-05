---
title: Compensation (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- compensations, examples
- examples, compensations
- compensations, orchestrations
ms.assetid: 9d10c7be-6a4c-44cc-bf29-78ecdf147bd1
caps.latest.revision: "32"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9752fced7e1b889c41b6e981be6c2858f0411b7b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="compensation-biztalk-server-sample"></a>Compensation (exemple BizTalk Server)
L’exemple Compensation illustre l’utilisation de la **compenser** forme dans une orchestration.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment compenser la transaction déjà validée dans l'orchestration en procédant comme suit :  
  
1.  Entrez les données client dans le formulaire InfoPath et envoyez-les à une orchestration exposée comme service Web.  
  
2.  L'orchestration effectue deux actions parallèles. L'une d'elle renvoie un accusé de réception au formulaire InfoPath, tandis que l'autre met à jour les bases de données Northwind et BTSCompensationSampleMailingList.  
  
3.  Dans la seconde action, l’orchestration mappe le message entrant à un format de message des applications client relation management (CRM) et met à jour la **clients** table dans la base de données Northwind. La table Mailing List dans la base de données BTSCompensationSampleMailingList est ensuite mise à jour.  
  
4.  Si une des actions échoue, les modifications apportées à la base de données Northwind sont compensées via l'appel d'un assembly externe pour réécrire les données client d'origine dans la base de données.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 A **étendue** forme est principalement utilisé pour l’exécution transactionnelle et la gestion des exceptions, notamment la compensation. Une étendue est constituée de deux blocs. Le premier est le bloc de contexte et le second peut être un ou plusieurs blocs de gestion des exceptions ou de compensation (équivalent à l'instruction try-catch dans le langage de programmation .NET). L'orchestration UpdateContact.odx inclut deux actions parallèles. La branche de droite, le bloc try est la **étendue** forme nommée Updated Backend Systems, qui a une transaction à Long terme de type et un identificateur de transaction Upd_Backend. Plus bas dans le flux, un bloc catch intercepte l'exception générale et initie la compensation.  
  
 Pour plus d’informations sur la **étendue** mettre en forme, consultez [étendues](../core/scopes.md). Consultez également [comment configurer la forme étendue](../core/how-to-configure-the-scope-shape.md).  
  
> [!NOTE]
>  L’orchestration doit être une transaction à long terme pour vous permettre de définir le type de transaction sur atomique ou à Long terme.  
  
 Dans le bloc try, il existe deux étendues nommées **mise à jour CRM** et **mise à jour de publipostage**. Toutes deux sont des transactions atomiques. L'étendue Update CRM inclut un bloc try et un bloc compensation. Le bloc try met à jour la base de données Northwind via un appel de méthode auprès d'un assembly externe. Le bloc compensation est l'emplacement dans lequel l'action de compensation intervient. Lorsqu'une exception survient dans l'étendue Update Backend Systems, le code dans la forme Undo CRM Expression met à jour l'enregistrement à son état d'origine. Cela est déclenché par le **compenser** forme dans le bloc intercepter l’Exception.  
  
> [!NOTE]
>  Les transactions atomiques garantissent que les mises à jour partielles sont automatiquement annulées en cas d'échec lors de la mise à jour transactionnelle et que les effets de la transaction sont effacés (à l'exception des effets des appels .NET effectués dans la transaction).  
  
> [!NOTE]
>  Une transaction à long terme est considérée comme validée une fois que sa dernière instruction a été exécutée. Il n’existe aucune restauration automatique de l’état en cas d’abandon de la transaction. Vous pouvez obtenir cette restauration par programme grâce aux gestionnaires d'exception et de compensation illustrés dans cet exemple.  
  
 Dans le bloc catch, il en existe un **délai** forme définie sur dix secondes. Celle-ci retarde l'action de compensation. Il existe également un **compenser** forme qui lance l’action de compensation dans la transaction Upd_Backend.  
  
 Les événements suivants se produisent une fois que l'orchestration a reçu le message d'entrée :  
  
1.  L'assembly UpdateCrm met à jour une ligne dans la base de données Northwind.  
  
2.  L'assembly UpdateMailingList met à jour un enregistrement correspondant dans la base de données BTSCompensationSampleMailingList.  
  
3.  En cas d'erreur lors de la mise à jour de la base de données Northwind, une exception est générée et l'orchestration quitte le processus.  
  
4.  En cas d'erreur lors de la mise à jour de la base de données BTSCompensationSampleMailingList, une exception est générée et la réécriture des données client d'origine dans la base de données Northwind intervient après un délai de dix secondes.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Orchestrations\Compensation\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Fichier de commandes utilisé pour désinstaller l'exemple.|  
|CompensationOrchestration.btproj|Projet d'orchestration.|  
|CompensationSample.sln|Exemple de solution.|  
|CompensationSampleBinding.xml|Données de liaison pour l'orchestration (utilisées lors de l'installation).|  
|ContactInfo.xsd|Schéma de message des coordonnées.|  
|ContactInfo.xsx|Fichier de disposition du concepteur d'orchestration.|  
|CreateSQLDataStore.sql|Script SQL qui permet de créer et renseigner l'exemple de base de données.|  
|CrmSchema.xsd|Schéma de message de la mise à jour CRM.|  
|MailingListSchema.xsd|Schéma de message de la mise à jour de la liste de distribution.|  
|RemoveVirDir.vbs|Script Microsoft Visual Basic Scripting Edition (VBScript) qui permet de supprimer les répertoires virtuels et physiques du service Web (utilisés lors de la désinstallation).|  
|Request2Crm.btm|Mappage de message qui permet de convertir la demande (coordonnées) en message de mise à jour CRM.|  
|Request2MailingList.btm|Mappage de message qui permet de convertir la demande (coordonnées) en message de liste de distribution.|  
|Setup.bat|Fichier de commandes qui permet d'installer l'exemple.|  
|UpdateContact.odx|Fichier d'orchestration.|  
|UpdateRequest2UpdateResponse.btm|Mappage de message qui permet de convertir la demande (coordonnées) en message de réponse.|  
|UpdateResponse.xsd|Schéma de message de réponse.|  
|InfoPath\Contact Info Update.xsn|Fichier Microsoft InfoPath utilisé pour envoyer les formulaires au service Web d'orchestration.|  
|UpdateCrm\AssemblyInfo.cs|Fichier de source d'informations de l'assembly UpdateCrm. (L'assembly UpdateCrm met à jour la base de données Northwind.)|  
|UpdateCrm\UpdateCrm.cs|Code source principal de l'assembly UpdateCrm.|  
|UpdateCrm\UpdateCRM.csproj|Fichier de projet UpdateCrm.|  
|UpdateMailingList\AssemblyInfo.cs|Fichier de source d'informations de l'assembly UpdateMailingList. (L'assembly UpdateMailingList met à jour l'exemple de base de données.)|  
|UpdateMailingList\UpdateMailingList.cs|Code source principal de l'assembly UpdateMailingList.|  
|UpdateMailingList\UpdateMailingList.csproj|Fichier de projet UpdateMailingList.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-compensation-sample"></a>Pour créer et initialiser l'exemple Compensation  
  
1.  Dans une fenêtre de commande [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Orchestrations\Compensation\  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   création et déploiement de l'exemple d'assembly.  
  
    -   Lors du lancement de l'Assistant Publication de services Web BizTalk, procédez manuellement comme suit :  
  
    1.  Sur le **Bienvenue dans l’Assistant de publication des Services Web BizTalk** , cliquez sur **suivant**.  
  
    2.  Sur le **créer un Service Web** page, sélectionnez **l’orchestration BizTalk de publier en tant que services web**, puis cliquez sur **suivant**.  
  
    3.  Sur le **BizTalk Assembly** page, recherchez et sélectionnez \< *exemples de chemin*\>\Orchestrations\Compensation\bin\Release\CompensationOrchestration.dll, puis cliquez sur **Suivant**.  
  
    4.  Sur le **Orchestrations et Ports** , cliquez sur **suivant**.  
  
    5.  Sur le **propriétés du Service Web** page **espace de noms cible du service web**, type **http://Microsoft.BizTalk.Samples.Compensation/**, puis cliquez sur **Suivant**.  
  
    6.  Sur le **projet de Service Web** page **emplacement**, type **http://localhost/CompensationOrchestrationWebServiceProxy**.  
  
    7.  Sélectionnez le **autorise l’accès anonyme au service web** case à cocher.  
  
    8.  Sélectionnez le **emplacement de réception BizTalk de créer dans l’application suivante** case à cocher.  
  
    9. Dans le **emplacement de réception BizTalk de créer dans l’application suivante** menu déroulant, sélectionnez **BizTalk Application 1** dans la liste déroulante, puis cliquez sur **suivant**.  
  
    10. Sur le **résumé du projet de Service Web** , cliquez sur **créer**.  
  
    11. Sur le **fin de l’Assistant de publication des Services Web BizTalk** , cliquez sur **Terminer**.  
  
3.  Le programme d'installation crée et lie les ports, crée la base de données principale pour l'exemple et ajoute les assemblys C# au GAC (Global Assembly Cache).  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Une fois l'exemple créé et initialisé, tenez compte des points suivants avant de l'exécuter :  
  
-   Si vous exécutez cet exemple sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)], vous devez créer un pool d'applications IIS et définir son identité sur un compte membre du groupe Windows Utilisateurs d'applications BizTalk. Vous devez également mettre à jour le répertoire virtuel du service Web d'orchestration afin qu'il soit exécuté dans ce pool d'applications.  
  
-   Ajoutez le compte ASPNET au groupe Utilisateurs d'hôtes BizTalk isolés.  
  
-   Accorder l’autorisation de db_owner du groupe utilisateurs de l’Application BizTalk à le **BTSCompensationSampleMailingList** et **Northwind** bases de données.  
  
-   Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n’est pas installé dans l’emplacement par défaut (lecteur : \Program Files\Microsoft BizTalk Server \<version\>\\), vous devez publier le formulaire Contact Info Update.xsn avant de l’utiliser. Pour ce faire, procédez comme suit.  
  
    #### <a name="to-publish-the-infopath-form"></a>Pour publier le formulaire InfoPath  
  
    1.  Dans Internet Explorer, sur le **outils** menu, cliquez sur **Options Internet**.  
  
    2.  Sur le **sécurité** , cliquez sur **Internet**, puis cliquez sur **niveau personnalisé**.  
  
    3.  Dans le **divers** section, vérifiez que le **accéder aux sources de données sur plusieurs domaines** paramètre est activé, puis cliquez sur **OK**. Ce paramètre est requis pour le code de script de la solution d'interface utilisateur InfoPath à exécuter.  
  
    4.  Dans l’Explorateur Windows, accédez à \< *exemples de chemin*\>\Orchestrations\Compensation\InfoPath, avec le bouton droit **Contact Info Update.xsn** puis cliquez sur  **Conception**.  
  
    5.  La solution de mise à jour des coordonnées InfoPath (Contact Info Update) est ouverte en mode Création.  
  
    6.  Dans l’application de la mise à jour des informations de Contact InfoPath, sur le **fichier** menu, cliquez sur **publier**.  
  
    7.  L'Assistant Publication s'affiche.  
  
    8.  Sélectionnez **dans un dossier partagé sur cet ordinateur ou sur un réseau** et publier la solution dans le chemin d’accès \< *exemples de chemin*\>\Orchestrations\Compensation\InfoPath\Contact Info Update.xsn.  
  
    9. Fermez InfoPath en mode Création.  
  
-   Vous êtes prêt à exécuter cet exemple.  
  
    #### <a name="to-run-the-compensation-sample"></a>Pour exécuter l'exemple Compensation  
  
    1.  Double-cliquez sur **Contact Info Update.xsn** pour l’ouvrir dans InfoPath.  
  
    2.  Renseignez le formulaire pour un compte existant dans les deux bases de données. Par exemple, utilisez l'ID de compte « ALFKI » de la table Customers dans la base de données Northwind.  
  
    3.  Sur le **fichier** menu, sélectionnez **Submit**, puis cliquez sur **Submit**.  
  
    4.  Le document de réponse doit apparaître dans le \< *exemples de chemin*\>\Orchestrations\Compensation\Out dossier et Northwind et les bases de données BTSCompensationSampleMailingList doivent être mis à jour avec les nouvelles données à partir du formulaire InfoPath.  
  
        > [!NOTE]
        >  Vous pouvez détacher la base de données BTSCompensationSampleMailingList ou la mettre hors connexion pour tester l'action de compensation effectuée par l'orchestration. Notez que l'enregistrement est d'abord mis à jour dans la base de données Northwind. Lorsque l'orchestration tente de mettre à jour la base de données BTSCompensationSampleMailingList par la suite, la mise à jour échoue car cette base de données est détachée. Une exception est donc générée et l'exécution de l'action de compensation en vue de la réécriture des données client d'origine dans la base de données Northwind intervient après un délai de dix secondes.  
  
        > [!NOTE]
        >  Vous risquez d'obtenir une erreur « Échec de la connexion pour l'utilisateur 'IIS APPPOOL\DefaultAppPool ». Cela est peut-être dû à un échec de la validation de l'accès au serveur basé sur les jetons. Pour corriger cette erreur, créez un pool d'applications et utilisez le compte d'administrateur dans ce pool.  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-compensation-sample"></a>Pour désinstaller l'exemple Compensation  
  
1.  Dans une fenêtre de commande [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Orchestrations\Compensation\  
  
2.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)