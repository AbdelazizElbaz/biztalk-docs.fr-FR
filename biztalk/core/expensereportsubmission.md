---
title: ExpenseReportSubmission | Documents Microsoft
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
ms.assetid: d0bacab3-7092-44b8-a1c6-6f574a2db8bd
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c450e2e39f2498722f9eb8d09430294927cb05f8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="expensereportsubmission"></a>ExpenseReportSubmission
L'exemple ExpenseReportSubmission montre comment soumettre un document à une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une application client riche comme Microsoft Excel.  
  
 Les applications client riche vous permettent d'effectuer un certain nombre d'actions, telles que des validations et des calculs préliminaires, sur le client. Cela contribue à réduire au minimum les interactions avec le serveur principal, ce qui peut être utile lorsque seules des connections à faible bande passante sont disponibles.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez vous assurer que votre environnement de développement est configuré et activé pour fonctionner avec les services Web [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [activation des Services Web](../core/enabling-web-services.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment vous pouvez soumettre une note de frais à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directement à partir d'Excel, en respectant les étapes suivantes :  
  
1.  L'utilisateur effectue les étapes manuelles de l'exemple fournies dans le tableur Excel.  
  
2.  Le code macro du tableur convertit les données de tableur au format Extensible Markup Language (XML), et soumet le message XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en utilisant une connection HTTP.  
  
3.  L'ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère le message XML de note de frais, valide son format en utilisant le schéma fourni, puis le range dans un dossier différent.  
  
4.  En pratique, au delà de cet exemple, une autre application, comme un système planification des ressources de l'entreprise (ERP), récupère ensuite le fichier de tableur pour un traitement ultérieur.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\AdaptersUsage\ExpenseReportSubmission\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.|  
|ExpenseReport.15.3.xls|Tableur Excel avec la mise en page de la note de frais, les macros associées, et des boutons pour appeler les macros.|  
|MessageExample.xml|Exemple de note de frais au format XML.|  
|Setup.bat|Crée et initialise l'exemple.|  
|Dans le dossier \BTSExpenseDemo :<br /><br /> AssemblyInfo.cs,<br /><br /> BTSExpenseDemo.btproj,<br /><br /> BTSExpenseDemo.sln|Fournit un projet, une solution, et des fichiers associés pour cet exemple.|  
|Dans le dossier \BTSExpenseDemo :<br /><br /> BTSExpenseDemoBinding.xml|Utilisé pour une installation automatique, comme une liaison de port.|  
|Dans le dossier \BTSExpenseDemo :<br /><br /> BTSExpenseOrchestration.odx|Fournit une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour cet exemple.|  
|Dans le dossier \BTSExpenseDemo :<br /><br /> SchemaExpenseReport.xsd|Fournit un schéma pour la note de frais au format XML.|  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\AdaptersUsage\ExpenseReportSubmission  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compile le projet Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, et déploie l'assembly résultant.  
  
    -   Crée et lie les ports d'envoi et de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :  
        >   
        >  `Warning: Receive handler not specified for receive location "BTSExpenseReceiveLocation"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.BTSExpenseDemo.BTSOrchestration"; updating with first available host`.  
        >   
        >  Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
    -   Configure IIS.  
  
    -   Lie et démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   Définit l'adresse HTTP à l'emplacement prévu par le tableur Excel.  
  
    > [!NOTE]
    >  Pour plus d’informations sur le filtre ISAPI de BizTalk, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
    > [!NOTE]
    >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
    > [!NOTE]
    >  Si vous choisissez d'ouvrir et de créer le projet dans cet exemple sans exécuter le fichier Setup.bat, vous devez d'abord créer une paire de clés de nom fort en utilisant l'utilitaire .NET Framework Strong Name Utility (sn.exe). Utilisez cette paire de clés pour signer l'assembly obtenu.  
  
    > [!NOTE]
    >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
3.  Le fichier setup.bat configure le répertoire virtuel pour que cet exemple soit exécuté dans le pool d'applications IIS associé au site Web par défaut.  Pour configurer le répertoire virtuel pour cet exemple soit exécuté sous le contexte d’un utilisateur dans le **utilisateurs d’hôtes BizTalk isolés** et **IIS_WPG** groupes d’utilisateurs, vous devez configurer le répertoire virtuel pour s’exécuter dans un nouveau Pool d’applications IIS.  Configurez le répertoire virtuel à exécuter dans un nouveau pool d’applications IIS en effectuant les étapes suivantes :  
  
    > [!NOTE]
    >  Si vous avez déjà créé un nouveau pool d'applications pour un autre exemple SDK, alors vous pouvez passer au dernier élément ci-dessous.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.  
  
    2.  Dans le **Gestionnaire des Services Internet (IIS)**, accédez à la **Pools d’applications** dossier.  
  
    3.  Cliquez sur le **Pools d’applications** dossier puis cliquez sur **nouveau**, **Pool d’applications...**  
  
    4.  Entrez un nom pour le **ID du Pool d’applications :** tel que BizTalkSDKSamples, vérifiez que le **utiliser les paramètres par défaut pour le nouveau pool d’applications** option est sélectionnée, puis cliquez sur **OK** à créer le pool d’applications.  
  
    5.  Cliquez sur le pool d’applications, puis sur **propriétés**.  
  
    6.  Cliquez sur le **identité** onglet de la boîte de dialogue Propriétés zone et de modifier l’identité sous laquelle ce pool d’applications s’exécute à un utilisateur qui est membre de la **utilisateurs d’hôtes BizTalk isolés** groupe d’utilisateurs.  Cet utilisateur doit également être un membre de la variable locale **IIS_WPG** groupe d’utilisateurs.  
  
    7.  Configurez le répertoire virtuel pour que cet exemple de Kit de développement logiciel soit exécuté sous le nouveau pool d'applications. Le **pool d’applications :** paramètre n’est disponible sur le **répertoire virtuel** onglet de la boîte de dialogue Propriétés du répertoire virtuel. Le répertoire virtuel créé pour cet exemple est **ExpenseReportSubmission**.  
  
4.  Ajout d'une extension de service web aux IIS pour HTTPReceive.dll  
  
    1.  Dans le **Gestionnaire des Services Internet (IIS)**, accédez à la **Extensions du Service Web** dossier.  
  
    2.  Avec le bouton droit le **Extensions du Service Web** et sélectionnez **ajouter une nouvelle extension de service Web** pour afficher les **nouvelle Extension de Service Web** boîte de dialogue.  
  
    3.  Entrez **ExpenseReportSubmission** pour **nom d’Extension :**  
  
    4.  Cliquez sur **ajouter** pour afficher les **ajouter le fichier** boîte de dialogue.  
  
    5.  Cliquez sur **Parcourir** pour afficher les **ouvrir** boîte de dialogue zone et accédez à  *\<dossier d’Installation de BizTalk Server\>*\HttpReceive\ BTSHTTPReceive.dll, puis cliquez sur **ouvrir**, puis cliquez sur **OK**.  
  
    6.  Activer l’option pour **définir l’état de l’extension à autorisée** et cliquez sur **OK**.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 Utilisez la procédure suivante pour exécuter l'exemple ExpenseReportSubmission.  
  
> [!NOTE]
>  Si vous utilisez les composants de sécurité avancée de Microsoft Excel, les macros du tableur peuvent être désactivées. Suivez les instructions fournies par Excel sur la manière d'exécuter des macros non-signées provenant d'une source approuvée.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Ouvrez le fichier Excel ExpenseReport.15.3.xls inclus dans cet exemple.  
  
2.  Eventuellement, modifiez les données d'exemple dans le tableur sans changer son format.  
  
3.  Dans la feuille de calcul, cliquez sur **Démarrer** pour effectuer des calculs locaux.  
  
     Le texte du bouton passe de **Démarrer** à **Submit**.  
  
4.  Dans la feuille de calcul, cliquez sur **Submit**.  
  
5.  Observez le texte du message soumis, le résultat au-dessus du tableau avec l'arrière-plan jaune (cellule C7), ainsi que le code de retour et la description de texte en dessous et à droite (cellule G23).  
  
     Si la soumission échoue, essayez à nouveau. Consultez également le tableau de résolution des problèmes dans la section Commentaires.  
  
## <a name="comments"></a>Commentaires  
 Des scénarios comme celui-ci peuvent se produire lorsqu'une force de vente sur le terrain est par exemple équipée de versions plus anciennes de Microsoft Windows, qui ne supportent pas le .NET Framework, et pour lesquelles une mise à jour vers une version plus récente de Windows ne serait pas une option viable.  
  
 Les principaux composants présentés dans cet exemple sont :  
  
-   Soumission à partir d'une application client riche (non basée sur .NET)  
  
-   Intégration de Microsoft Office  
  
-   Connections de réception HTTP  
  
-   Orchestration simple  
  
-   Adaptateur de fichier  
  
 Le tableau suivant montre les éventuelles erreurs de soumission et leurs solutions.  
  
|Code d'erreur HTTP|Action possible|  
|---------------------|---------------------|  
|401 Non autorisé|Activez l'accès anonyme sur le répertoire virtuel.|  
|503 Service non disponible, et la plupart des autres codes HTTP dans les plages 400 et 500|Assurez-vous que l'hôte est en cours d'exécution et que le service est déployé, relié au bon port, et démarré.|  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs- Utilisation](../core/adapter-samples-usage.md)