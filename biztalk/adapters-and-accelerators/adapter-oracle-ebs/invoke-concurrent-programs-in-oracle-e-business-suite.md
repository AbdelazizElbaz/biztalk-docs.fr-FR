---
title: "Appeler des programmes simultanés dans Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85c55a35-bee4-4b50-8b00-e4198ad4c2af
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b0991ab2714ddb7acc22161ffcd29179ff7339c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-concurrent-programs-in-oracle-e-business-suite"></a>Appeler des programmes simultanés dans Oracle E-Business Suite
Oracle E-Business Suite expose des programmes simultanés que vous pouvez exécuter pour effectuer des opérations spécifiques sur les applications Oracle. Chaque application Oracle a un ensemble de programmes simultanés standard (qui sont les mêmes pour toutes les opérations) et certains programmes simultanés qui sont spécifiques à une application Oracle. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] expose tous les programmes simultanés en tant qu’opérations que les clients de l’adaptateur peuvent appeler. Pour plus d’informations sur la façon dont l’adaptateur prend en charge des programmes simultanés, consultez [opérations sur les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md). Pour plus d’informations sur la structure de SOAP des messages pour l’appel des programmes simultanés, consultez [des schémas de Message pour les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md).  
  
> [!NOTE]
>  Pour les programmes simultanés qui n’exposent pas leurs métadonnées, l’adaptateur Oracle E-Business expose 100 paramètres facultatifs pour chacun de ces programmes simultanés. Pour appeler ces programmes simultanés avec succès, l’utilisateur doit consultez la documentation d’Oracle E-Business Suite pour déterminer les paramètres pour un programme simultané qui nécessitent une valeur et puis de les spécifier. Est un exemple d’un tel programme simultané **importation du Journal** (nom réel : **GLLEZL**) dans le **comptabilité** application.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez avoir terminé les étapes de [conditions préalables requises pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/prerequisites-to-create-oracle-e-business-suite-applications.md).
  
## <a name="how-to-invoke-concurrent-programs-in-oracle-applications"></a>Comment appeler des programmes simultanés dans les Applications d’Oracle  
 Une opération sur Oracle E-Business Suite à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md). Pour appeler un programme simultané, ces tâches sont :  
  
-   Créez un projet BizTalk et générer le schéma pour le programme simultané que vous souhaitez appeler.  
  
-   Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages vers et à partir d’Oracle E-Business Suite.  
  
-   Créez une orchestration pour appeler le programme simultané.  
  
-   Générez et déployez le projet BizTalk.  
  
-   Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
-   Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment appeler le **Interface client** simultanées du programme à partir de la **des comptes clients** application. Cette application est disponible avec l’application d’Oracle E-Business Suite par défaut. Ce programme simultané renvoie un ID de demande. Pour vérifier l’état du programme simultané, nous exécutons la **Get_Status** simultanées du programme en passant l’ID de demande reçu dans la réponse de la **Interface client** simultanées du programme.  
  
 Dans cette rubrique, nous générer le schéma pour les deux le **Interface client** et **Get_Status** programmes simultanés. Pour plus d’informations sur la génération de schéma, consultez [récupérer des métadonnées pour des opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
 Dans cette orchestration, vous devez créer quatre messages, définie par une réception-réponse pour appeler le **Interface client** simultanées du programme et l’autre réception-réponse défini pour appeler le **Get_Status** simultanées du programme.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ConcurrentProgram.OracleEBSBindingSchema.RACUST*, où ConcurrentProgram est le nom de votre projet BizTalk. OracleEBSBindingSchema est le schéma généré pour appeler le **Interface client** simultanées du programme. **Remarque :** RACUST est le nom réel de la **Interface client** simultanées du programme. Alors que le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] affiche le nom convivial (**Interface client**), le schéma contient le nom réel du programme simultané.|  
  
6.  Répétez l’étape 3 pour créer trois nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Réponse|*ConcurrentProgram.OracleEBSBindingSchema.RACUSTResponse*|  
    |Get_StatusRequest|*ConcurrentProgram.OracleEBSBindingSchema1.GetStatusForConcurrentProgram*|  
    |Get_StatusResponse|*ConcurrentProgram.OracleEBSBindingSchema1.GetStatusForConcurrentProgramResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler des programmes simultanés dans Oracle E-Business Suite. Dans cette orchestration, vous supprimez un message de demande à une emplacement de réception. L’orchestration traite ce message et le transmet à Oracle E-Business Suite pour appeler le **Interface client** simultanées du programme. La réponse pour le programme simultanée est reçue à partir d’Oracle et est enregistrée dans un autre emplacement. Le message de réponse contient un ID de demande. L’orchestration inclut un **construire un Message** forme pour extraire l’ID de demande de la réponse et construire un message qui est conforme au schéma de la **Get_Status** simultanées du programme. Le message pour appeler le **Get_Status** simultanées du programme est envoyé pour Oracle E-Business Suite avec l’ID de demande en tant que paramètre. Vous devez inclure l’envoi et réception des formes, des formes de construction de message et des ports pour envoyer des messages à Oracle et de recevoir des réponses.  
  
 En règle générale, les **Interface client** simultanées du programme prendra du temps d’exécution, donc vous devez attendre avant d’exécuter le **Get_Status** simultanées. Vous pouvez automatiser ce processus en ajoutant un **délai** forme.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration permettant d’appeler des programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/media/2a02e9d8-8ea8-4898-8d05-c060761f4feb.gif "2a02e9d8-8ea8-4898-8d05-c060761f4feb")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le **forme** colonne correspondent aux formes message tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
|SendGetStatus|Send|-Définissez **nom** à *SendGetStatus*|  
|ReceiveStatusResponse|Recevoir|-Définissez **nom** à *ReceiveStatusResponse*<br />-Définissez **activer** à *False*|  
|SaveStatusResponse|Send|-Définissez **nom** à *SaveStatusResponse*|  
  
### <a name="adding-a-delay-shape"></a>Ajout d’une forme attente  
 Si vous souhaitez que l’orchestration doit attendre avant d’appeler le **Interface client** et **Get_Status** programmes simultanés, vous devez ajouter un **délai** forme à l’orchestration. Vous devez ajouter un **délai** mettre en forme une fois que l’orchestration de copie de la réponse pour le **Interface client** simultanées du programme vers un fichier de port d’envoi. Par conséquent, vous devez ajouter un **délai** forme après la **SendResponse** forme.  
  
 Dans le **délai** forme, vous pouvez spécifier l’intervalle de temps pour lequel l’orchestration doit attendre avant de procéder, en ajoutant le code suivant à l’éditeur d’Expression pour la **délai** forme :  
  
```  
new System.TimeSpan(0,2,0)  
```  
  
 En ajoutant ce code, l’orchestration attend deux minutes avant de continuer. Pour plus d’informations sur la façon de configurer le **délai** mettre en forme, consultez [comment configurer la forme attente](../../core/how-to-configure-the-delay-shape.md).  
  
### <a name="adding-the-construct-message-shape"></a>Ajout de la forme construire un Message  
 La réponse à partir d’Oracle E-Business Suite pour les **Interface client** simultanées du programme contient un ID de demande. Pour obtenir l’état du programme simultané, vous devez passer le même ID de demande en tant que paramètre à la **Get_Status** simultanées du programme. Pour ce faire, dans l’orchestration, vous devez inclure un **construire un Message** forme, dans laquelle un **assignation du Message** forme. L’objectif de la **construire un Message** est de forme :  
  
-   Pour extraire l’ID de demande à partir de la réponse est reçue pour le **Interface client** simultanées du programme.  
  
-   Pour construire un message conforme au schéma de message pour le **Get_Status** simultanées du programme.  
  
 Pour le **construire un Message** mettre en forme, définissez le **Message construit** propriété **Get_StatusRequest**.  
  
 Pour le **assignation du Message** forme, ajoutez le ci-dessous. Avant d’ajouter le code, vous devez avoir :  
  
```  
XmlDoc = new System.Xml.XmlDocument();  
XmlDoc.LoadXml("<GetStatusForConcurrentProgram xmlns='http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR'><RequestId /></GetStatusForConcurrentProgram>");  
Get_StatusRequest = XmlDoc;  
Get_StatusRequest.RequestId = xpath(Response,"string(/*[local-name()='RACUSTResponse']/*[local-name()='RACUSTResult']/text())");  
```  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Pour configurer les ports, vous spécifiez les propriétés répertoriées dans le tableau ci-dessous pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne correspondent aux noms des ports affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*<br />-Créer une opération *Cust_Interface*. Cette opération est utilisée pour le **Interface client** simultanées du programme.<br />-Créer une opération *Get_Status*. Cette opération est utilisée pour le **Get_Status** simultanées du programme.|  
|LOBPort_GetStatus|-Définissez **identificateur** à *LOBPort_GetStatus*<br />-Définissez **Type** à *LOBPort_GetStatusType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les valeurs de propriété pour spécifier des messages pour les formes d’action et les lier aux ports. Les noms répertoriés dans le **forme** colonne correspondent aux noms des formes de message, tel qu’affiché dans le diagramme d’orchestration.  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.Cust_Interface.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBport.Cust_Interface.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBport.Cust_Interface.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.Cust_Interface.Request*|  
|SendGetStatus|-Définissez **Message** à *Get_StatusRequest*<br />-Définissez **opération** à *LOBPort_GetStatus.Get_Status.Request*|  
|ReceiveStatusResponse|-Définissez **Message** à *Get_StatusResponse*<br />-Définissez **opération** à *LOBPort_GetStatus.Get_Status.Response*|  
|SaveStatusResponse|-Définissez **Message** à *Get_StatusResponse*<br />-Définissez **opération** à *ResponseOut.Get_Status.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à Oracle E-Business Suite.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir d’Oracle E-Business Suite.  
  
    -   Définir deux physique de WCF-Custom ou ports d’envoi WCF-OracleEBS : un pour envoyer des messages pour Oracle E-Business Suite pour exécuter la **Interface client** simultanées du programme et l’autre pour exécuter le **Get_Status**simultanées du programme. Vous devez également spécifier l’action dans les ports d’envoi. Pour plus d’informations sur la création de ports, consultez [configuration manuelle d’un Port physique de liaison à l’adaptateur Oracle E-Business](../../adapters-and-accelerators/adapter-oracle-ebs/manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter.md).  
  
         Pour appeler des programmes simultanés à l’aide de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)], vous devez définir le contexte de l’application appropriée dans lequel l’opération est appelée. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] fournit certaines propriétés de liaison pour spécifier le contexte d’application pour toute opération. Vous devez définir ces propriétés de liaison sur le port WCF-Custom ou WCF-OracleEBS utilisé pour appeler des programmes simultanés.  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **base de données**, vous devez spécifier les propriétés de liaison suivantes pour définir le contexte des applications.  
  
            |Propriété de liaison|Valeur|  
            |----------------------|-----------|  
            |**OracleUserName**|Spécifiez le nom d’un utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OracleUserName** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le nom d’utilisateur est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que la casse du nom d’utilisateur doivent être conservés ou si vous souhaitez entrer un nom d’utilisateur contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OraclePassword**|Le mot de passe pour l’utilisateur Oracle E-Business Suite. Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] ne conserve pas la casse de la valeur que vous entrez pour le **OraclePassword** liaison de la propriété lorsqu’il se connecte à Oracle E-Business Suite. Le mot de passe est passé pour Oracle E-Business Suite à l’aide de règles standard de SQL * Plus. Toutefois, si vous souhaitez que le cas du mot de passe doivent être conservés ou si vous souhaitez entrer un mot de passe contenant des caractères spéciaux, vous devez spécifier la valeur entre guillemets doubles.|  
            |**OracleEBSResponsibilityName**|La responsabilité est associée à l’utilisateur Oracle E-Business Suite.|  
  
        -   Si le **ClientCredentialType** liaison de la propriété est définie sur **EBusiness**, vous devez déjà avoir spécifié les informations d’identification de Oracle E-Business lors de l’établissement de la connexion. Dans ce cas, vous devez uniquement spécifier la valeur pour le **OracleEBSResponsibilityName** propriété de liaison.  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour Oracle E-Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md). Pour plus d’informations sur la façon dont l’adaptateur prend en charge la définition du contexte de l’application, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
        > [!NOTE]
        >  Vous pouvez définir le contexte de l’application soit en spécifiant les propriétés de liaison, ou en définissant des propriétés de contexte exposées par le message le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-the-binding-properties-for-oracle-e-business-suite.md). Pour obtenir des instructions sur la façon de définir le contexte de l’application à l’aide des propriétés de contexte de message, consultez [configurer les propriétés de contexte de Message à l’aide de Application contexte dans Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-application-context-using-message-context-properties-in-oracle-ebs.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer un physique Port de liaison avec un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk avant d’appeler les programmes simultanés. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour appeler le **Interface client** simultanées du programme est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-OracleEBS port d’envoi pour appeler le **Get_Status** simultanées du programme est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande qui est conforme au schéma pour l’appel de la **Interface client** simultanées du programme. Par exemple, le message de demande pour appeler le **Interface client** simultanées du programme est :  
  
```  
<RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <Description>Customer Interface Program</Description>  
  <StartTime></StartTime>  
  <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
  <ORG_ID>203</ORG_ID>  
</RACUST>  
```  
  
> [!NOTE]
>  Le message de demande pour appeler un programme simultané requiert des paramètres facultatifs tels que SetOptions, SetPrintOptions et SetRepeatOptions. Le message de demande fourni ici ne contient pas ces paramètres facultatifs. Pour plus d’informations sur le message de demande complète, y compris les paramètres facultatifs, consultez [des schémas de Message pour les programmes simultanés](../../adapters-and-accelerators/adapter-oracle-ebs/message-schemas-for-concurrent-programs.md).  
  
 L’orchestration consomme le message, le transmet à Oracle E-Business Suite et reçoit une réponse. Le message de réponse est enregistré dans l’autre emplacement de fichier spécifié en tant que partie de l’orchestration. La réponse pour le programme simultanée Interface client ressemble à ceci :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<RACUSTResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <RACUSTResult>2794708</RACUSTResult>  
</RACUSTResponse>  
```  
  
 La réponse à partir d’Oracle E-Business Suite contient un ID de demande. Extrait l’ID de demande à partir du message de réponse de l’orchestration, construit un message à appeler le **Get_Status** simultanées du programme et le passe à Oracle E-Business Suite pour exécuter la **Get_Status** simultanées du programme. Une fois que la réponse est reçue pour th **Get_Status** simultanées du programme, il est copié vers le même emplacement de fichier en tant que la première réponse. La réponse pour le **Get_Status** simultanées du programme ressemble à ceci :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<GetStatusForConcurrentProgramResponse xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
  <GetStatusForConcurrentProgramResult>true</GetStatusForConcurrentProgramResult>   
  <Phase>Pending</Phase>   
  <Status>Standby</Status>   
  <DevPhase>PENDING</DevPhase>   
  <DevStatus>STANDBY</DevStatus>   
  <Message>null</Message>   
</GetStatusForConcurrentProgramResponse>  
```  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Après avoir générer un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin créer des éléments tels que des ports d’envoi ports et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de carte avec Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/reuse-adapter-bindings-with-oracle-e-business-suite.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/develop-biztalk-applications-using-the-oracle-e-business-suite-adapter.md)