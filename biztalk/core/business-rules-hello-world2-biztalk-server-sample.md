---
title: "Exemple Hello World2 de règles d’entreprise (exemple BizTalk Server) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, business rules
- business rules, examples
ms.assetid: 2a88a2a0-8cb6-4373-8441-0ab04345a477
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eed1c0c83432417b53debcf523eeec91f85e5c2b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="business-rules-hello-world2-biztalk-server-sample"></a>Exemple Hello World2 de règles d’entreprise (exemple BizTalk Server)
L’exemple d’entreprise règles « Hello World2 » étend l’exemple de Business règles « Hello world1 » en montrant comment vers la version, publier et déployer l’ensemble pour le magasin de règles SQL partagé et l’exécution de la stratégie à l’aide de règles XML le **stratégie** objet fourni par l’infrastructure des règles d’entreprise. L'exemple illustre également les stratégies de mise à jour dynamiques en action.  
  
> [!NOTE]
>  Il est basé sur l'hypothèse que l'utilisateur a installé le service de mise à jour du moteur des règles et les composants des règles d'entreprise (situés sous le nœud « Logiciels supplémentaires ») durant l'installation du produit.  
  
> [!NOTE]
>  Vous utilisez **stratégie** objets pour intégrer le moteur de règles dans une application autonome. Le **stratégie** objet est l’abstraction gérés via la règle de plusieurs instances du moteur, les jeux sont extraits et instanciés à partir du magasin SQL partagé, et les stratégies mises à jour sont extraites et publiées à l’hébergement de règles application.  
  
 Pour plus d’informations de base sur l’ensemble défini et des exemples de règles faits créés par cet exemple, consultez [entreprise règles « Hello world1 »](../core/business-rules-hello-world1-biztalk-server-sample.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple crée un fichier exécutable qui effectue la séquence d'étapes suivante :  
  
1.  Appelle la méthode **CreateRuleset** pour générer l’ensemble de règles décrit dans la section Notes.  
  
2.  Appelle la méthode **SaveToFile** pour montrer l’enregistrement d’un ensemble de règles dans un fichier.  
  
3.  Appelle la méthode **LoadFromFile** pour montrer le chargement à partir d’un fichier.  
  
4.  Déploie l'ensemble de règles dans un magasin de règles SQL partagé.  
  
5.  Exécute l’ensemble à l’aide de règles une **stratégie** de l’objet et en utilisant le même ensemble d’exemples de faits utilisées dans l’entreprise règles « Hello world1 » d’exemple.  
  
6.  Temps de pause, ce qui vous permet de modifier la règle de définie le fichier **SampleRuleStore.xml** d’une manière spécifique.  
  
7.  Exécute l’ensemble à l’aide de règles une **stratégie** de l’objet, la règle modifiée maintenant définir et à nouveau avec le même jeu d’exemples de faits utilisées dans l’entreprise règles « Hello world1 » exemple.  
  
8.  Effectue un nettoyage en supprimant le fichier de l'ensemble de règles et les enregistrements de l'ensemble de règles déployé pour préparer les exécutions suivantes de l'exemple.  
  
> [!NOTE]
>  Pour obtenir des informations importantes sur tous les exemples dans ce SDK, consultez [exemples](../core/samples-in-the-sdk.md).  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès\>*\Business Rules\Business règles Hello World2\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld2.csproj, BusinessRulesHelloWorld2.sln|Projet, solution et fichiers associés pour la portion de cet exemple qui crée, enregistre, charge, déploie et exécute un ensemble de règles.|  
|HelloWorld2.cs|Les fichier Visual c# qui contient des méthodes servant à montrer la création d’une règle définir, l’enregistrement d’un ensemble de règles à un fichier, son chargement à partir d’un fichier de déploiement de la règle à un magasin de règles partagé Microsoft SQL Server, et ensuite la règle en cours d’exécution définies à l’aide un **stratégie**objet.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|SampleDocumentInstance.xml|Exemple de fichier d'entrée conforme au schéma défini dans le fichier SampleSchema.xsd.|  
|SampleSchema.xsd|Fichier de schéma qui définit un schéma unique avec un élément référencé par l'ensemble de règles créé dans le fichier Visual C# Class1.cs.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \HelloWorld2Library :<br /><br /> AssemblyInfo.cs, HelloWorld2Library.csproj, HelloWorld2Library.sln|Projet, solution et fichiers associés pour la portion de cet exemple qui fournit la classe définissant les objets référencés par l'ensemble de règles créé.|  
|Dans le dossier \HelloWorld2Library :<br /><br /> HelloWorld2LibraryClass.cs|Les fichiers Visual c# qui contient la propriété référencée dans le **IF** partie de la règle créée et la méthode qui peut être appelée dans le **puis** partie de la règle créée.|  
  
### <a name="to-build-and-initialize-the-business-rules-hello-world2-sample"></a>Pour créer et initialiser l'exemple de règles d'entreprise « Hello World2 »  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Business Rules\Business règles Hello World2\  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compilation et déploiement des projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple.  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
    > [!NOTE]
    >  Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
### <a name="to-run-the-business-rules-hello-world2-sample"></a>Pour exécuter l'exemple de règles d'entreprise « Hello World2 »  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     *\<Exemples de chemin d’accès\>*\Business Rules\Business règles Hello World2\bin\Debug\  
  
2.  Dans la fenêtre de commande, tapez le nom du fichier pour cet exemple (**BusinessRulesHelloWorld2.exe**), puis appuyez sur ENTRÉE.  
  
## <a name="hello-world2-output"></a>Sortie de l'exemple « Hello World2 »  
 Selon la nature de l’ensemble de règles créé, décrit dans la section commentaires du [entreprise règles « Hello world1 »](../core/business-rules-hello-world1-biztalk-server-sample.md), si vous exécutez cet exemple avec l’exemple d’entrée de fichier fourni SampleDocumentInstance.xml, ce qui a une valeur d’un (1) définie pour son **ID** élément, vous verrez la sortie suivante :  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Deploying the ruleset ...  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...  
Grabbing the policy ...  
Executing the policy...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
The major version of the policy was: 1  
The minor version of the policy was: 0  
Press the ENTER to continue after updating the policy...  
```  
  
> [!NOTE]
>  La sortie en gras est la sortie produite par l’exemple d’objet métier défini par les fichiers dans le **HelloWorld2Library** que la règle de définie les références de dossier. À ce stade, l'application reste en attente dans cet état.  
  
 La partie suivant de l'exécution de l'exemple implique l'utilisation de l'Éditeur de règles d'entreprise pour modifier ces dernières.  
  
#### <a name="to-use-the-business-rules-composer-to-change-the-business-rules"></a>Utiliser l'Éditeur de règles d'entreprise afin de modifier les règles d'entreprise  
  
1.  Pour ouvrir l’éditeur des règles d’entreprise, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Si une boîte de dialogue SQL Server sur l’ordinateur exécutant SQL Server, cliquez sur **OK** pour se connecter au magasin de règles.  
  
3.  Dans **l’Explorateur de stratégies**, ci-dessous la **SampleRuleSet** nœud, cliquez sur le noeud **Version 1.0 – Deployed**, puis cliquez sur **copie**.  
  
4.  Avec le bouton droit **SampleRuleSet**, puis cliquez sur **Coller (Version de stratégie)**.  
  
5.  Vous pouvez modifier la condition et l'action de la règle en fonction de vos besoins. Pour cette procédure, cliquez sur **rule1** dans **Version 1.1 (non enregistrée)**. Dans le volet droit, cliquez sur **Conditions**, puis cliquez sur **ajouter le NOT logique**. Ajout d’un **NOT logique** opération **n’est pas égal** pour le prédicat équivaut à utiliser une **égal** prédicat.  
  
6.  Cliquez sur le noeud **Version 1.1 (non enregistrée)**, puis cliquez sur **enregistrer**. Cliquez sur Nouveau, puis cliquez sur **publier**. Avec le bouton droit une troisième fois, puis cliquez sur **déployer**.  
  
7.  Dans la fenêtre de commande en pause vous demandant d'appuyer sur une touche pour continuer après la mise à jour de la stratégie, appuyez sur une touche.  
  
 La sortie (en supposant que vous ayez modifié la règle en ajoutant un Not logique) du fichier exécutable BusinessRulesHelloWorld2.exe continue comme suit :  
  
```  
Sleeping for 60 seconds (so that the deployed ruleset becomes effective) ...         
Grabbing the policy ...         
Executing the policy...         
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5         
The major version of the policy was: 1         
The minor version of the policy was: 1         
Press ENTER to continue after updating the policy...         
```  
  
 Notez la façon dont la sortie a changé :  
  
-   La ligne de sortie dans la méthode **MySampleMethod** ne s’imprime une fois maintenant, pour l’instance de la **MySampleBusinessObject** classe pour laquelle le **MyValue** propriété est égale à 1 , au lieu de la règle précédente imprimer lorsque la **MyValue** propriété n’est pas égale à 1.  
  
-   Le numéro de version mineure de la stratégie est désormais 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise (dossier d’exemples BizTalk Server)](../core/business-rules-biztalk-server-samples-folder.md)