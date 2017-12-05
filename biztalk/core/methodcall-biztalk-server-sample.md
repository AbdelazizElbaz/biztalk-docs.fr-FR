---
title: MethodCall (exemple BizTalk Server) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, calling
- examples, orchestrations
- orchestrations, methods
ms.assetid: 6bdc72da-9478-403a-b706-3089b7374ac7
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16b97b7c81b36774bcf2eaff53a1a4ff91b6f9e8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="methodcall-biztalk-server-sample"></a>MethodCall (exemple BizTalk Server)
L'exemple MethodCall illustre l'appel d'une méthode .NET à partir d'une orchestration BizTalk Server.  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple interagit avec une méthode .NET en procédant comme suit :  
  
1.  L'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] récupère un fichier d'entrée XML dans le dossier In. Ce fichier contient des informations sur une addition ou une soustraction que vous souhaitez voir la bibliothèque d'écritures mathématiques effectuer.  
  
2.  L'orchestration appelle la bibliothèque d'écritures mathématiques intégrée afin de réaliser l'addition ou la soustraction spécifiée dans le fichier d'entrée XML.  
  
3.  L’approprié à la méthode de la bibliothèque mathématique, soit **ajouter** ou **soustraction**, effectue le calcul demandé et empaquette le résultat sous forme de document XML.  
  
4.  L'orchestration place le fichier .xml résultant dans le dossier Out.  
  
## <a name="how-this-sample-is-designed-and-why"></a>Cet exemple est conçu et pourquoi  
 Il illustre les fonctionnalités suivantes :  
  
-   Exploitation des propriétés promues dans une orchestration. Les trois éléments dans InputSchema.xsd sont promus en tant que champs distinctifs. Lorsque l'orchestration reçoit le message d'entrée, elle récupère les valeurs de ces trois champs et les affecte aux variables correspondantes qui sont déclarées dans l'orchestration.  
  
-   À l’aide de la **décider** forme pour exprimer la logique « if-then-else » dans une orchestration. Une fois que l’orchestration assigne les valeurs des champs distinctifs à des variables internes, il passe à la **décider** forme pour vérifier si une addition ou soustraction doit être effectuée. Si aucune opération ne doit être effectuée, l'orchestration est arrêtée.  
  
-   Appel d'un assembly externe à partir d'une orchestration. Lorsqu'une addition doit être effectuée, l'orchestration appelle un assembly C# externe et transmet deux paramètres nécessaires pour effectuer l'opération. La même procédure s'applique dans le cas d'une soustraction.  
  
    > [!NOTE]
    >  Vous devez installer l'assembly dans le GAC (Global Assembly Cache) avant de pouvoir l'appeler à partir de l'orchestration ; sinon, vous recevez une erreur XLANG au moment de l'exécution.  
  
-   À l’aide de la **assignation du Message** forme pour construire le message de sortie.  
  
-   Débogage de l'orchestration en ajoutant le code suivant dans la forme Expression :  
  
    ```  
    System.Diagnostics.Debug.WriteLine(iResult);  
    ```  
  
     Vous pouvez également écrire le résultat dans le journal des événements comme suit :  
  
    ```  
    System.Diagnostics.EventLog.WriteEntry("MethodCall SDK Sample Debug", System.String.Format("Result = {0}", iResult);  
    ```  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*\>\Orchestrations\MethodCall\  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Permet d'annuler le déploiement des assemblys et de supprimer ceux-ci du Global Assembly Cache. Supprime les ports d'envoi et de réception. Supprime les répertoires virtuels Microsoft Internet Information Services (IIS) le cas échéant.|  
|Input.xml|Exemple de fichier d'entrée.|  
|Setup.bat|Utilisé pour créer et initialiser cet exemple.|  
|Dans le dossier \MathLibrary :<br /><br /> AssemblyInfo.cs, MathHelper.cs, MathLibrary.csproj|Projet et fichiers sources pour la bibliothèque d'écritures mathématiques utilisée par cet exemple.|  
|Dans le dossier \MethodCallSample :<br /><br /> InputSchema.xsd, OutputSchema.xsd|Schémas pour les fichiers .xml d'entrée et de sortie, respectivement.|  
|Dans le dossier \MethodCallSample :<br /><br /> MethodCallSample.btproj, MethodCallSample.sln|Fichiers projet et solution de l'exemple.|  
|Dans le dossier \MethodCallSample :<br /><br /> MethodCallSampleBinding.xml|Utilisé pour l’installation automatique, notamment la liaison de port.|  
|Dans le dossier \MethodCallSample :<br /><br /> MethodCallService.odx|Orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui appelle la bibliothèque d'écritures mathématiques afin d'effectuer le calcul demandé.|  
  
## <a name="building-and-initializing-this-sample"></a>Création et initialisation de cet exemple  
  
#### <a name="to-build-and-initialize-the-methodcall-sample"></a>Pour créer et initialiser l'exemple MethodCall  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*\>\Orchestrations\MethodCall  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée (In) et de sortie (Out) associés à cet exemple dans le dossier MethodCall.  
  
    -   Compilation des projets de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] pour cet exemple, puis déploiement des assemblys qui en résultent.  
  
    -   Création et liaison à l'orchestration de l'emplacement de réception de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ainsi que des ports d'envoi et de réception.  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi. Inscrit et démarre l’orchestration.  
  
> [!NOTE]
>  Vous devez confirmer que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'a pas signalé d'erreur pendant le processus de création et d'initialisation, avant d'essayer de faire fonctionner cet exemple.  
  
## <a name="running-this-sample"></a>Cet exemple en cours d’exécution  
  
#### <a name="to-run-the-methodcall-sample"></a>Pour exécuter l'exemple MethodCall  
  
1.  Collez une copie du fichier Input.xml dans le dossier In.  
  
2.  Observez le fichier .xml créé dans le dossier Out. Ce fichier contient le résultat de l'opération d'addition ou de soustraction demandée. Le format du nom de ce fichier est \< *MessageID*\>.xml, où  *\<MessageID\>*  est le GUID généré pour identifier de façon unique le message .  
  
3.  Vous pouvez modifier le fichier d'entrée de manière à réaliser des additions ou des soustractions différentes.  
  
## <a name="uninstalling-this-sample"></a>Désinstallation de l'exemple  
  
#### <a name="to-uninstall-the-methodcall-sample"></a>Pour désinstaller l'exemple MethodCall  
  
1.  À un [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] invite de commandes, accédez au répertoire (**cd**) à \< *exemples de chemin*\>\Orchestrations\MethodCall\\.  
  
2.  Exécutez Cleanup.bat.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestrations (dossier d’exemples BizTalk Server)](../core/orchestrations-biztalk-server-samples-folder.md)