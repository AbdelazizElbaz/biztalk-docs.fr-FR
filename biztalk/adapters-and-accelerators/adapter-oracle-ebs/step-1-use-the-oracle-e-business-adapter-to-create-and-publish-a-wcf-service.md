---
title: "Étape 1 : Utiliser l’adaptateur Oracle E-Business pour créer et publier un service WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cd76f6f-600f-4eb5-8eee-8f3604d0fef4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c03f11ad2849b3d46e9e489a1657aa043fb0e61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-use-the-oracle-e-business-adapter-to-create-and-publish-a-wcf-service"></a>Étape 1 : Utiliser l’adaptateur Oracle E-Business pour créer et publier un service WCF
![Étape 1 sur 4](../../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **Durée :** 15 minutes  
  
 **Objectif :** que vous pouvez utiliser la [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour générer un service WCF à partir d’artefacts Oracle E-Business Suite qui peuvent être hébergés dans un environnement d’hébergement telles que Internet Information Services (IIS) ou le Service d’Activation des processus Windows (WAS). Cette rubrique montre comment utiliser l’Assistant pour générer un fichier de service WCF.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d’exécuter l’Assistant, vous devez installer les éléments suivants :  
  
-   [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)]à l’aide la **Complete** option ou **personnalisé** option (et en choisissant **outils** au sein de cette option). Cette commande installe le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] modèle pour le [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)].  
  
-   [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]à partir de la [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)].  
  
 Pour plus d’informations sur ces conditions préalables, consultez le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] guide d’installation. Le guide d’installation est généralement installé sur \<lecteur d’installation > : \Program Files\Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]\Documents.  
  
> [!NOTE]
>  Vous devez également exécuter le script create_apps_artifacts.sql fourni avec l’exemple de Microsoft Office SharePoint Server pour créer le **MS_SAMPLE_EMPLOYEE** table d’interface dans le **bibliothèque d’objets Application**application. Cette table de l’interface est utilisée dans ce didacticiel.  
  

  
##  <a name="Create_Service"></a>Créer un Service WCF pour l’opération sur Oracle E-Business artefact  
 Cette section fournit les étapes pour créer un service WCF pour l’opération Select sur la Table d’Interface MS_SAMPLE employé.  
  
#### <a name="to-create-a-wcf-service-for-the-select-operation-on-the-mssample-employee-interface-table"></a>Pour créer un Service WCF pour l’opération Select sur la Table d’Interface MS_SAMPLE employé  
  
1.  Démarrer [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], puis créez un projet.  
  
2.  Dans le **nouveau projet** boîte de dialogue, à partir de la **types de projet** volet, sélectionnez **Visual C#**. À partir de la **modèles** volet, sélectionnez **Service d’adaptateur WCF**.  
  
     Également, dans le **types de projet** volet, développez **Visual C#**, puis sélectionnez **Web**. À partir de la **modèles** volet, sélectionnez **Service d’adaptateur WCF**.  
  
     ![Boîte de dialogue Nouveau projet](../../adapters-and-accelerators/adapter-oracle-ebs/media/01-new-project.gif "01_New_Project")  
  
    > [!NOTE]
    >  Si vous avez installé [!INCLUDE[btsVStudio2008](../../includes/btsvstudio2008-md.md)] avec le composant développement Web, le **Service d’adaptateur WCF** modèle est également disponible à partir de la **nouveau Site Web** option (**fichier**  >  **Nouveau** > **Site Web**).  
    >   
    >  Toutefois, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] prend uniquement en charge les sites Web qui sont créés sur le système de fichiers. Par conséquent, lors de la création d’un site Web dans la boîte de dialogue Nouveau Site Web, vous devez cliquer sur système de fichiers dans la liste d’emplacements.  
  
3.  Spécifiez un nom et l’emplacement de la solution, puis cliquez sur **OK**. WCF [!INCLUDE[afsvcdevwizshort](../../includes/afsvcdevwizshort-md.md)] démarre.  
  
4.  Dans la page d’accueil, cliquez sur **suivant**.  
  
5.  Dans la page Choisir les opérations, spécifiez une chaîne de connexion pour se connecter à Oracle E-Business Suite. Pour cela :  
  
    1.  Dans le **sélectionner une liaison** , cliquez sur **oracleEBSBinding**, puis cliquez sur **configurer**.  
  
    2.  Dans le **configurer l’adaptateur** boîte de dialogue, cliquez sur le **propriétés de liaison** onglet.  
  
        1.  Sous le **général** catégorie, pour le **ClientCredentialType** liaison de propriété, sélectionnez **EBusiness**.  
  
        2.  Sous le **OracleEBS** catégorie, spécifiez les valeurs appropriées pour le **OracleUserName**, **OraclePassword**, et **OracleEBSResponsibilityName** propriétés de liaison. Dans ce cas, vous devez fournir les informations d’identification de la base de données pour le **OracleUserName** et **OraclePassword** propriétés de liaison.  
  
        3.  Sous le **métadonnées** catégorie, pour le **EnableSafeTyping** liaison de propriété, sélectionnez **True**. Si vous récupérez des valeurs pour la colonne de date, nous vous recommandons de définir la **EnableSafeTyping** liaison de propriété **True** lors de la génération de métadonnées.  
  
    3.  Cliquez sur le **propriétés URI** onglet et spécifiez des valeurs pour les paramètres de connexion. Pour plus d’informations sur l’URI de connexion pour le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], consultez [créer l’URI de connexion Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/create-the-oracle-e-business-suite-connection-uri.md).  
  
    4.  Cliquez sur le **sécurité** onglet et dans le **type d’informations d’identification du Client** liste, sélectionnez **nom d’utilisateur**. Spécifiez un nom d’utilisateur Oracle E-Business Suite et le mot de passe pour se connecter à Oracle E-Business Suite valide.  
  
    5.  Cliquez sur **OK** pour fermer la boîte de dialogue Configurer l’adaptateur, puis cliquez sur **connexion**. Une fois que Visual Studio a réussi à établir une connexion avec Oracle E-Business Suite, l’état de connexion s’affiche en tant que **connecté**. Vous pouvez également voir les métadonnées d’Oracle E-Business Suite est affichée sur la page Choisir les opérations.  
  
6.  Dans la page Choisir les opérations, dans le **type de contrat Select** , cliquez sur **Client (Outbound operations)**.  
  
7.  Dans le **sélectionner une catégorie** zone, accédez à la table d’interface MS_SAMPLE_EMPLOYEE dans une application de bibliothèque d’objet de l’Application. Pour plus d’informations sur la navigation à un artefact dans l’adaptateur, consultez [Parcourir, rechercher et récupérer des métadonnées pour des opérations Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/browse-search-and-get-metadata-for-oracle-e-business-suite-operations.md).  
  
8.  Dans le **catégories et opérations disponibles** boîte, sélectionnez le **sélectionnez** opération, puis cliquez sur **ajouter**. L’opération de sélection est ajoutée à la **ajouté des catégories et opérations** boîte.  
  
     ![Ajout de l’opération Select](../../adapters-and-accelerators/adapter-oracle-ebs/media/02-msb-gui.gif "02_MSB_GUI")  
  
    > [!NOTE]
    >  Vous pouvez ajouter plus d’une opération pour chaque artefact. Vous pouvez également ajouter des opérations pour différents artefacts Oracle E-Business Suite. Par exemple, vous pouvez ajouter une opération pour une table d’interface et l’autre pour un programme simultané. En outre, vous pouvez rechercher des opérations spécifiques en spécifiant des caractères génériques dans les expressions de recherche. Pour plus d’informations sur les prise en charge des caractères spéciaux et les niveaux de nœud à partir duquel vous pouvez rechercher les opérations, consultez [recherche pour des opérations Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/search-for-oracle-e-business-suite-operations.md).  
  
9. Dans la page Choisir les opérations, cliquez sur **suivant**.  
  
10. Dans la page Configurer le Service et les comportements de point de terminaison, spécifier des valeurs pour configurer le comportement de service et de point de terminaison.  
  
    1.  Dans le **Configuration de comportement de Service** , spécifiez des valeurs pour les éléments suivants :  
  
        |Pour la propriété|Spécifiez la valeur|  
        |----------------------|-----------------------|  
        |EnableMetadataExchange|Affectez la valeur **True** pour créer un point de terminaison de métadonnées exchange. En définissant ce paramètre **True**, vous rendre les métadonnées de service disponible à l’aide de protocoles standardisés, tels que les demandes WS-MEX (Metadata Exchange) et HTTP/GET. Valeur par défaut est **False**.|  
        |IncludeExceptionDetailsinFault|Affectez la valeur **True** pour inclure des informations d’exception gérées dans le détail des erreurs SOAP retournées au client à des fins de débogage. Valeur par défaut est **False**.|  
        |Nom|Nom de la configuration de comportement de service. Pour ce didacticiel, tapez **customServiceBehavior**.|  
        |UseServiceCertificate|Spécifie si vous souhaitez utiliser le mode de sécurité de niveau message WCF. Valeur par défaut est **True**. Pour ce didacticiel, vous affectez la valeur **False**.|  
  
        > [!NOTE]
        >  Étant donné que nous n’utilisons pas les certificats de service pour ce didacticiel, vous n’avez pas besoin fournir des valeurs pour le **FindValue**, **StoreLocation**, **StoreName**et **X509FindType** propriétés. Pour plus d’informations sur les certificats et les propriétés associées, consultez « Propriétés X509ClientCertificateCredentialsElement » à [http://go.microsoft.com/fwlink/?LinkId=103771](http://go.microsoft.com/fwlink/?LinkId=103771).  
  
    2.  Dans le **Configuration de comportement de point de terminaison** , spécifiez des valeurs pour les éléments suivants :  
  
        |Pour la propriété|Spécifiez la valeur|  
        |----------------------|-----------------------|  
        |Type d’authentification|Pour Microsoft Office SharePoint Server utiliser le service WCF, vous devez définir en tant que **HTTPUserNamePassword**. Ainsi, les clients à spécifier le nom d’utilisateur et mot de passe dans le cadre de l’en-tête HTTP.|  
        |Nom|Spécifiez un nom pour la configuration de comportement de point de terminaison. Pour ce didacticiel, tapez **customEndpointBehavior**.|  
        |UsernameHeader|Nom de l’en-tête de nom d’utilisateur. Pour cet exemple, spécifiez **MyUserHeader**. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour HTTP et SOAP en-têtes personnalisés » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692). **Remarque :** vous devez spécifier une valeur pour cette propriété si le **Type d’authentification** a la valeur **HTTPUserNamePassword**. Si **Type d’authentification** a la valeur **automatique**, cette propriété est facultative.|  
        |PasswordHeader|Nom de l’en-tête de mot de passe. Pour cet exemple, spécifiez **MyPassHeader**. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour HTTP et SOAP en-têtes personnalisés » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692). **Remarque :** vous devez spécifier une valeur pour cette propriété si le **Type d’authentification** a la valeur **HTTPUserNamePassword**. Si **Type d’authentification** a la valeur **automatique**, cette propriété est facultative.|  
  
     L’illustration suivante montre la page Configurer le Service et les comportements de point de terminaison avec les valeurs spécifiées.  
  
     ![Configurer la page de Service et comportements de point de terminaison](../../adapters-and-accelerators/adapter-oracle-ebs/media/03-service-and-endpoint-behavior.gif "03_Service_and_EndPoint_Behavior")  
  
11. Dans la page Configurer le Service et les comportements de point de terminaison, cliquez sur **suivant**.  
  
12. Dans la page Configurer la liaison de point de terminaison de Service et l’adresse, le **sélectionner un contrat pour configurer** affiche l’artefact (MS_SAMPLE_EMPLOYEE) que vous avez configuré. Le **opérations sous le contrat sélectionné** zone affiche la **sélectionnez** opération que vous avez sélectionné pour l’artefact sur la page Choisir les opérations.  
  
13. Dans le **configurer l’adresse et la liaison pour le contrat** , spécifiez des valeurs pour les éléments suivants :  
  
    |Pour la propriété|Spécifiez la valeur|  
    |----------------------|-----------------------|  
    |Configuration de la liaison|L’Assistant prend uniquement en charge la liaison HTTP de base. Par conséquent, le champ de configuration de liaison est automatiquement rempli pour *System.ServiceModel.Configuration.BasicHttpBindingElement*.<br /><br /> Cliquez sur le bouton de sélection **(...)**  pour modifier les propriétés pour la liaison HTTP. Pour utiliser un canal de communication sécurisé, vous devez toujours définir la **Mode** propriété **Transport**. L’Assistant définit la valeur par défaut pour le **Mode** propriété en tant que **Transport**.<br /><br /> Pour plus d’informations sur les autres liaisons exposé, consultez « Membres BasicHttpBindingElement » à [http://go.microsoft.com/fwlink/?LinkId=103773](http://go.microsoft.com/fwlink/?LinkId=103773).|  
    |Nom du point de terminaison|Spécifiez un nom de point de terminaison pour le contrat.|  
  
     Les autres champs de cette page sont remplis automatiquement selon les valeurs spécifiées dans les pages précédentes.  
  
     Cliquez sur **Appliquer**.  
  
    > [!NOTE]
    >  Si vous ne spécifiez pas de toutes les valeurs de cette page, les valeurs par défaut sont acceptés pour tous les contrats.  
  
     L’illustration suivante montre la page adresse avec les valeurs spécifiées et configurer la liaison de point de terminaison de Service.  
  
     ![Configurer la liaison de point de terminaison de Service et l’adresse](../../adapters-and-accelerators/adapter-oracle-ebs/media/04-service-endpoint-binding.gif "04_Service_Endpoint_Binding")  
  
14. Dans la page Configurer la liaison de point de terminaison de Service et l’adresse, cliquez sur **suivant**.  La page Résumé répertorie une arborescence de l’artefact Oracle E-Business Suite et de l’opération sélectionnée pour l’artefact.  
  
15. Passez en revue le résumé, puis cliquez sur **Terminer**.  
  
16. L’Assistant crée un service WCF et ajoute les fichiers suivants à la [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] projet :  
  
    1.  fichier .svc. Il s’agit du fichier de service WCF. L’Assistant génère un fichier pour chaque contrat.  
  
    2.  Fichier Web.config.  
  
    3.  Code de service (fichier .cs)  
  
##  <a name="cs"></a>Modifier le fichier .cs  
 Lorsque vous créez un service en dehors d’un artefact d’Oracle E-Business Suite à l’aide du [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] et son utilisation à partir du composant WebPart de liste de données métier dans Microsoft Office SharePoint Server, vous devez fournir la clause de filtre complète en commençant par la clause WHERE . Par exemple, si vous souhaitez rechercher un employé dont le nom est « John », vous devez fournir la clause de filtre suivante dans le composant WebPart de liste de données Business :  
  
```  
where NAME like ‘JOHN’  
```  
  
 Toutefois, si vous souhaitez que l’utilisateur à fournir uniquement le nom en tant qu’entrée pour la clause de filtre sans réellement mentionner la clause de filtre entier, vous pouvez ajouter un code dans le fichier .cs qui modifie la clause de filtre provenant du composant WebPart de liste de données métier dans Microsoft Office  SharePoint Server pour Oracle E-Business de passer au format de la clause WHERE.  
  
 Par exemple, dans le cas de ce didacticiel, si vous souhaitez que l’utilisateur à entrer un nom d’employé dans la liste données métier WebPart dans Microsoft Office SharePoint Server et de récupérer l’enregistrement pour cet employé, vous pouvez ajouter le code suivant dans le fichier .cs :  
  
```  
SelectResponse InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.Select(SelectRequest request)   
{  
     request.FILTER = "where NAME like '" + request.FILTER + "'"; // The code to avoid the users from specifying the WHERE clause in the filter from Business Data List Web Part.  
     return base.Channel.Select(request);  
}  
```  
  
##  <a name="Publish"></a>Publier le Service WCF  
 Assurez-vous que SSL est activé pour IIS. Pour obtenir des instructions sur l’activation de SSL pour IIS, consultez [http://go.microsoft.com/fwlink/?LinkId=197170](http://go.microsoft.com/fwlink/?LinkId=197170).  
  
 Pour publier le service WCF :  
  
1.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **publier**.  
  
2.  Dans le **publier le site Web** boîte de dialogue, spécifiez une URL pour le service WCF. Exemple :  
  
    ```  
    https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/  
    ```  
  
    > [!NOTE]
    >  Vous devez publier le service WCF dans un emplacement avec SSL activé. En d’autres termes, la valeur de la **emplacement cible** boîte doit commencer par « https:// ». Étant donné que les informations d’identification sont passées dans l’en-tête HTTP, l’Assistant configuré automatiquement le comportement de liaison de la carte pour utiliser « Transport » comme mode de sécurité, ce qui implique le chiffrement SSL. Vous pouvez bien sûr revenir en arrière et modifier le fichier web.config pour modifier la valeur de la  **\<mode de sécurité >** paramètre, mais à l’aide de SSL est toujours une meilleure option lorsque vous disposez des informations sensibles transmises en texte clair dans le En-tête HTTP.  
  
3.  À partir de la **copie** , cliquez sur **tous les fichiers projet**.  
  
4.  Cliquez sur **Publier**.  
  
5.  Vérifiez que le service WCF est publié avec succès.  
  
    1.  Démarrez la Console de gestion de Microsoft IIS. Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Accédez au nœud sur lequel vous avez publié le service. Pour le **MS_SAMPLE_EMPLOYEE** de service, accédez à **Internet Information Services** > **\<nom de l’ordinateur >**  >  **Sites Web** > **Site Web par défaut** > **MS_SAMPLE_EMPLOYEE**.  
  
    3.  Dans le volet droit, cliquez sur le fichier InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc, puis cliquez sur **Parcourir**.  
  
    4.  La page Web s’affiche avec l’URL pour l’extraction du WSDL. Vous pouvez décider de tester la récupération de métadonnées à l’aide du **svcutil** commande. Par exemple, la commande pour récupérer les métadonnées pour le service MS_SAMPLE_EMPLOYEE est la suivante :  
  
        ```  
        svcutil.exe https://<COMPUTER_NAME>:<PORT_NUMBER>/MS_SAMPLE_EMPLOYEE/InterfaceTables_FND_APPS_MS_SAMPLE_EMPLOYEE.svc?wsdl  
  
        ```  
  
## <a name="next-step"></a>Étape suivante  
 Pour créer un fichier de définition d’application pour l’artefact Oracle E-Business Suite, utilisez l’éditeur de définition de catalogue de données métier. Pour obtenir des instructions, consultez [étape 2 : créer un fichier de définition d’Application pour Oracle E-Business Suite artefacts](../../adapters-and-accelerators/adapter-oracle-ebs/step-2-create-an-application-definition-file-for-the-oracle-ebs-artifacts.md). Le fichier de définition d’application identifie où sont stockées les données LOB et le format dans lequel il est stocké.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Présenter les données à partir d’Oracle E-Business Suite sur un Site SharePoint](Tutorial:%20Present%20data%20from%20Oracle%20E-Business%20Suite%20on%20a%20SharePoint%20Site.md)