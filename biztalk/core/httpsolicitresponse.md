---
title: HTTPSolicitResponse | Documents Microsoft
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
ms.assetid: b149544e-3279-4ac9-b31f-fff3e41ec8e7
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59f5c2821af02fb87727a4096f4b6e586bfd5b4f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="httpsolicitresponse"></a>HTTPSolicitResponse
L'exemple HTTPSolicitResponse montre comment créer une orchestration Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui se sert d'une application ASP.NET pour faciliter le traitement des données d'orchestration. Dans cet exemple, l'orchestration utilise un port de requête/réponse pour envoyer un message à l'application ASP.NET et pour récupérer la réponse. L'intégration entre l'orchestration BizTalk Server et l'application ASP.NET est effectuée à l'aide de l'adaptateur HTTP. Pour plus d’informations, consultez [adaptateur HTTP](../core/http-adapter.md).  
  
## <a name="what-this-sample-does"></a>Fonctions de l'exemple  
 Cet exemple consiste en une orchestration BizTalk Server qui reçoit une requête contenant deux nombres à multiplier, et qui satisfait cette requête au moyen de la séquence d'étapes suivante :  
  
1.  L'orchestration BizTalk Server récupère un fichier d'entrée .xml dans un dossier spécifique.  
  
2.  L'orchestration utilise une requête HTTP pour transmettre le XML du fichier vers une application ASP.NET de multiplication.  
  
3.  L'application ASP.NET de multiplication répond à la requête HTTP en effectuant la multiplication et en renvoyant le résultat sous forme de XML dans la réponse HTTP.  
  
4.  L'orchestration reçoit le résultat sous forme de XML dans une réponse XML et écrit ce résultat dans un fichier .xml dans un dossier spécifique.  
  
## <a name="where-to-find-this-sample"></a>Accès à l'exemple  
 \<*Exemples de chemin d’accès*> \AdaptersUsage\HTTPSolicitResponse  
  
 Le tableau suivant présente les fichiers de cet exemple et décrit leur fonction.  
  
|Fichier(s)| Description|  
|---------------|-----------------|  
|Cleanup.bat|Annule le déploiement des assemblys et les supprime du GAC, supprime les ports d'envoi et de réception, ainsi que les répertoires virtuels Microsoft Internet Information Services.|  
|HttpSolicitResponse.btproj, HttpSolicitResponse.sln|Fournissent des fichiers projet et source pour le projet BizTalk contenant l'orchestration qui utilise l'application ASP.NET de multiplication, les schémas associés, etc.|  
|HttpSolicitResponseBinding.xml|Fournit une configuration automatisée notamment la liaison de port.|  
|MultiplyRequest.xsd, MultiplyResponse.xsd|Fournissent respectivement des schémas pour la requête de multiplication et les messages XML de réponse.|  
|MultiplyTwoIntegers.odx|Fournit une orchestration BizTalk Server qui reçoit un fichier .xml demandant une opération de multiplication, transfère la requête à l'application ASP.NET de multiplication, et écrit la réponse dans un fichier.|  
|request_in.xml|Exemple de fichier d'entrée.|  
|Setup.bat|Crée et initialise l'exemple.|  
|Dans le dossier \Multiplier :<br /><br /> Multiplier.aspx, Multiplier.aspx.cs, Multiplier.sln|Contiennent des fichiers constituant l'application ASP.NET qui effectue le service de multiplication, y compris les fichiers de projet et de solution, les fichiers ASPX, Microsoft Visual C# .NET, les fichiers sources, etc.|  
  
## <a name="building-and-initializing-the-sample"></a>Création et initialisation de l'exemple  
 Les procédures suivantes permettent de créer et d'initialiser l'exemple HTTPSolicitResponse.  
  
> [!NOTE]
>  Cet exemple ne fonctionne pas si le nom de l'emplacement de réception contient des caractères en majuscules.  
  
#### <a name="to-build-and-initialize-the-sample"></a>Pour créer et initialiser l’exemple  
  
1.  Dans une fenêtre de commande, accédez au dossier suivant :  
  
     \<*Exemples de chemin d’accès*> \AdaptersUsage\HTTPSolicitResponse  
  
2.  Exécutez le fichier Setup.bat, qui effectue les actions suivantes :  
  
    -   Création des dossiers d'entrée et de sortie pour cet exemple :  
  
         \<*Exemples de chemin d’accès*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseInput  
  
         \<*Exemples de chemin d’accès*> \AdaptersUsage\HttpSolicitResponse\HttpSolicitResponseOutput  
  
    -   Compilation et configuration l'application ASP.NET de multiplication utilisée par cet exemple.  
  
        > [!NOTE]
        >  Lors de la création de pool d’applications dans IIS Manager, définissez la **DefaultAppPool** version .NET Framework à **.Net Framework v4.0**.  
  
    -   Compilation et déploiement de l'orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisée dans l'exemple ;  
  
    -   Création et liaison de l'emplacement et des ports [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de réception nécessaires.  
  
        > [!NOTE]
        >  Cet exemple affiche les avertissements suivants lors de la création et de la liaison des ports :  
  
        > [!NOTE]
        >  `Warning: Receive handler not specified for receive location "HttpSolicitResponseReceiveLocation"; updating with first receive handler with matching transport type.`  
  
        > [!NOTE]
        >  `Warning: Host not specified for orchestration "Microsoft.Samples.BizTalk.HttpSolicitResponse.MultiplyTwoIntegers"; updating with first available host.`  
  
    -   Active l'emplacement de réception, et démarre le port d'envoi.  
  
        > [!NOTE]
        >  Dans cet exemple, l'orchestration utilise un port bidirectionnel pour l'interaction HTTP avec l'application ASP.NET.  
  
        > [!NOTE]
        >  Avant de tenter d'exécuter cet exemple, vous devez confirmer que BizTalk n'a signalé aucune erreur durant le processus de création et d'initialisation.  
  
        > [!NOTE]
        >  Si vous décidez d'ouvrir et de créer les projets de cet exemple sans exécuter le fichier Setup.bat, vous devez commencer par créer une paire de clés de nom fort à l'aide de .NET Framework Strong Name Utility (sn.exe). Celle-ci permet de signer les assemblys obtenus.  
  
        > [!NOTE]
        >  Pour annuler les modifications effectuées par Setup.bat, exécutez Cleanup.bat. Vous devez exécuter Cleanup.bat avant d'exécuter Cleanup.bat une seconde fois.  
  
## <a name="running-the-sample"></a>Exécution de l’exemple  
 La procédure suivante permet d'exécuter l'exemple HTTPSolicitResponse.  
  
#### <a name="to-run-the-sample"></a>Pour exécuter l’exemple  
  
1.  Collez une copie du fichier request_in.xml dans le dossier HttpSolicitResponseInput.  
  
2.  Observez le fichier .xml créé dans le dossier HttpSolicitResponseOutput. Le nom de ce fichier .xml a pour base le GUID de l'ID du message. Ce fichier contient le résultat au format XML de l'opération de multiplication.  
  
    > [!NOTE]
    >  Vous pouvez modifier les valeurs d'opérande dans le fichier d'entrée pour effectuer une autre opération de multiplication.  
  
## <a name="comments"></a>Commentaires  
 Vous pouvez adapter cet exemple pour communiquer avec un autre système externe qui présente une interface HTTP.  
  
 Les fichiers MultiplyRequest.xsd et MultiplyResponse.xsd sont les schémas XML qui définissent le format des données d'entrée et de sortie de l'application ASP.NET de multiplication. L'orchestration utilise ces fichiers pour définir les types de message requête et réponse.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’adaptateur HTTP](../core/http-adapter-samples.md)