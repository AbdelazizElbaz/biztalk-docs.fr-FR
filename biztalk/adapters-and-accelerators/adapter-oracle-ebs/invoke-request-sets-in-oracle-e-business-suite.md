---
title: "Appeler des ensembles de requêtes dans Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a79bff63-325d-4745-ab0e-839e00476ab1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 924bfbfc8e0d22ba5fb00099039b21a5b8180bcf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-request-sets-in-oracle-e-business-suite"></a>Appeler des ensembles de requêtes dans Oracle E-Business Suite
[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]vous permet d’exécuter la demande définit dans Oracle E-Business Suite. Demander des jeux sont divisées en une ou plusieurs étapes, et chaque étape contient un ensemble de rapports et des programmes simultanés. Pour plus d’informations sur comment l’adaptateur prend en charge les ensembles de requêtes, consultez [opérations sur demande définit](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md). Pour plus d’informations sur la structure de SOAP des messages pour l’appel d’ensembles de requêtes, consultez [des schémas de Message de demande définit](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé les étapes de [conditions préalables requises pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/prerequisites-to-create-oracle-e-business-suite-applications.md).  
  
## <a name="how-to-invoke-request-sets-in-oracle-e-business-suite"></a>L’appel de demande définit dans Oracle E-Business Suite  
 Une opération sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour appeler une demande de définition, ces tâches sont :  
  
-   Créez un projet BizTalk et générer le schéma pour le jeu de demande que vous souhaitez appeler.  
  
-   Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages vers et à partir d’Oracle E-Business Suite.  
  
-   Créez une orchestration pour appeler l’ensemble de la demande.  
  
-   Générez et déployez le projet BizTalk.  
  
-   Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
-   Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment appeler un ensemble de la demande, en appelant le **fonction des rapports de sécurité** demande (nom convivial) définie à partir de la **bibliothèque d’objets Application** application. Le nom réel de l’ensemble de la demande est **FNDRSSUB43**. Cet ensemble de la demande est disponible avec l’application d’Oracle E-Business Suite par défaut. Cet ensemble de la requête retourne un ID de demande.  
  
 Par conséquent, dans cette rubrique, nous génération du schéma pour le **FNDRSSUB43** demander ensemble. Consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
 Dans cette orchestration, vous devez créer deux messages : un pour envoyer le message à appeler l’ensemble de la demande et l’autre pour recevoir une réponse pour l’ensemble de la demande.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *RequestSet.OracleEBSBindingRequestSets_FND. FNDRSSUB43*, où RequestSet est le nom de votre projet BizTalk. OracleEBSBindingRequestSets est le schéma généré pour appeler le **FNDRSSUB43** demander ensemble.|  
  
6.  Répétez l’étape 3 pour créer un message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Réponse|*RequestSet.OracleEBSBindingRequestSets_FND. FNDRSSUB43Response*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour l’appel de demande définit dans Oracle E-Business Suite. Dans cette orchestration, vous supprimez un message de demande à une emplacement de réception. L’orchestration traite ce message et le transmet à Oracle E-Business Suite pour appeler le **FNDRSSUB43** demander ensemble. La réponse pour l’ensemble de la demande est reçue à partir d’Oracle et est enregistrée dans un autre emplacement. Une orchestration classique pour appeler un ensemble de la demande doit contenir :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à Oracle E-Business Suite et de recevoir des réponses.  
  
-   Unidirectionnel port de réception pour recevoir des messages de demande à envoyer à Oracle E-Business Suite.  
  
-   Un double port d’envoi pour envoyer des messages de demande pour Oracle E-Business Suite et de recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir d’Oracle E-Business Suite dans un dossier.  
  
 Un exemple d’orchestration pour appeler un ensemble de la demande ressemble à ceci :  
  
 ![Orchestration permettant d’appeler des ensembles de requêtes](../../adapters-and-accelerators/adapter-oracle-ebs/media/ea161292-8613-4c0b-ac24-2f26c54bf3a3.gif "ea161292-8613-4c0b-ac24-2f26c54bf3a3")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.RequestSet.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.RequestSet.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.RequestSet.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.RequestSet.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à Oracle E-Business Suite.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir d’Oracle E-Business Suite.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleEBS physique pour envoyer des messages pour Oracle E-Business Suite. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports d’envoi, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  
  
         Pour appeler la demande définit à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez définir le contexte de l’application appropriée dans lequel l’opération est appelée. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] fournit certaines propriétés de liaison pour spécifier le contexte d’application pour toute opération. Vous devez définir ces propriétés de liaison sur le port WCF-Custom ou WCF-OracleEBS utilisé pour appeler des ensembles de requêtes.  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **base de données**, vous devez spécifier les propriétés de liaison suivantes pour définir le contexte des applications.  
  
            |Propriété de liaison|Valeur|  
            |----------------------|-----------|  
            |**OracleUserName**|Spécifiez le nom d’un utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OracleUserName** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que la casse du nom d’utilisateur doivent être conservés ou si vous souhaitez entrer un nom d’utilisateur contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OraclePassword**|Le mot de passe pour l’utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OraclePassword** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le mot de passe est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que le cas du mot de passe doivent être conservés ou si vous souhaitez entrer un mot de passe contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OracleEBSResponsibilityName**|La responsabilité est associée à l’utilisateur Oracle E-Business Suite.|  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **EBusiness**, vous devez déjà avoir spécifié les informations d’identification de Oracle E-Business lors de l’établissement de la connexion. Dans ce cas, vous devez uniquement spécifier la valeur pour le **OracleEBSResponsibilityName** propriété de liaison.  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés ](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour plus d’informations sur la façon dont l’adaptateur prend en charge la définition du contexte de l’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
        > [!NOTE]
        >  Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour l’appel de la demande définit. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour appeler le **FNDRSSUB43** ensemble de la demande est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande qui est conforme au schéma pour l’appel de la **FNDRSSUB43** demander ensemble. Par exemple, le message de demande pour appeler le **FNDRSSUB43** ensemble de la demande est :  
  
```  
<FNDRSSUB43 xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSets/FND">  
  <StartTime>\</ StartTime>  
  <All_x0020_Requests_x0020_in_x0020_the_x0020_Set_STAGE10>  
    <FNDMNNAV xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      <Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator</Responsibility>  
      \<ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">\</ns3:Application>  
    \</ns2:FNDMNNAV>  
    \<ns2:FNDMNMNU xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      \<ns3:Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator\</ns3:Responsibility>  
      \<ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">\</ns3:Application>  
    \</ns2:FNDMNMNU>  
    \<ns2:FNDMNFUN xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetStage/FND/FNDRSSUB43">  
      \<ns3:Responsibility xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">System Administrator\</ns3:Responsibility>  
      \<ns3:Application xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSetConcurrentProgram/FND/FNDRSSUB43/STAGE10/FND">\</ns3:Application>  
    \</ns2:FNDMNFUN>  
  \</ns0:All_x0020_Requests_x0020_in_x0020_the_x0020_Set_STAGE10>  
\</ns0:FNDRSSUB43>  
```  
  
> [!NOTE]
>  Le message de demande pour l’appel d’un ensemble de la demande requiert des paramètres facultatifs tels que SetRelClassOptions, SetPrintOptions, SetRepeatOptions et SetNlsOptions. Le message de demande fourni ici ne contient pas ces paramètres facultatifs. Pour plus d’informations sur le message de demande complète, y compris les paramètres facultatifs, consultez [des schémas de Message de demande définit](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-request-sets.md).  
  
 L’orchestration consomme le message, le transmet à Oracle E-Business Suite et reçoit une réponse. Le message de réponse est enregistré dans l’autre emplacement de fichier spécifié en tant que partie de l’orchestration. La réponse pour le **FNDRSSUB43** demande ensemble ressemble à ceci :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<FNDRSSUB43Response xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/RequestSets/FND">  
  <FNDRSSUB43Result>2543208</FNDRSSUB43Result>  
</FNDRSSUB43Response>  
```  
  
 La réponse à partir d’Oracle E-Business Suite contient un ID de demande. Demande de code '0' indique que l’opération sur l’échec de la définition de requête d’envoi de la dernière. Dans ce cas, vous pouvez spécifier d’autres paramètres optionnels dans le message de demande, tels que ContinueOnFail, pour déterminer la cause de l’échec et déboguer plus.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)