---
title: "Erreurs dans la liste des tâches de build | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- building, errors
- errors, building
ms.assetid: 05b36511-3031-4e13-ac2f-bfdbec0f48cb
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1bfd5b9f7b974b00d63831484ecbaa44e2568fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="build-errors-in-the-task-list"></a>Erreurs de génération dans la liste des tâches
Lorsque vous générez votre projet ou solution, les résultats s'affichent dans la fenêtre Sortie tandis que les erreurs individuelles et avertissements apparaissent dans la liste des tâches.  
  
 Les erreurs et avertissements apparaissent dans la liste des tâches. Vous pouvez double-cliquer sur l'erreur. La sélection s'applique alors à l'objet qui n'est pas configuré correctement.  
  
> [!NOTE]
>  Lors de la génération, le compilateur ne valide pas les XPath. Prenez garde d’utiliser une syntaxe XPath valide.  
  
## <a name="insufficient-configuration-action"></a>Action relative à une configuration insuffisante  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!CAUTION]
>  Si le Concepteur d'orchestration fournit des avertissements relatifs à une configuration insuffisante là où il le peut, rien ne garantit que votre orchestration soit correctement compilée en l'absence de ce genre d'avertissements.  
  
## <a name="compiler-asks-if-you-are-missing-an-assembly-reference"></a>Le compilateur vous demande s'il manque une référence d'assembly  
  
### <a name="problem"></a>Problème  
 Lorsque vous compilez l'orchestration, un message d'erreur s'affiche. Il finit par la question « ne manque-t-il pas une référence d'assembly ? ». Les deux messages les plus courants sont les suivants :  
  
-   Le type ou le nom d'espace de noms 'X' n'existe pas dans l'espace de noms 'Y' (ne manque-t-il pas une référence d'assembly ?)  
  
-   L'identificateur 'X' n'existe pas dans 'Y' ; ne manque-t-il pas une référence d'assembly ?  
  
### <a name="cause"></a>Cause  
 Cette erreur peut être générée par l'un des cas suivants :  
  
-   Votre projet ne fait pas référence aux assemblys requis.  
  
-   Votre projet comporte un mappage ou un autre type d'objet dont le nom est identique au projet.  
  
-   Votre projet utilise des schémas PIP (Partner Interface Process) basés sur le langage XSD (XML Schema definition language) et contient des schémas XSD dans un sous-dossier appelé Système.  
  
-   Votre projet utilise une propriété globale dont l'espace de noms est un sous-ensemble de l'espace de nom actuel du projet. Par exemple, l'utilisation de l'espace de noms de propriété globale « File.ReceivedFileName » dans une orchestration contenue dans le projet « Accounts.FILE ».  
  
### <a name="resolution"></a>Résolution  
 Les solutions suivantes peuvent s'appliquer, en fonction de la cause du problème :  
  
-   Ajoutez une référence aux assemblys manquants nécessaires au projet.  
  
-   Attribuez un nom de mappage ou d'objet différent du nom du projet. Vous pouvez effectuer cette opération dans la page des propriétés de l'objet (par exemple, la page de propriétés du mappage contient une propriété Nom).  
  
-   Modifiez l'espace de noms des schémas dans Visual Studio. Pour faire cela à l’aide de Visual Studio, cliquez sur **afficher tous les fichiers** sur la **projet** menu, puis développez le **système** nœud dans l’Explorateur de solutions. Cliquez sur chaque fichier dans le dossier système et de ses sous-dossiers et modifiez l’entrée de l’espace de noms dans la fenêtre Propriétés ainsi que toute occurrence de **système** devienne _**système**. Par exemple, remplacez le **MyProject.System.SubFolder** espace de noms **MyProject._System.Subfolder** espace de noms. Pour plus d’informations sur ce problème, consultez l’article [916649](http://support.microsoft.com/?kbid=916649).  
  
-   Supprimez l'espace de noms de propriété globale conflictuel du projet.  
  
## <a name="you-receive-a-message-has-not-been-initialized-in-construct-statement-error-when-building-your-project"></a>L'erreur « le message n'a pas été initialisé dans l'instruction de construction » s'affiche lors de la génération du projet  
  
### <a name="problem"></a>Problème  
 Lorsque vous compilez l'application BizTalk, l'erreur « le message n'a pas été initialisé dans l'instruction de construction » s'affiche.  
  
### <a name="cause"></a>Cause  
 Lorsque vous créez un message, vous en indiquez toutes les variables. Vous procédez ensuite aux affectations au message ou à des parties de ce dernier. Si une affectation de message est inclus dans une fonction **construire un Message** forme, vous pouvez recevoir le message d’erreur d’initialisation.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, assurez-vous que vous incluez toutes les parties d’une assignation de message spécifique dans le même **construire un Message** forme. Pour obtenir un support liées, consultez l’article [870606](http://support.microsoft.com/?kbid=870606).  
  
 Vous pouvez également résoudre ce problème en créant un message dans un **construire** forme avant d’utiliser une instance de celui-ci dans un **Expression** forme. Par exemple, le code suivant génère une erreur si placé dans un **Expression** forme :  
  
```  
XMLDOM = new System.Xml.XmlDocument();  
POAckMsg = XMLDOM;  
```  
  
 Pour résoudre le problème, créez une instance de XMLDOM dans une **construire** mettre en forme, puis effectuez l’assignation dans une en aval **Expression** forme.  
  
## <a name="you-receive-a-use-of-unconstructed-message-error-when-building-your-project"></a>L'erreur « utilisation du message non construit » s'affiche lors de la génération du projet  
  
### <a name="problem"></a>Problème  
 Lorsque vous compilez votre projet BizTalk, vous recevez l’erreur « utilisation du message non construit '\<message >' ».  
  
### <a name="cause"></a>Cause  
 Cette erreur se produit lorsqu’un message non construit est utilisé dans un **envoyer** forme.  
  
### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, ajoutez un **construire un Message** forme à l’orchestration. Inclure le **construire un Message** avant de mettre en forme le **envoyer** forme est liée à un service Web.  
  
 Pour plus d’informations sur cette erreur et les services Web, consultez l’article [921043](http://support.microsoft.com/?kbid=921043).  
  
## <a name="setting-a-transaction-level-for-a-scope-results-in-an-error"></a>Définition du niveau de transaction pour les résultats de l'étendue d'une erreur  
  
### <a name="problem"></a>Problème  
 Une fois le type de transaction configuré pour une étendue ou une autre entité prenant en charge des transactions dans l'orchestration, le message « Une orchestration non transactionnelle ne peut contenir aucune autre transaction » s'affiche.  
  
### <a name="cause"></a>Cause  
 Cette erreur se produit lorsque vous tentez de configurer le type de transaction d'une étendue (ou d'une autre entité) d'une orchestration en « Atomique » ou « À long terme » lorsque le type de transaction de l'orchestration elle-même est « Aucun ».  
  
### <a name="resolution"></a>Résolution  
 Assurez-vous que les paramètres du type de transaction de l'orchestration et des objets qui la composent sont compatibles.  
  
## <a name="project-build-results-in-the-error-you-must-specify-at-least-one-already-initialized-correlation-set-for-a-non-activation-receive-that-is-on-a-non-selfcorrelating-port"></a>La génération du projet entraîne l'affichage du message d'erreur « vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation »  
  
### <a name="problem"></a>Problème  
 Lorsque vous compilez votre projet BizTalk, le message d'erreur « vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation » s'affiche.  
  
### <a name="cause"></a>Cause  
 Cette erreur peut se produire si votre orchestration ne possède aucune forme **réception** formes (activer = true) ou ne possède aucune forme **réception** formes et n’est pas appelé directement par une autre orchestration.  
  
### <a name="resolution"></a>Résolution  
 Si votre orchestration n’est pas appelée par une autre orchestration, vous devez configurer un de le **réception** formes soit active. Pour plus d’informations sur la configuration de la **réception** forme, y compris des liens vers la corrélation, consultez [comment configurer la forme réception](../core/how-to-configure-the-receive-shape.md).  
  
## <a name="you-receive-the-error-assembly-generation-failed----referenced-assembly-assembly-does-not-have-a-strong-name-when-building-your-solution"></a>Vous recevez l’erreur « Échec de la génération de l’Assembly--l’assembly référencé '\<assembly >' n’a pas un nom fort » lors de la génération de votre solution  
  
### <a name="problem"></a>Problème  
 Vous recevez l’erreur « Échec de la génération de l’Assembly--l’assembly référencé '\<assembly >' n’a pas un nom fort » lorsque la génération de votre solution qui a une orchestration.  
  
### <a name="cause"></a>Cause  
 Ce problème se produit lorsqu'un type issu d'un assembly référencé non signé est utilisé dans une orchestration.  
  
### <a name="resolution"></a>Résolution  
 Attribuez un nom fort à l'assembly référencé. S'il s'agit d'un assembly personnalisé que vous pouvez recompiler, utilisez l'outil Strong Name Tool pour créer un fichier (de clé) .snk, puis référencez ce fichier de clé dans les propriétés de l'assembly du projet. Pour plus d’informations sur un assembly de noms forts, consultez [comment configurer un fichier de clé de Assembly de nom fort](../core/how-to-configure-a-strong-name-assembly-key-file.md).  
  
## <a name="the-error-failed-to-add-resources-change-requests-failed-for-some-resources-occurs-when-deploying-an-orchestration"></a>L'erreur « Échec d'ajout de ressource(s). Échec des requêtes de modification pour certaines ressources » se produit lors du déploiement d'une orchestration  
  
### <a name="problem"></a>Problème  
 Lors du déploiement d'une orchestration, le message d'erreur suivant s'affiche et le déploiement échoue :  
  
```  
Failed to add resource(s). Change requests failed for some resources. BizTalkAssemblyResourceManager failed to complete end type change request. Object reference not set to an instance of an object.  
```  
  
### <a name="cause"></a>Cause  
 Cette erreur se produit si l'orchestration contient des objets qui utilisent les mots clés de C#.  
  
### <a name="resolution"></a>Résolution  
 Supprimez tout mot clé de C# de l'orchestration. Pour obtenir la liste des mots clés c#, consultez [http://go.microsoft.com/fwlink/?LinkId=74346](http://go.microsoft.com/fwlink/?LinkId=74346).  
  
## <a name="you-receive-an-invalid-property-value-error-when-compiling-your-orchestration"></a>Une erreur de valeur de propriété incorrecte s'affiche lors de la compilation de l'orchestration  
  
### <a name="problem"></a>Problème  
 Une erreur de valeur de propriété incorrecte s'affiche lors de la génération de l'orchestration.  
  
### <a name="cause"></a>Cause  
 Des objets de la solution ont des noms identiques. Par exemple, un message a le même nom qu'un port.  
  
### <a name="resolution"></a>Résolution  
 Vérifiez que chaque objet de la solution a un nom unique. Pour éviter que cette erreur se produise, vous pouvez adhérer à une convention d'affectation de nom.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer des Orchestrations](../core/how-to-build-orchestrations.md)