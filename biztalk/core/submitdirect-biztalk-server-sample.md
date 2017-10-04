---
title: SubmitDirect (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- receive adapters, examples
- examples, receive adapters
ms.assetid: 3540368b-cf46-4c83-a87b-94aec9cd1b36
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1e355f752241135d781c3425e05f017b0d86d93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="submitdirect-biztalk-server-sample"></a>SubmitDirect (exemple BizTalk Server)
L'exemple SubmitDirect présente l'envoi par programme des messages unidirectionnels et de type requête/réponse à Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'applications basées sur .NET. L'exemple illustre l'utilisation des API [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour les adaptateurs. Il fournit également un adaptateur de réception, nommé Submit, qui peut être utilisé pour envoyer des messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant d'exécuter cet exemple, assurez-vous que vous avez ouvert une session en tant qu'utilisateur membre du groupe Utilisateurs d'hôtes BizTalk isolés.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple montre comment effectuer diverses tâches liées aux adaptateurs BizTalk. Plus précisément, il montre comment :  
  
-   Travailler avec des adaptateurs isolés qui s'exécutent en dehors du processus de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur Submit est un adaptateur isolé car il est créé par un processus externe au processus de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (vous le démarrez en tant qu'application .NET).  
  
-   Envoyer des lots de messages à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adaptateur Submit utilise la fonctionnalité d'envoi de messages par lot pour envoyer plusieurs messages à la fois.  
  
-   Envoyer des messages de façon synchrone à l'aide d'un paradigme de requête/réponse, ainsi que de façon asynchrone à l'aide d'un paradigme unidirectionnel.  
  
-   Enregistrer un adaptateur avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cet exemple montre comment enregistrer un adaptateur et fournit un exécutable d'enregistrement qui automatise l'enregistrement d'un adaptateur.  
  
 Cet exemple est en fait deux exemples dans un, comme suit :  
  
-   **Envoi d’un lot de messages unidirectionnels.** L’application console SubmitMessages.exe prend les chaînes de sa ligne de commande et envoie chacune d’elles en tant qu’un message distinct pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Chaque message envoyé est récupéré à l'emplacement de réception par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], envoyé par des pipelines de réception et d'envoi PassThrough, puis écrit dans un fichier texte.  
  
-   **Envoi du message de demande/réponse.** L’application console SubmitRequest.exe prend le fichier .xml spécifié sur sa ligne de commande et l’envoie à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le schéma de ce fichier .xml définit les éléments qui contiennent deux champs d'entier. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère le fichier .xml et le traite avec une orchestration (avec un port de requête/réponse). Il utilise un mappage pour produire un message de réponse XML qui renvoie un entier, produit des deux entiers dans la requête. Lorsque la console reçoit la réponse, elle affiche le résultat.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*> \AdaptersDevelopment\SubmitDirect\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.|  
|Setup.bat|Crée et initialise l'exemple.|  
|SubmitDirect.sln|Fichier de solution qui inclut le projet BizTalk dans le dossier ProcessRequest et les projets Microsoft Visual C# dans les autres dossiers.|  
|SubmitMessagesBinding.xml, SubmitRequestBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Dans le dossier \ProcessRequest :<br /><br /> DocIn.xsd, DocOut.xsd, Multiplier.odx, Multiply.btm, ProcessRequest.btproj|Fournit un projet BizTalk qui effectue la multiplication des entiers dans le scénario de requête/réponse.|  
|Dans le dossier \SubmitMessages :<br /><br /> AssemblyInfo.cs, SubmitMessages.cs, SubmitMessages.csproj|Fournit un projet Visual C# pour la console qui transmet ses paramètres de chaîne de ligne de commande en tant que lot de messages séparés.|  
|Dans le dossier \SubmitRequest :<br /><br /> AssemblyInfo.cs, DocInstance.xml, SubmitRequest.cs, SubmitRequest.csproj|Fournit un projet C# pour la console qui transmet un fichier .xml (DocInstance.xml) contenant deux entiers à multiplier.|  
|Dans le dossier \TransportProxyUtils :<br /><br /> AssemblyInfo.cs, MessageHelper.cs, MessagingAPIInterface.cs, MessagingAPIs.cs, ResponseCallBack.cs, TpBatchAsyncCallback.cs, TpBatchAsyncResult.cs, TpBatchStatus.cs, TransportProxyUtils.csproj|Fournit un projet C# pour la partie exécution de l'adaptateur Submit qui implémente des méthodes d'envoi de messages synchrone et asynchrone, et d'envoi de lot et de message de requête simple.|  
|Dans le dossier \TransportProxyUtilsReg :<br /><br /> AssemblyInfo.cs, RegisterAdapter.cs, TransportProxyUtilsReg.csproj|Fournit un projet Visual C# qui montre le code que vous pouvez utiliser pour enregistrer les adaptateurs avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
|Dans le dossier \TransportProxyUtilsUI :<br /><br /> AssemblyInfo.cs, TransportProxyUtilsMgmt.cs, TransportProxyUtilsUI.csproj|Fournit un projet Visual C# pour la partie interface utilisateur de l'adaptateur Submit.|  
  
## <a name="building-and-initializing-the-sample"></a>Création et initialisation de l'exemple  
  
#### <a name="to-build-and-initialize-the-submitdirect-sample"></a>Pour créer et initialiser l'exemple SubmitDirect  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersDevelopment\SubmitDirect  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Crée le dossier de sortie suivant pour la partie envoi de lot de cet exemple.  
  
         \<*Exemples de chemin d’accès*> \AdaptersDevelopment\SubmitDirect\Out  
  
    -   Compile les divers projets [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] de cet exemple.  
  
    -   Enregistre l'adaptateur Submit avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
    -   Création et liaison des emplacements de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :  
        >   
        >  `Warning: Receive handler not specified for receive location "SubmitDirectRL"; updating with first receive handler with matching transport type.`  
        >   
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.ProcessRequest.Multiplier"; updating with first available host.`  
        >   
        >  Vous pouvez ignorer ces avertissements sans problème. (Pour s'adapter aux éventuelles différences d'attribution de noms dans les installations utilisateur, le nom d'hôte et le gestionnaire de réception ont été omis dans le fichier de liaison.)  
  
    -   Active les emplacements de réception et démarre les ports d'envoi et l'orchestration.  
  
        > [!NOTE]
        >  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
        > [!NOTE]
        >  Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
        > [!NOTE]
        >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 Puisque cet exemple utilise l'adaptateur FILE, l'hôte BizTalk (BizTalkServerApplication) doit être en cours d'exécution. Les procédures suivantes permettent d'exécuter l'exemple SubmitDirect.  
  
#### <a name="to-run-the-batch-submission-portion-of-the-submitdirect-sample"></a>Pour exécuter la partie envoi de lot de l'exemple SubmitDirect  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersDevelopment\SubmitDirect\SubmitMessages\bin\Debug  
  
2.  Exécutez le fichier SubmitMessages.exe, en transmettant plusieurs chaînes sur la ligne de commande.  
  
     Exemple : SubmitMessages msg1 msg2 msg3  
  
3.  Observez les différents fichiers texte créés dans le dossier de sortie Out. Ces fichiers contiennent les chaînes transmises sur la ligne de commande, une par fichier.  
  
#### <a name="to-run-the-requestresponse-portion-of-the-submitdirect-sample"></a>Pour exécuter la partie requête/réponse de l'exemple SubmitDirect  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersDevelopment\SubmitDirect\SubmitRequest\bin\Debug  
  
2.  Exécutez le fichier SubmitRequest.exe, en transmettant un nom de fichier .xml approprié sur la ligne de commande.  
  
     Exemple : SubmitRequest... \\.. \DocInstance.Xml  
  
3.  Observez le message de réponse XML, contenant le résultat de la multiplication, affiché dans la console.  
  
## <a name="comments"></a>Commentaires  
 Vous pouvez utiliser l'adaptateur Submit dans d'autres applications. Vous pouvez l'utiliser à partir de n'importe quel code basé sur .NET pour envoyer des messages à votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] par programme. Pour utiliser cet adaptateur avec votre code, respectez la procédure suivante.  
  
#### <a name="to-use-the-sample-adapter-with-your-code"></a>Pour utiliser l'exemple d'adaptateur avec votre code  
  
1.  Enregistrez l'adaptateur Submit avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous avez exécuté le fichier Setup.bat fourni avec cet exemple, l'adaptateur doit être enregistré et prêt à l'emploi. Sinon, vous pouvez l'enregistrer en créant les projets TransportProxyUtils.csproj, TransportProxyUtilsUI.csproj et TransportProxyUtilsReg.csproj, puis en exécutant l'exécutable produit par le projet RegisterAdapter.exe.  
  
    > [!IMPORTANT]
    >  Si vous installez BizTalk sur un ordinateur 64 bits, modifiez toutes les instances de l’entrée de Registre HKEY_CLASSES_ROOT\CLSID\ à HKEY_CLASSES_ROOT\Wow6432Node\CLSID\ dans le **RegisterAdapter.cs** fichier.  
  
2.  Créez un port de réception avec un emplacement de réception qui utilise l'adaptateur Submit. Spécifiez l'adresse de l'emplacement de réception. L'adresse peut être toute chaîne unique parmi les emplacements de réception qui utilisent cet adaptateur.  
  
3.  Référencez l'assembly Microsoft.BizTalk.SDKSamples.AdaptersDevelopment.TransportProxyUtils.dll dans votre projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
4.  Envoyez des messages à votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide d'une des méthodes suivantes fournies par cet assembly.  
  
    |Méthode(s)| Description|  
    |-----------------|-----------------|  
    |**SubmitMessage()**<br /><br /> **BeginSubmitMessage()**<br /><br /> **EndSubmitMessage()**|Méthodes synchrones et asynchrones pour envoyer un message unidirectionnel à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L’adresse de l’emplacement de réception où le message est envoyé doit être définie dans le contexte du message.<br /><br /> Une valeur booléenne indiquant l'état de l'envoi (réussite/échec) est renvoyée.|  
    |**SubmitMessages()**<br /><br /> **BeginSubmitMessages()**<br /><br /> **EndSubmitMessages()**|Méthodes synchrones et asynchrones pour envoyer un tableau de messages unidirectionnels à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Les adresses des emplacements de réception où les messages sont envoyés doivent être définies dans le contexte des messages.<br /><br /> Une valeur booléenne indiquant l'état de l'envoi (réussite/échec) est renvoyée.|  
    |**SubmitSyncMessage()**<br /><br /> **BeginSubmitSyncMessage()**<br /><br /> **EndSubmitSyncMessage()**|Méthodes synchrones et asynchrones pour envoyer un message de requête à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'adresse de l'emplacement de réception où le message est envoyé doit être définie dans le contexte du message.<br /><br /> Le message de réponse est renvoyé.|  
    |**CreateMessageFromString()**|Crée un objet de message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'une chaîne et définit la propriété de l'adresse de l'emplacement de réception dans le contexte du message.<br /><br /> Renvoie un objet de message BizTalk.|  
    |**CreateMessageFromStream()**|Crée un objet de message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à partir d'un flux et définit la propriété de l'adresse de l'emplacement de réception dans le contexte du message.<br /><br /> Renvoie un objet de message [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|  
  
     Pour plus de détails sur les paramètres et les types de retours pour ces méthodes, consultez le fichier MessagingAPIInterface.cs dans le dossier TransportProxyUtils.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateurs - développement](../core/adapter-samples-development.md)   
 [Inscription d’un adaptateur](../core/registering-an-adapter.md)