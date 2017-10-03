---
title: "Hello World1 de règles d’entreprise (exemple BizTalk Server) | Documents Microsoft"
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
ms.assetid: 0623ad20-96cc-430e-bb36-35431a5d17ee
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7231fd0d2aba7298127534eb43f1bf3c8c453b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-rules-hello-world1-biztalk-server-sample"></a>Hello World1 de règles d’entreprise (exemple BizTalk Server)
L'exemple de règles d'entreprise « Hello World1 » montre comment créer un ensemble de règles BizTalk, l'enregistrer dans un fichier (SampleRuleSet.xml), le charger et l'exécuter sur la base d'un exemple d'ensemble de faits. L'exemple d'ensemble de règles contient une seule règle impliquant un élément XML, ainsi que des objets .NET (propriétés et membres) en tant que termes dans la définition de règle.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple crée un fichier exécutable qui effectue la séquence d'étapes suivante :  
  
1.  Appelle la méthode **CreateRuleset** pour générer l’ensemble de règles décrit dans la section Notes.  
  
2.  Appelle la méthode **SaveToFile** pour montrer l’enregistrement d’un ensemble de règles dans un fichier.  
  
3.  Appelle la méthode **LoadFromFile** pour montrer le chargement à partir d’un fichier.  
  
4.  Crée les exemples de faits sur lesquels exécuter l'ensemble de règles.  
  
5.  Exécute l'ensemble de règles sur les exemples de faits et génère une sortie écran.  
  
6.  Marque un temps d'arrêt vous permettant d'examiner le fichier de l'ensemble de règles SampleRuleStore.xml.  
  
7.  Effectue un nettoyage en supprimant le fichier de l'ensemble de règles pour préparer les exécutions suivantes de l'exemple.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|App.ico, AssemblyInfo.cs, BusinessRulesHelloWorld1.csproj, BusinessRulesHelloWorld1.sln|Projet, solution et fichiers associés pour la portion de cet exemple qui crée, enregistre, charge et exécute un ensemble de règles.|  
|HelloWorld1.cs|Fichier Visual C# contenant les méthodes servant à montrer la création d'un ensemble de règles, son enregistrement dans un fichier et son chargement à partir d'un fichier. Il contient également un code environnant qui appelle ces méthodes, puis exécute l'ensemble de règles créé.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|SampleDocumentInstance.xml|Exemple de fichier d'entrée conforme au schéma défini dans le fichier SampleSchema.xsd.|  
|SampleSchema.xsd|Fichier de schéma qui définit un schéma unique avec un élément référencé par l'ensemble de règles créé dans le fichier Visual C# HelloWorld1.cs.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \MySampleLibrary :<br /><br /> AssemblyInfo.cs, MySampleLibrary.csproj, MySampleLibrary.sln|Projet, solution et fichiers associés pour la portion de cet exemple qui fournit la classe définissant les objets référencés par l'ensemble de règles créé.|  
|Dans le dossier \MySampleLibrary :<br /><br /> MySampleLibraryClass.cs|Les fichiers Visual c# qui contient la propriété référencée dans le **IF** partie de la règle créée et la méthode qui peut être appelée dans le **puis** partie de la règle créée.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Suivez la procédure suivante pour créer et initialiser l'exemple de règles d'entreprise « Hello World1 ».  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compile et déploie le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Microsoft utilisé dans l'exemple ;  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
    > [!NOTE]
    >  Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Pour exécuter l'exemple de règles d'entreprise « Hello World1 », procédez comme suit.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Business Rules\Business règles Hello World1\bin\Debug\  
  
2.  Dans la fenêtre Commande, tapez le nom du fichier exécutable pour cet exemple, (BusinessRulesHelloWorld1.exe), puis appuyez sur ENTREE.  
  
    > [!NOTE]
    >  Lors de l’exécution, cet exemple produit l’ensemble de règles de fichier SampleRuleStore.xml dans le **bin\Debug** dossier. Lorsque le fichier exécutable marque un arrêt en attendant que vous appuyiez sur ENTRÉE pour terminer, vous pouvez en examiner le contenu. N'oubliez pas de le fermer avant d'appuyer sur une touche pour terminer. Autrement, le fichier exécutable risque de ne pas pouvoir le supprimer en préparation des exécutions suivantes de l'exemple.  
  
 Selon la nature de l’ensemble de règles créé, si vous exécutez cet exemple avec l’exemple d’entrée de fichier fourni SampleDocumentInstance.xml, qui a la valeur un (1) définie pour sa **ID** élément, vous verrez la sortie suivante :  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 2 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
> [!NOTE]
>  La sortie en gras, à la fois dans le code précédent et dans le code qui suit, est la sortie produite par l’exemple d’objet métier défini par les fichiers dans le **MySampleLibrary** dossier, qui est référencé par l’ensemble de règles.  
  
 Si vous modifiez la valeur associée à la **ID** élément dans l’exemple de fichier d’entrée **SampleDocumentInstance.xml** à partir d’un (1) à deux (2), la sortie pourrait être modifié comme suit :  
  
```  
Creating a new ruleset ...  
Saving ruleset to SampleRuleStore.xml ...  
Loading ruleset ...  
Asserting objects ...  
Executing ...  
MySampleBusinessObject Class -- MySampleMethod executed for object 1 with parameter 5  
MySampleBusinessObject Class -- MySampleMethod executed for object 3 with parameter 5  
Press any key to finish ...  
```  
  
 Vous n’obtiendrez pas une ligne de sortie pour des objets de la **MySampleBusinessObject** classe qui ont leur **MyValue** propriété une valeur qui correspond à la valeur associée à le (pendantlaconstruction) **ID** élément dans l’exemple de fichier d’entrée SampleDocumentInstance.xml.  
  
## <a name="comments"></a>Commentaires  
 La règle créée par programme dans le **CreateRuleset()** méthode montre :  
  
 **IF**  
  
 **MySampleBusinessObject.MyValue** n’est pas égale à la valeur de la **ID** élément dans le document XML.  
  
 **PUIS**  
  
 **MySampleBusinessObject.MySampleMethod(int)** avec un paramètre de type entier dur codé à la constante cinq (5) dans ce cas. Cette méthode génère les lignes de sortie qui commencent **MySampleBusinessObject classe –-**.  
  
 Cette règle dépend de ce qui suit :  
  
-   A **MySampleBusinessObject** classe avec une propriété publique appelée **MyValue** et une méthode publique appelée **MySampleMethod** (qui prend un paramètre de type entier).  
  
-   Un schéma XML schema definition language (XSD) qui définit un document XML qui contient un **ID** élément.  
  
 Vous définissez les règles en termes de classes et de schémas, mais, en cours d'exécution, des instances d'objet des classes appropriées et des instances de document des schémas appropriés sont requises. Vous évaluez les règles par rapport à ces instances d'exécution (appelées faits). Dans cet exemple, les faits sont plusieurs instances de la **MySampleBusinessObject** objet construit avec des valeurs différentes pour leurs **MyValue** propriété et une seule instance XML du schéma défini qui contient une valeur pour le **ID** élément.  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise (dossier d’exemples BizTalk Server)](../core/business-rules-biztalk-server-samples-folder.md)