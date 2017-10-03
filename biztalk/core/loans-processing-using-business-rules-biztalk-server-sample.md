---
title: "À l’aide de règles d’entreprise (exemple BizTalk Server) de traitement de prêts | Documents Microsoft"
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
ms.assetid: 3e1c80c6-adc1-4a0f-83fd-409ce1b8f21f
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c51f0ff13b06bd57ccdd52ec6e35fdd7e0acf839
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="loans-processing-using-business-rules-biztalk-server-sample"></a>À l’aide des règles d’entreprise (exemple BizTalk Server) de traitement des prêts
L'exemple Traitement de prêts à l'aide de règles d'entreprise montre comment utiliser un ensemble de règles gérées à l'intérieur d'une orchestration, ainsi qu'une combinaison d'entrées appelées faits, pour calculer les paramètres de certains champs à l'intérieur d'un document en cours de traitement. Les faits peuvent être le résultat de l'appel d'un assembly basé sur .NET, les valeurs extraites du code XML du message ou les données extraites d'une base de données. L'exemple montre également comment modifier les règles à tout moment, qui affectent les calculs suivants sans nécessiter de redéploiement.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre ces fonctionnalités dans le contexte d’un scénario de traitement de prêt simplifiée. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]orchestration récupère et traite une demande de prêt, également appelé un cas de prêt, dans le format de message XML. Cette orchestration utilise le Moteur de règles d'entreprises pour évaluer des messages entrants en fonction de règles, modifier certaines messages avec le résultat de l'application des règles, puis les écrire sous forme de fichiers dans un dossier de sortie.  
  
 Basées sur des faits à partir de plusieurs sources, notamment le message en cours de traitement, cet exemple définit le **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**et  **ResidencyStatus** éléments du message en cours de traitement.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*> \Business Rules\Loans le traitement à l’aide de Business Rules\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Case.xsd|Fichier de schéma pour les demandes de prêt entrantes, également appelées cas de prêt.|  
|Cleanup.bat|Utilisé pour annuler le déploiement des assemblys et les supprimer du Global Assembly Cache (GAC). Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|Create_CustInfo_Table.sql|Script SQL pour la création de la table CustInfo dans la base de données exemple SQL Northwind.|  
|LoanProcessorBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|LoansProcessor.btproj, LoansProcessor.sln|Fichiers de projet et de solution BizTalk pour cet exemple.|  
|My Sample Service.odx|Orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour cet exemple.|  
|sampleLoan.xml|Exemple de fichier d'entrée, avec des valeurs vides pour les quatre éléments d'état à la fin de la structure XML dans le fichier.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \CreateRules :<br /><br /> App.ico, AssemblyInfo.cs, Case.xsd, CreateLoanProcessingPolicy.csproj, CreateLoanProcessingPolicy.sln, WriteToBRL.cs|Project, solution, source et fichiers associés Visual C# utilisés pour créer l'application qui crée les règles par programme. Pour obtenir des exemples de création d'ensembles de règles par programme, consultez le fichier source WriteToBRL.cs.|  
|Dans le dossier \myFactRetriever :<br /><br /> AssemblyInfo.cs<br /><br /> FactRetrieverForLoansProcessing.cs<br /><br /> myFactRetriever.csproj<br /><br /> myFactRetriever.sln|Project, solution, source et fichiers associés Visual C# utilisés pour créer un assembly permettant d'extraire des informations de la table CustInfo ajoutée précédemment à l'exemple de base de données SQL Server Northwind.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-loans-processing-using-business-rules-sample"></a>Création et initialisation de l'exemple Traitement de prêts à l'aide de règles d'entreprise  
  
1.  Vérifiez que vous disposez de la base de données Northwind sur votre ordinateur.  
  
    > [!IMPORTANT]
    >  Pour exécuter cet exemple, vous devez disposer d'une base de données nommée Northwind. [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]et [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] ne sont pas fournis avec la base de données Northwind. Pour créer la base de données Northwind, téléchargez le fichier d’installation [http://go.microsoft.com/fwlink/?LinkId=196020](http://go.microsoft.com/fwlink/?LinkId=196020), suivez les instructions.  
  
2.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \Business Rules\Loans le traitement à l’aide de règles d’entreprise  
  
3.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   nettoie le GAC pour éliminer les données résiduelles d'exécutions précédentes de cet exemple ;  
  
    -   compile et déploie le programme extracteur de faits, myFactRetreiever.dll ;  
  
    -   ajoute, à l'aide du fichier de script SQL Create_CustInfo_Table.sql, une table nommée CustInfo à la base de données SQL exemple Northwind ;  
  
    -   nettoie le magasin de règles SQL partagé pour éliminer les données résiduelles d'exécutions précédentes de cet exemple ;  
  
    -   crée, publie et déploie la dernière version (1.0) de l'ensemble de règles de traitement des prêts  
  
        > [!NOTE]
        >  (l'outil Éditeur des règles d'entreprise fourni avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'examiner les règles définies par programme) ;  
  
    -   crée les dossiers d'entrée (in) et de sortie (out) pour cet exemple ;  
  
    -   compile et déploie les projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] restants pour cet exemple, notamment le projet BizTalk contenant l'orchestration que vous utilisez pour coordonner l'exemple ;  
  
    -   crée et lie l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que les ports d'envoi et de réception :  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et liaison des ports :  
        >   
        >  `Warning: Receive handler not specified for receive location "LoansProcessor_1.0.0.0_LoansProcessor.My_Sample_Service_Incoming_ReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "LoansProcessor.My_Sample_Service"; updating with first available host.`  
        >   
        >  Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
    -   inscrit et démarre l'orchestration.  
  
> [!NOTE]
>  Si votre nom d'hôte BizTalk n'est pas BizTalkServerApplication, modifiez les fichiers Setup.bat et LoanProcessorBinding.xml de façon à ce qu'ils reflètent le nom d'hôte approprié.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
> [!NOTE]
>  Si vous choisissez Ouvrir et générer les projets dans cet exemple sans exécuter le fichier Setup.bat, vous devez tout d’abord créer une paire de clés de nom fort à l’aide du Kit de développement .NET Framework Strong Name utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
> [!NOTE]
>  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-loans-processing-using-business-rules-sample"></a>Pour exécuter l'exemple Traitement de prêts à l'aide de règles d'entreprise  
  
1.  Collez une copie du fichier sampleLoan.xml dans le **\In** dossier.  
  
2.  Observez le fichier .xml créé dans le dossier **hors**. Il contient le message XML d’entrée avec les données ajoutées aux éléments de quatre état suivants à la fin de la structure XML : **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, et **ResidencyStatus**.  
  
 L'outil Éditeur des règles d'entreprise permet de modifier les règles de l'ensemble de règles, puis de les redéployer.  
  
#### <a name="to-use-the-business-rule-composer-tool-to-change-one-or-more-of-the-rules-in-a-rule-set"></a>Pour utiliser l'outil Éditeur des règles d'entreprise pour modifier une ou plusieurs règles d'un ensemble de règles  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Éditeur des règles d’entreprise**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur. Pour ce faire, cliquez sur l’application, puis **exécuter en tant qu’administrateur**.  
  
2.  Dans le **SQL Server** boîte de dialogue, cliquez sur **OK** pour se connecter au magasin de règles.  
  
3.  Dans **l’Explorateur de stratégies**, sous le nœud **LoanProcessing**, avec le bouton droit le **Version 1.0 – Deployed** nœud, puis cliquez sur **copie**.  
  
4.  Avec le bouton droit **LoanProcessing**, puis cliquez sur **coller**.  
  
5.  Modifiez toute règle ou l’action d’une manière qui génère des valeurs différentes pour le **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, et  **ResidencyStatus** éléments. Veillez à modifier également la valeur de la partie négation (essentiellement, le **Else** clause) de toute règle que vous souhaitez modifier.  
  
     Le tableau suivant présente l'ensemble de règles utilisées par cet exemple. Sauf mention contraire, les faits proviennent du message XML entrant. La chaîne (db) indique une base de données comme source d'un fait.  
  
    |Numéro de règle|Nom de règle| Description|  
    |-----------------|---------------|-----------------|  
    |1|Règle d'état de revenu|IF **BasicSalary** + **OtherIncome** > 0<br /><br /> PUIS **IncomeStatus** = **valide**|  
    |2|Règle d'état d'engagements|IF **ID** == **ID (db)**<br /><br /> AND<br /><br /> IF **CreditCardBalance (db)** > 500<br /><br /> PUIS **CommitmentsStatus** =<br /><br /> « Calculer engagements »|  
    |3|Employment Status Rule|IF **EmploymentType &#124; TimeInMonths** > 18<br /><br /> PUIS **EmploymentStatus** = **valide**|  
    |4|Residency Status Rule|IF **PlaceOfResidence &#124; TimeInMonths** > 18<br /><br /> PUIS **ResidencyStatus** = **valide**|  
    |!1, !2, !3, !4|Règles de négation|Les conditions qui sont une logique **pas** de la condition correspondante décrite dans les règles 1 et 4. Actions qui en résultent sont une modification dans la chaîne qui est définie.|  
  
6.  Cliquez sur le **Version 1.1 (non enregistrée)** nœud, puis cliquez sur **enregistrer**.  
  
7.  Cliquez sur le **Version 1.1** nœud, puis cliquez sur **publier**.  
  
8.  Cliquez sur le **Version 1.1** nœud, puis cliquez sur **déployer**.  
  
9. Patientez 60 secondes, le temps que les modifications se propagent au magasin de règles SQL Server partagé.  
  
10. Collez une copie du fichier sampleLoan.xml dans le dossier **dans**.  
  
11. Observez le fichier .xml créé dans le dossier **hors**. Il contient le message XML d’entrée avec les données ajoutées aux éléments de quatre état suivants à la fin de la structure XML : **IncomeStatus**, **CommitmentsStatus**, **EmploymentStatus**, et **ResidencyStatus**. Les données ajoutées à ces éléments diffèrent ou non de l'exécution précédente, en fonction de la nature des modifications apportées à l'étape 5 de cette procédure.  
  
## <a name="comments"></a>Commentaires  
 Si vous voulez afficher les informations de suivi pour cet exemple, vous devez annuler le déploiement, puis redéployer l'ensemble de règles approprié (Traitement de prêts) à l'aide de l'Assistant Déploiement du moteur de règles d'entreprise.  
  
 Cet exemple montre comment utiliser des règles d'entreprise pour appliquer des stratégies commerciales sous la forme de règles au sein d'une orchestration. Elle montre également comment modifier les stratégies et faire en sorte que cette modification se reflète de façon dynamique dans l'orchestration sans devoir recompiler ni redéployer la solution d'orchestration.  
  
 Les cas de prêt entrés pour cet exemple sont des messages XML qui présentent la structure suivante :  
  
```  
    Name  
    ID  
    Income  
        BasicSalary  
        OtherIncome  
    EmploymentType  
        TimeInMonths  
    PlaceOfResidence  
        TimeInMonths  
    CommitmentsStatus  
    IncomeStatus  
    EmploymentStatus  
    ResidencyStatus  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Règles d’entreprise (dossier d’exemples BizTalk Server)](../core/business-rules-biztalk-server-samples-folder.md)