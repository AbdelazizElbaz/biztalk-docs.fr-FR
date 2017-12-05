---
title: HTTPSSO (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- SSO, examples
- SSO, HTTP adapters
- examples, HTTP adapters
- HTTP adapters, SSO
- examples, SSO
ms.assetid: 322360df-81d2-4a73-9512-bda9382351a2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41956d9e10cba87e0e1a1f44d49dd8ec8b6039bc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="httpsso-biztalk-server-sample"></a>HTTPSSO (exemple BizTalk Server)
L'exemple HTTPSSO montre comment utiliser la fonction d'authentification unique de l'entreprise (SSO) avec l'adaptateur HTTP Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
> [!NOTE]
>  Cet exemple n'est pas pris en charge sur les systèmes d'exploitation 64 bits.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple illustre un scénario de bout en bout qui utilise SSO et les adaptateurs d'envoi et de réception HTTP BizTalk pour simuler la manière dont SSO permet à un utilisateur d'éviter de fournir des informations d'identification supplémentaires pour se connecter aux systèmes non Microsoft Windows une fois que Windows les a authentifiées.  
  
 L'exemple utilise également les modules d'administration et de mappage de SSO pour créer des mappages d'applications associées et de SSO à l'aide de la DLL du client Interop de SSO.  
  
 L'exemple montre l'utilisation de SSO en implémentant les aspects suivants d'un scénario de bout en bout :  
  
-   Interface utilisateur, représentée par un répertoire virtuel Microsoft Internet Information Services (IIS) configuré pour utiliser l'authentification intégrée Windows.  
  
-   Système principal, représenté par un répertoire virtuel IIS configuré pour utiliser l'authentification de base.  
  
-   Base de données principale, représentée par l'exemple de base de données SQL Northwind.  
  
 Cet exemple suppose que vous avez installé [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SSO. Vous devez disposer des privilèges d’administrateur pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], IIS, SSO et COM + sur Windows XP Professionnel. Vous devez également être membre des groupes Windows Administrateurs SSO, Administrateurs BizTalk Server et Utilisateurs d'hôtes BizTalk isolés.  
  
 L'utilisation efficace de cet exemple suppose que vous maîtrisiez suffisamment SSO et l'adaptateur HTTP BizTalk. Par exemple, vous devez savoir ce qu'est une application associée dans le contexte de SSO. Pour plus d’informations sur ces sujets, consultez [à l’aide de l’authentification unique](../core/using-sso.md). Consultez également [adaptateur HTTP](../core/http-adapter.md).  
  
 Après avoir terminé la configuration, cet exemple fonctionne comme suit :  
  
1.  Lorsque vous cliquez sur **Terminer** dans l’Assistant qui comprend l’interface utilisateur pour cet exemple, une instance d’Internet Explorer démarre et transmet l’URL de la DLL de réception HTTP BizTalk.  
  
2.  BizTalk Server, à l'aide de SSO, transfère efficacement la requête HTTP au fichier EmployeeData.aspx dans un répertoire virtuel IIS configuré avec l'authentification de base. Ce fichier ASPX simule le point d'entrée dans un système principal non Windows. Comme vous utilisez SSO, la requête HTTP inclut les informations d'identification configurées qui simulent un compte de connexion au système principal simulé.  
  
3.  Le fichier ASPX accède à une version modifiée de l'exemple de base de données SQL Northwind pour extraire les données employé correspondant aux informations d'identification du système principal simulé.  
  
4.  Le fichier ASPX renvoie les données employé extraites dans une réponse HTTP.  
  
5.  BizTalk Server route la réponse HTTP vers Internet Explorer qui affiche les données employé renvoyées à l'utilisateur.  
  
 Si vous contournez BizTalk Server et SSO et accédez directement au fichier EmployeeData.aspx, une boîte de dialogue Windows vous demande vos informations d'identification.  
  
 Pour voir un exemple qui montre comment utiliser l’utilitaire de ligne de commande ssomanage.exe pour configurer l’authentification unique, telles que la création d’applications associées et des mappages utilisateur, [gérer (exemple BizTalk Server)](../core/manage-biztalk-server-sample.md).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\SSO\HTTPSSO\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|AssemblyInfo.cs, SsoSample.csproj|Projet et fichiers associés pour cet exemple HTTP SSO.|  
|SsoSample.cs|Fichier source Microsoft Visual C# de niveau supérieur pour l'application graphique HTTP SSO qui constitue la grande partie de cet exemple. Ce fichier contient le code de configuration de l’authentification unique, dans une classe nommée **SsoConfigurator** qui est finalement le point de cet exemple.|  
|Dans le dossier \Scripts :<br /><br /> EmployeeData.aspx|Utilisé pour accéder à la base de données principale et l'interroger (dans ce cas, la base de données SQL Northwind) lorsqu'un employé établit une demande d'affichage de ses données personnelles, directement ou à l'aide de SSO.|  
|Dans le dossier \Scripts :<br /><br /> ValidateUser.aspx|Simple test pour valider un utilisateur et signaler si cet utilisateur est validé, directement ou à l'aide de SSO.|  
|Dans le dossier \UI :<br /><br /> AddApplication.cs, AddApplication.resx, AddMapping.cs, AddMapping.resx, App.ico, BtsPage.cs, BtsPage.resx, ExecutePage.cs, ExecutePage.resx, FinishPage.cs, FinishPage.resx, IisPage.cs, IisPage.resx, InfoPage.cs, InfoPage.resx, PageBase.cs, PageBase.resx, SsoPage.cs, SsoPage.resx, SsoSampleWizard.cs, SsoSampleWizard.resx, WelcomePage.cs, WelcomePage.resx, WorkPage.cs, WorkPage.resx|Fichiers sources Visual C# auxiliaires et leurs fichiers de ressources XML associés pour l'application graphique HTTP SSO qui constitue la grande partie de cet exemple.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-httpsso-sample"></a>Pour créer et initialiser l'exemple HTTPSSO  
  
1.  Créez un compte Windows local que Microsoft Internet Information Services (IIS) peut utiliser pour l'authentification de base. SSO mappe le compte de domaine Windows à ce compte Windows local. Par exemple, utilisez votre nom de famille pour créer un compte Windows local.  
  
    > [!NOTE]
    >  Si vous exécutez sur un contrôleur de domaine, vous pouvez créer des comptes de domaine et mapper votre compte de domaine connecté à ce compte.  
  
2.  À l’aide de Microsoft SQL Server Enterprise Manager, ouvrez le **employés** de table dans la base de données Northwind, puis ajoutez une ligne correspondant au compte Windows local que vous venez de créer, y compris les exemples de données pour les différentes colonnes. La valeur que vous ajoutez à la colonne LastName de la table Employés doit être la même que le nom d'utilisateur du compte Windows local que vous avez ajouté à l'étape 1.  
  
3.  Assurez-vous que le compte ASP.NET (ASPNET) a un accès en lecture à la base de données Northwind.  
  
4.  Ouvrez le fichier de projet SsoSample.csproj à l'aide de Visual Studio.  
  
5.  Dans le menu **Générer** , cliquez sur **Générer la solution**.  
  
    > [!NOTE]
    >  Vous pouvez être invité à enregistrer un fichier de solution avant de procéder à la génération.  
  
     Si vous ne trouvez pas les références d'assembly BizTalk suivantes pour le projet, supprimez-les et ajoutez-les de nouveau à partir des emplacements indiqués et répétez la génération :  
  
    -   **Microsoft.BizTalk.ExplorerOM**. Par défaut, le fichier Microsoft.BizTalk.ExplorerOM.dll se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]outils de développement\\.  
  
    -   **Microsoft.BizTalk.SSOClient.Interop**. Par défaut, le fichier Microsoft.BizTalk.Interop.SSOClient.dll se trouve dans le dossier \< *ProgramFiles*\>\Common Files\Enterprise Single Sign-On\\.  
  
     Cette opération génère le fichier exécutable SsoSample.exe dans le dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\SSO\HTTPSSO\bin\Debug\  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
> [!NOTE]
>  Si vous exécutez cet exemple sur IIS 6.0 en mode d'isolation des processus de travail, les pools d'application sont créés pour les deux répertoires virtuels. Vous devez configurer manuellement l'identité de ces deux pools d'applications dans votre compte Windows (vous pouvez configurer l'identité dans le Gestionnaire des services Internet).  
  
#### <a name="to-run-the-httpsso-sample"></a>Pour exécuter l'exemple HTTPSSO  
  
1.  Exécutez le fichier exécutable SsoSample.exe, qui se trouve dans le dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\SSO\HTTPSSO\bin\Debug\  
  
     L'Assistant pour cet exemple s'ouvre.  
  
2.  Sur la page d’accueil, acceptez le paramètre par défaut pour la configuration IIS, SSO et BizTalk, puis cliquez sur **suivant**.  
  
3.  Dans la page de Configuration IIS, acceptez les paramètres par défaut pour les deux répertoires virtuels IIS vous souhaitez créer, puis cliquez sur **suivant**.  
  
4.  Dans la page Configuration SSO, acceptez les paramètres par défaut de l’application associée, qui est accessible à l’aide de la **ajouter application** bouton.  
  
5.  Dans la page Configuration SSO, acceptez la plupart des paramètres par défaut pour les mappages utilisateur, accessible à l’aide de la **Ajouter mappage** bouton. Indiquez des valeurs pour les deux paramètres suivants en fonction du compte Windows local que vous avez ajouté lors de la génération et l'initialisation de cet exemple.  
  
    |Paramètre|Valeur|  
    |-------------|-----------|  
    |Nom d’utilisateur externe|Défini sur le nom de compte d'utilisateur Windows local ajouté.|  
    |Mot de passe utilisateur externe|Défini sur le mot de passe du compte d'utilisateur Windows local ajouté.|  
  
6.  Dans la page Configuration de l’authentification unique, cliquez sur **suivant**.  
  
7.  Dans la page de Configuration de BizTalk, acceptez les paramètres par défaut pour l’envoi et ports de réception et ainsi de suite, puis cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Vous pouvez modifier le paramètre de port d’envoi par défaut à partir de **EmployeeData.aspx** à **ValidateUser.aspx** si vous souhaitez voir la validation utilisateur plutôt que des exemples de données extraites à partir de la table employés de la Base de données SQL Northwinds. Cette modification change la nature de la sortie affichée dans le navigateur après avoir cliqué sur **Terminer** à l’étape 9.  
  
8.  Consultez les messages d'état correspondant à la configuration IIS, SSO et BizTalk en cours d'exécution. Vous pouvez trouver le code exécuté durant cette phase dans le **IisConfigurator**, **SsoConfigurator**, et **BtsConfigurator** classes définies dans le fichier SsoSample.cs. Une fois la configuration terminée, cliquez sur **suivant**.  
  
9. Dans la dernière page de l’Assistant, acceptez les paramètres par défaut **démarrer le navigateur à** (case à cocher et une zone de texte avec l’URL http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/>), puis cliquez sur **Terminer**.  
  
     Une instance d'Internet Explorer s'ouvre et affiche les exemples de données employé que vous avez ajoutés à la table Employés de la base de données SQL Northwind.  
  
 Pour comparer, vous pouvez contourner BizTalk et SSO et accéder directement à l'un des fichiers ASPX :  
  
-   http://localhost/SsoSampleServerApplication/ValidateUser.aspx  
  
-   http://localhost/SsoSampleServerApplication/EmployeeData.aspx  
  
 Dans les deux cas, comme vous contournez BizTalk et SSO, vous êtes invité par IIS à entrer vos informations d'authentification (utilisez les informations du compte Windows local que vous avez créé).  
  
## <a name="comments"></a>Commentaires  
 L'Assistant SsoSample.exe configure deux répertoires virtuels IIS :  
  
-   Le premier répertoire virtuel est configuré avec l'authentification intégrée Windows et correspond à l'extension ISAPI de l'emplacement de réception HTTP BizTalk. Il doit être associé au fichier .dll BTSHTTPReceive.dll situé dans le dossier suivant :  
  
     \<*Le chemin d’installation*\>\HttpReceive  
  
-   Le second répertoire virtuel est configuré avec l'authentification de base et simule un système principal qui accepte un ID et mot de passe utilisateur pour authentifier l'utilisateur. Il doit être associé à l'un ou l'autre des fichiers ASPX, ValidateUser.aspx ou EmployeeData.aspx, situés dans le dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\SSO\HTTPSSO\Scripts  
  
 Vous pouvez utiliser l'Assistant SsoSample.exe configurer une ou plusieurs applications associées. Pour chacune de ces applications associées, vous pouvez créer un ou plusieurs mappages utilisateur. Chacun de ces mappages utilisateur mappe un compte d'utilisateur Windows à un compte que vous utilisez pour accéder à un système principal spécifique. Dans cet exemple, ce compte est un compte Windows local que vous utilisez pour l'authentification avec le second répertoire virtuel IIS qui simule un système principal original.  
  
 Pour exécuter de nouveau cet exemple, vous avez le choix entre plusieurs solutions :  
  
-   Accédez directement à l'URL suivante dans Internet Explorer :  
  
     http://localhost/SsoSampleBizTalkHttpReceive/BTSHttpReceive.dll?<message/>  
  
-   Exécutez de nouveau l'Assistant mais désactivez toutes les cases à cocher de configuration dans la première page.  
  
-   Exécutez de nouveau l'Assistant, laissez les cases à cocher de configuration activées dans la première page mais configurez de manière soigneuse et appropriée des éléments BizTalk supplémentaires, des applications associées, etc., afin que des erreurs de configuration ne se produisent pas.  
  
 Pour le nettoyage à partir de cet exemple, utilisez la procédure suivante.  
  
#### <a name="to-clean-up-from-this-sample"></a>Pour nettoyer à partir de cet exemple  
  
1.  Si nécessaire, inversez la configuration manuelle que vous avez effectuée, telle que la suppression du compte Windows local.  
  
2.  Supprimez les applications IIS qui correspondent aux répertoires virtuels, puis supprimez les répertoires virtuels IIS créés par cet exemple.  
  
3.  À l'aide de la console Administration de BizTalk, désinscrivez, puis supprimez le port d'envoi associé à cet exemple. Ensuite, supprimez le port de réception (et son emplacement de réception) associé à cet exemple.  
  
4.  Utilisez l’application Ssomanage (située dans \Program Files\Enterprise Single Sign-On\\) pour supprimer l’application SSO pour cet exemple :  
  
    ```  
    Ssomanage –deleteapp SsoSampleApplication  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification unique (dossier d’exemples BizTalk Server)](../core/sso-biztalk-server-samples-folder.md)