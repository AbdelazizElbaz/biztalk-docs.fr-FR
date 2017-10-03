---
title: HTTPRequestResponse | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, examples
- examples, HTTP adapters
ms.assetid: 81c66f61-d86c-49cf-8d24-21c67c68bc5a
caps.latest.revision: "35"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fad45e80cac2a398507b4288c9ac6f35c887e71b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="httprequestresponse"></a>HTTPRequestResponse
L'exemple HTTPRequestResponse présente l'utilisation du filtre ISAPI (Internet Server Application Programming Interface) de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour autoriser une application ASP.NET à communiquer avec une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Dans cet exemple, l'application ASP.NET envoie une requête au filtre ISAPI de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'orchestration traite ce message et le renvoie à l'application ASP.NET à l'aide d'une réponse synchrone. L'intégration entre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l'application ASP.NET est effectuée à l'aide du filtre ISAPI [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Dans cet exemple, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et une application ASP.NET échangent des messages et des accusés de réception de bon de commande en procédant comme suit :  
  
1.  Une application ASP.NET envoie, à l'aide d'une requête HTTP, un message de bon de commande XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit le message de bon de commande XML et crée un accusé de réception de bon de commande XML, qu'il renvoie à l'application ASP.NET dans la réponse HTTP.  
  
 L'application ASP.NET reçoit l'accusé de réception de bon de commande et actualise le formulaire Web avec des informations d'état extraites de la réponse.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 *\<Exemples de chemin d’accès >*\AdaptersUsage\HTTPRequestResponse\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.|  
|HTTPRequestResponse.btproj, HTTPRequestResponse.sln|Fournit les fichiers source et de projet du projet BizTalk qui reçoit la requête HTTP, traite le message de bon de commande et émet la réponse.|  
|HTTPRequestResponseBinding.xml|Fournit une installation automatisée, telle qu'une liaison de port.|  
|POAck.xsd, POSchema.xsd|Fournissent respectivement des schémas pour l'accusé de réception de bon de commande et les fichiers .xml de bon de commande.|  
|POReceiveOrchestration.odx|Fournit une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui reçoit le bon de commande, le traite et émet l'accusé de réception associé.|  
|Setup.bat|Crée et initialise l'exemple.|  
|Dans le dossier \RequestResponse :<br /><br /> AssemblyInfo.cs, default.aspx, default.aspx.cs, Global.asax, Global.asax.cs, RequestResponse.csproj, RequestResponse.csproj.webinfo, RequestResponse.sln, Web.config|Fichiers constituant l'application ASP.NET qui sert de pilote pour cet exemple, y compris les fichiers de projet et de solution, les fichiers ASPX, Microsoft Visual C# .NET, les fichiers sources, etc.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
 Les procédures suivantes permettent de créer et d'initialiser l'exemple HTTPRequestResponse.  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersUsage\HTTPRequestResponse  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Compile et configure l'application ASP.NET utilisée pour piloter l'exemple.  
  
        > [!NOTE]
        >  Lors de la création de pool d’applications dans IIS Manager, définissez la **DefaultAppPool** version .NET Framework à **.Net Framework v4.0**.  
  
    -   Compilation et déploiement de l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisée dans l'exemple ;  
  
    -   Compile et déploie le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Microsoft utilisé dans l'exemple ;  
  
    -   Crée et relie les ports [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nécessaires.  
  
    -   Démarre l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
        > [!IMPORTANT]
        >  Vous devez modifier l'exemple de code qui implémente l'application Web (Default.aspx.cs) pour refléter votre environnement :  
        >   
        >  http://\<*nom du serveur*>/\<*répertoire virtuel*>/BTSHTTPReceive.dll où `<servername>` est le nom du serveur Web que vous publiez et `<` *répertoire virtuel* `>` est le répertoire virtuel où réside ce fichier.  
  
        > [!NOTE]
        >  Avant de tenter d'exécuter cet exemple, vous devez confirmer que BizTalk n'a signalé aucune erreur durant le processus de création et d'initialisation.  
  
        > [!NOTE]
        >  Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Celle-ci permet de signer les assemblys obtenus. Avant de tenter de créer ce projet, vous devez également supprimer manuellement les références aux fichiers default.aspx.resx et Global.asax.resx dans le fichier RequestResponse.csproj.  
  
        > [!NOTE]
        >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
        > [!NOTE]
        >  Vous devez configurer et activer les services IIS pour utiliser l'adaptateur de réception HTTP. Pour plus d’informations, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
3.  Le fichier setup.bat configure le répertoire virtuel pour que cet exemple soit exécuté dans le pool d'applications IIS associé au site Web par défaut.  Pour configurer le répertoire virtuel pour cet exemple soit exécuté sous le contexte d’un utilisateur dans le **utilisateurs d’hôtes BizTalk isolés** et **IIS_IURS** groupes d’utilisateurs, vous devez configurer le répertoire virtuel pour s’exécuter dans un nouveau Pool d’applications IIS. Configurez le répertoire virtuel à exécuter dans un nouveau pool d’applications IIS en effectuant les étapes suivantes :  
  
    > [!NOTE]
    >  Si vous avez déjà créé un pool d'applications pour un autre exemple de Kit de développement logiciel (SDK), vous pouvez passer à la dernière étape ci-dessous.  
  
    1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
    2.  Dans le **Gestionnaire des Services Internet (IIS)**, accédez à la **Pools d’applications** dossier.  
  
    3.  Cliquez sur le **Pools d’applications** dossier puis cliquez sur **nouveau**, **Pool d’applications...**  
  
    4.  Entrez un nom pour le **ID du Pool d’applications :** tel que BizTalkSDKSamples, vérifiez que le **utiliser les paramètres par défaut pour le nouveau pool d’applications** option est sélectionnée, puis cliquez sur **OK** à créer le pool d’applications.  
  
    5.  Cliquez sur le pool d’applications, puis sur **propriétés**.  
  
    6.  Cliquez sur le **identité** onglet de la boîte de dialogue Propriétés zone et de modifier l’identité sous laquelle ce pool d’applications s’exécute à un utilisateur qui est membre de la **utilisateurs d’hôtes BizTalk isolés** groupe d’utilisateurs.  Cet utilisateur doit également être un membre de la variable locale **IIS_IURS** groupe d’utilisateurs.  
  
    7.  Configurez le répertoire virtuel pour que cet exemple de Kit de développement logiciel soit exécuté sous le nouveau pool d'applications. Le **pool d’applications** paramètre n’est disponible sur le **répertoire virtuel** onglet de la boîte de dialogue Propriétés du répertoire virtuel. Le répertoire virtuel créé pour cet exemple est HttpRequestResponseSample.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
 La procédure suivante permet d'exécuter l'exemple HTTPRequestResponse.  
  
#### <a name="to-run-this-sample"></a>Pour exécuter l'exemple  
  
1.  Sous Internet Explorer, accédez à http://localhost/RequestResponse/.  
  
2.  Renseignez les champs nécessaires dans le formulaire Web, puis cliquez sur **passer une commande** pour envoyer votre commande.  
  
3.  Observez l'état de votre commande lorsque le formulaire Web est actualisé après la réception d'une réponse.  
  
## <a name="comments"></a>Commentaires  
 Le **BTSHTTPReceiveISAPI** extension utilisée dans cet exemple est configurée pour fonctionner sur un ordinateur unique par défaut d’installation. Pour étendre cet exemple à d’autres configurations, consultez [adaptateur HTTP](../core/http-adapter.md).  
  
 Vous pouvez étendre cet exemple aux applications obligatoires pour l'envoi de données à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] via un formulaire Web, ou via le HTTP en général. L'extension de la portion de l'application ASP.NET de cet exemple permet d'émettre des requêtes pour d'autres informations et d'effectuer d'autres pré-traitements avant l'envoi des données à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateur HTTP](../core/http-adapter-samples.md)