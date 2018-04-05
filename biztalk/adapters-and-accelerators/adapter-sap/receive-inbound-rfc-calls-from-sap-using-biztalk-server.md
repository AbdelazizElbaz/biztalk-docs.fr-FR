---
title: Recevoir des appels de RFC entrants à partir de SAP à l’aide de BizTalk Server | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RFC calls, receiving using BizTalk Server
ms.assetid: 822fd9fb-772f-4910-a11e-25c1d5dca6e1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b949ae0d6d5938493c78ed542a67d3c8bd09b48
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-inbound-rfc-calls-from-sap-using-biztalk-server"></a>Recevoir des appels de RFC entrants à partir de SAP à l’aide de BizTalk Server
Dans un scénario de serveur RFC, il existe trois entités :  
  
-   Un client SAP qui envoie une demande à SAP pour appeler une commande RFC. Ceci pourrait être invoqué à l’aide de l’interface utilisateur graphique SAP ou en effectuant un client RFC appeler via le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Le système SAP qui contient une définition de fonction RFC qui appelle par le client SAP. Le système SAP transmet la demande au serveur RFC (l’adaptateur). Il est utilisé par l’adaptateur pour accéder aux métadonnées de l’appel RFC qu’au serveur SAP à l’adaptateur.  
  
-   Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] qui fait Office de serveur RFC et héberge le document RFC réel.  
  
 La première entité, le client SAP, n’est pas traitée dans cette rubrique. Si vous utilisez l’interface utilisateur graphique SAP pour appeler une commande RFC, reportez-vous à la documentation de SAP. Si vous utilisez la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour appeler une commande RFC, consultez [appeler les RFC dans SAP par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md).  
  
 Cette section fournit des instructions sur l’utilisation de l’adaptateur pour recevoir un appel de serveur RFC, une fois que le document RFC est appelé par un client SAP. Pour plus d’informations sur comment l’adaptateur prend en charge la réception RFC server appelle à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], consultez [opérations sur les documents RFC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md).  
  
## <a name="how-to-receive-an-inbound-rfc-call-from-the-sap-system"></a>La réception d’un appel entrant RFC à partir du système SAP ?  
 Une opération sur un système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour recevoir un appel RFC à partir du système SAP, ces tâches sont :  
  
1.  Configurer votre système SAP pour envoyer les RFC à une application externe, dans ce cas le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
2.  Créez un projet BizTalk et générer le schéma pour le document RFC qui le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] recevra à partir du système SAP.  
  
3.  Créer des messages dans le projet BizTalk pour recevoir des messages à partir du système SAP et l’envoi des réponses.  
  
4.  Créez une orchestration pour recevoir une demande de changement à partir du système SAP, traiter et envoyer la réponse au système SAP.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
7.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="activities-on-the-sap-system"></a>Activités sur le système SAP  
 Avant d’utiliser le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour recevoir des appels RFC entrants à partir du système SAP, assurez-vous d’effectuer les tâches suivantes sur le système SAP.  
  
-   Une destination RFC de l’adaptateur SAP doit exister. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] reçoit les RFC à partir du système SAP via une destination RFC défini sur le système SAP. La destination RFC contient l’hôte de passerelle SAP, le Service de passerelle SAP et l’ID de programme SAP que vous devez spécifier dans l’URI de connexion dans votre code. Pour plus d’informations sur la configuration d’une destination RFC sur SAP, consultez [créer une demande de changement, la destination RFC et envoyer une demande de changement à partir du système SAP](creating-an-rfc-in-an-sap-system.md).  
  
-   Vous devez créer un module de fonction qui définit la RFC sur le système SAP. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise la définition de la RFC sur le système SAP pour récupérer des métadonnées sur le document RFC (à la fois au moment du design et au moment de l’exécution). Pour plus d’informations, consultez [création d’une commande RFC dans un système SAP](../../adapters-and-accelerators/adapter-sap/creating-an-rfc-in-an-sap-system.md).  
  
     Voici un exemple de code source sur le système SAP pour une commande RFC qui ajoute deux entiers et retourne son résultat. Le code appelle simplement la RFC via une destination spécifique. L’implémentation de la fonction est effectuée par le code client de l’adaptateur SAP.  
  
    ```  
    FUNCTION Z_RFC_ADD.  
    *"------------------------------------------------------------------  
    *"  
    *"Local interface:  
    *"  IMPORTING  
    *"     VALUE(X) TYPE  INT4  
    *"     VALUE(Y) TYPE  INT4  
    *"     VALUE(DEST) TYPE  CHAR20 DEFAULT 'SAPADAPTER'  
    *"  EXPORTING  
    *"     VALUE(RESULT) TYPE  INT4  
    *"------------------------------------------------------------------  
    CALL FUNCTION 'Z_RFC_ADD' DESTINATION DEST  
      EXPORTING X = X  
                Y = Y  
      IMPORTING RESULT = RESULT.  
  
    ENDFUNCTION.  
    ```  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, RFCServer, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
## <a name="generating-the-schema"></a>Générer le schéma  
 Dans cette rubrique, pour illustrer comment recevoir un appel RFC entrant à partir du système SAP, nous générer le schéma pour *Z_RFC_ADD* RFC. Vous avez créé cette RFC à l’étape précédente. Ce document RFC accepte deux valeurs entières en tant que paramètres d’entrée.  
  
 Consultez [Parcourir, rechercher et obtenir de métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) pour obtenir des instructions sur la génération de schéma pour une demande de changement particulier.  
  
> [!IMPORTANT]
>  Étant donné que vous générez le schéma d’un appel RFC entrant, veillez à sélectionner **Service (opération entrante)** à partir de la **sélectionner type de contrat** liste déroulante dans le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour recevoir des messages à partir du système SAP et l’autre pour envoyer une réponse au système SAP.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajoutez une nouvelle orchestration au projet BizTalk.  
  
2.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *RFCServer.SAPBindingSchema.Z_RFC_ADD*, où *RFCServer* est le nom de votre projet BizTalk. *SAPBindingSchema* est le schéma généré pour le document RFC *Z_RFC_ADD*.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *RFCServer.SAPBindingSchema.Z_RFC_ADDResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des appels de serveur RFC à partir du système SAP. Pour cet exemple, imaginez un scénario où un client RFC envoie une demande au système SAP pour ajouter deux entiers. Le système SAP accepte la demande, avec les paramètres d’entrée et le transmet au serveur RFC externe hébergé par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] reçoit la demande à partir du système SAP, processus de la demande d’ajout de deux entiers et génère une réponse. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] transmet la réponse au système SAP, qui à son tour, est passé au client RFC.  
  
 Pour cela dans le cadre d’une orchestration, l’orchestration doit contenir :  
  
-   Un double port de réception pour recevoir la demande au serveur RFC à partir du système SAP et envoyer la réponse.  
  
-   Envoyer et recevoir des formes.  
  
-   Forme construire un Message, et dans ce une forme assignation du Message, pour traiter la demande de serveur RFC en provenance du système SAP.  
  
 Un exemple d’orchestration pour un appel de serveur RFC semblable au suivant.  
  
 ![Orchestration permettant d’appeler serveur RFC](../../adapters-and-accelerators/adapter-sap/media/f5da2947-56d6-41f0-b411-c8e6eacf68cd.gif "f5da2947-56d6-41f0-b411-c8e6eacf68cd")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ListenToSAP|Recevoir|-Définissez **nom** à *ListenToSAP*<br />-Définissez **activer** à *True*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-construct-message-shape"></a>Ajout de forme construire un Message  
 Pour traiter l’appel RFC entrant pour ajouter deux valeurs entières, vous devez ajouter une forme construire un Message et dans laquelle une forme assignation du Message à votre orchestration, entre les deux formes d’envoi. Pour cet exemple, la forme assignation du Message appelle pour ajouter deux entiers. La forme assignation du Message définit également l’action pour la réponse à envoyer au système SAP.  
  
 Pour la forme construire un Message, définissez la **Message construit** propriété **réponse**.  
  
 Le code pour traiter la demande RFC peut faire partie de la même solution Visual Studio en tant que votre projet BizTalk. En Voici un exemple de code pour l’ajout de deux entiers.  
  
```  
namespace RFCServerResponseCreator  
{  
    public class RFCServerResponseCreator  
    {  
        private static XmlDocument messageIn;  
        private static XmlDocument messageOut;  
        public static XmlDocument CreateRequest(int a, int b, string destination)  
        {  
            messageIn = new XmlDocument();  
            messageIn.LoadXml(  "<Z_RFC_ADD xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<DEST>" + destination + "</DEST>" +  
                                "<X>" + a + "</X>" +  
                                "<Y>" + b + "</Y>" +   
                                "</Z_RFC_ADD>"  
                             );  
            return messageIn;  
        }  
        public static XmlDocument CreateResponse(int a, int b)  
        {  
            int c = a + b;  
            messageOut = new XmlDocument();  
            messageOut.LoadXml( "<Z_RFC_ADDResponse xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\">" +  
                                "<RESULT>" + c + "</RESULT>" +   
                                "</Z_RFC_ADDResponse>"  
                              );  
            return messageOut;  
        }  
    }  
}  
```  
  
> [!NOTE]
>  Une fois que vous générez le projet, RFCServerResponseCreator.dll sera créé dans le répertoire du projet. Vous devez ajouter cette DLL dans le global assembly cache (GAC).  
  
 Ajoutez l’expression suivante pour appeler ce code à partir de la forme assignation du Message et définir l’action de la réponse envoyée au système SAP. Pour ajouter une expression, double-cliquez sur la forme assignation du Message pour ouvrir l’éditeur d’Expression.  
  
```  
Response = RFCServerResponseCreator.RFCServerResponseCreator.CreateResponse(Request.X, Request.Y);  
Response(WCF.Action) = "http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response";  
```  
  
> [!IMPORTANT]
>  Vous devez définir explicitement l’action du message de réponse. Si vous ne définissez pas l’action, l’adaptateur WCF-Custom arrive sur le message d’action en ajoutant « Réponse » à l’action de demande. Par conséquent, l’action pour le message de réponse devient `http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADDResponse`. Toutefois, le sapBinding attend l’action de réponse en ajoutant « / réponse » à l’action de la demande, par exemple `http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_ADD/response`.  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour le port logique. Le nom indiqué dans le *Port* colonne est le nom du port, tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|RFCServerPort|-Définissez **identificateur** à *RFCServerPort*<br />-Définissez **Type** à *RFCServerPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *de réception-envoi*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ListenToSAP|-Définissez **Message** à *demande*<br />-Définissez **opération** à *RFCServerPort.Add.Request*|  
|SendResponse|-Définissez **Message** à *FuncResponse*<br />-Définissez **opération** à *RFCServerPort.Add.Response*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un WCF-Custom ou port de réception WCF-SAP. Ce port reçoit les appels RFC entrants à partir du système SAP et envoie la réponse au système SAP. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
 Vous devez également ajouter l’assembly pour le projet RFCServerResponseCreator à votre application BizTalk. Vous avez créé ce projet pour traiter l’appel RFC reçu du système SAP. Pour cela :  
  
1.  Dans l’arborescence de la console sur le côté gauche de la console Administration de BizTalk Server, sous l’application BizTalk où vous avez importé les liaisons, cliquez sur **ressources**, pointez sur **ajouter**, puis cliquez sur **Assemblys BizTalk**.  
  
2.  Dans le **ajouter des ressources** boîte de dialogue, cliquez sur **ajouter**, puis accédez au dossier contenant RFCServerResponseCreator.dll. Sélectionnez le fichier, puis cliquez **ouvrir**.  
  
3.  Dans le **ajouter des ressources** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour la réception des appels RFC entrants à partir d’un système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md), et [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SAP port de réception pour recevoir des appels RFC à partir de SAP système est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez envoyer une demande de changement pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous pouvez le faire en exécutant la transaction SE37 sur le système SAP. Vous devez également spécifier les paramètres d’entrée pour l’appel de RFC. L’adaptateur reçoit l’appel ainsi que les paramètres, la traite et envoie la réponse au système SAP. Vous serez en mesure d’afficher la réponse dans la même transaction à partir de laquelle vous avez envoyé la demande de changement.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de la réception d’un appel de serveur RFC à partir d’un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)