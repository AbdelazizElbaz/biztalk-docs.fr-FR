---
title: "Recevoir des IDOC SAP à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDOCs, sample (receiving)
- IDOCs, business scenarios for receiving
- IDOCs, receiving from SAP using BizTalk Server
ms.assetid: b904bf07-1108-4ed3-8564-d83eaafff247
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45dc38a939e71a8f4eb3d3afe87736fc548f8570
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-idocs-from-sap-using-biztalk-server"></a>Recevoir des IDOC SAP à l’aide de BizTalk Server
Réception d’un IDOC implique la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] d’agir en tant que RFC serveur pour recevoir un appel RFC spécial à partir de SAP. L’adaptateur SAP peut recevoir des IDOC agissant comme un serveur de RFC ou tRFC. Pour plus d’informations sur la réception d’un IDOC avec l’adaptateur se comporte comme un serveur tRFC, consultez [recevoir des IDOC de SAP dans un contexte transactionnel à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/receive-idocs-from-sap-in-a-transactional-context-using-biztalk-server.md).  
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des deux opérations distinctes pour recevoir des IDOC :  
  
-   **Réception** opération permet de recevoir des IDOC ayant un schéma fortement typée de l’adaptateur.  
  
-   **ReceiveIdoc** opération permet de recevoir des IDOC ayant un schéma faiblement typée de l’adaptateur. Cette opération reçoit IDOC sous forme de chaîne dans un message XML sous la \<idocData > balise.  
  
 Sur le côté de la carte, vous pouvez spécifier une valeur pour le **ReceiveIDocFormat** propriété pour spécifier le format de l’adaptateur doivent recevoir des IDOC de liaison.  
  
-   **Typé** Spécifie l’adaptateur recevra IDOC avec un schéma fortement typé. Il en résulte un IDOC XML.  
  
-   **Chaîne** Spécifie l’adaptateur recevra IDOC avec faiblement typée un schéma. Il en résulte un message XML avec le \<idocData > balise.  
  
-   **RFC** Spécifie l’adaptateur recevra IDOC dans n’importe quel format.  
  
 Pour recevoir des IDOC, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend également en charge un ensemble de propriétés de contexte de message qui permet aux clients de carte dans les orchestrations. Pour obtenir la liste des propriétés, consultez [propriétés de contexte de Message pour recevoir des IDOC](../../adapters-and-accelerators/adapter-sap/message-context-properties-for-receiving-idocs.md).  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge la réception des IDOC à partir d’un système SAP, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md). Pour plus d’informations sur la structure de SOAP des messages pour la réception d’un IDOC, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
## <a name="biztalk-scenarios-for-receiving-idocs-from-an-sap-system"></a>Scénarios de BizTalk pour recevoir des IDOC à partir d’un système SAP  
 Le tableau suivant fournit des scénarios clés de BizTalk pour recevoir des IDOC à partir d’un système SAP :  
  
|Entrée de carte à partir de SAP|Traitement BizTalk|Sortie|  
|-------------------------------|------------------------|------------|  
|IDOC (via l’interface de tRFC)|**Heure de création de métadonnées**<br /><br /> 1.  Définissez la propriété binding GenerateFlatFileCompatibleIdocSchema à **True**.<br />2.  Générer le schéma pour le **réception** opération un IDOC spécifique à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br />3.  Définissez la propriété binding ReceiveIdocFormat à **typé**.<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Recevoir des IDOC de XML.<br />2.  Utilisez l’assembleur de fichier plat pour convertir XML IDOC de fichier plat.|Format de fichier plat IDOC|  
|IDOC (via l’interface de tRFC)|**Heure de création de métadonnées**<br /><br /> 1.  Définissez la propriété binding GenerateFlatFileCompatibleIdocSchema à **True**.<br />2.  Générer le schéma pour le **réception** opération un IDOC spécifique à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br />3.  Définissez la propriété binding ReceiveIdocFormat à **typé**.<br /><br /> **Orchestration au moment du Design**<br /><br /> -Réception IDOC de XML.|XML IDOC|  
|IDOC (via l’interface de tRFC)|**Heure de création de métadonnées**<br /><br /> 1.  Définissez la propriété binding GenerateFlatFileCompatibleIdocSchema à **True**.<br />2.  Générer le schéma pour le **réception** opération un IDOC spécifique à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br />3.  Définissez la propriété binding ReceiveIdocFormat à **chaîne**.<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Réception de message XML avec IDOC de fichier plat dans \<idocData > balise.<br />2.  Utilisez la prise en charge de l’adaptateur WCF XPath dans la configuration de port de réception pour extraire l’IDoc de fichier plat à partir du message XML. Exemple :<br />     `/*[local-name()='ReceiveIdoc']/*[local-name()='idocData']`<br />3.  Utilisez le désassembleur de fichier plat pour convertir des IDOC de fichier plat en XML IDOC.<br /><br /> **Important** cette approche peut être utilisée pour recevoir des IDOC à l’aide de la nouvelle basé sur WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] et de les appliquer directement dans un projet BizTalk existant écrit pour recevoir des IDOC à partir de l’adaptateur BizTalk SAP existante. Il s’agit également l’approche recommandée pour recevoir des IDOC avec le numéro de version inférieur au nombre de version (SYSREL).|XML IDOC|  
|IDOC (via l’interface de tRFC)|**Heure de création de métadonnées**<br /><br /> 1.  Générer le schéma pour le **ReceiveIdoc** opération à partir du nœud IDOC avec [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br />2.  Définissez la propriété binding ReceiveIdocFormat à **chaîne**.<br /><br /> **Moment de la conception d’orchestration**<br /><br /> -Recevoir le message XML avec l’IDOC représenté sous forme de chaîne dans le \<idocData > balise.|IDOC de fichier plat dans le message XML|  
  
## <a name="how-to-receive-an-idoc-from-an-sap-system"></a>La réception d’un IDOC à partir d’un système SAP ?  
 Une opération sur un système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour recevoir un IDOC à partir d’un système SAP, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer un schéma pour l’IDOC que vous souhaitez appeler dans le système SAP. Lors de la génération du schéma Assurez-vous que vous définissez les propriétés de liaison requis, comme indiqué dans le tableau précédent. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système SAP.  
  
3.  Créer une orchestration pour recevoir un IDOC à partir d’un système SAP.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="samples-based-on-this-topic"></a>Exemples en fonction de cette rubrique  
 Exemples, ReceiveIDOC et ReceiveIDOC_SYSREL, en fonction de cette rubrique sont également fournies avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Vous devez générer le schéma pour le *réception* opération de le *ORDERS03. V3.620* IDOC sous le */IDOC/ORDERS/ORDERS03* nœud. Consultez [Parcourir, rechercher et obtenir de métadonnées pour des opérations IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-idoc-operations-in-sap.md) pour obtenir des instructions sur la génération de schéma pour un IDOC particulier. Lors de la génération du schéma, vous pouvez souhaiter définir les propriétés suivantes :  
  
-   *GenerateFlatFileCompatibleIDoc* – génère \<appinfo > balises afin que l’Analyseur de fichier plat BizTalk peut être utilisée dans les scénarios de BizTalk pour prendre en charge le format de fichier plat IDOC.  
  
-   *FlatFileSegmentIndicator* – indique si le schéma IDOC \<appinfo > balises doivent contenir les noms de définition des segments ou des noms de type de segment. Cela s’applique lorsqu’un veut utilisé pour envoyer/recevoir un fichier plat IDOC de SAP. Si le *GenerateFlatFileCompatibleIDoc* est définie sur false, puis *FlatFileSegmentIndicator* liaison de la propriété est ignorée.  
  
> [!IMPORTANT]
>  Étant donné que vous générez le schéma d’un appel d’IDOC entrant, veillez à sélectionner **Service (opération entrante)** à partir de la **sélectionner type de contrat** liste déroulante dans le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)].  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour recevoir un IDOC à partir du système SAP et l’autre pour envoyer une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajoutez une nouvelle orchestration au projet BizTalk.  
  
2.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ReceiveIDOC.SAPBindingSchema2*, où *ReceiveIDOC* est le nom de votre projet BizTalk. *SAPBindingSchema2* est le schéma généré pour l’opération de réception.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ReceiveIDOC.SAPBindingSchema3*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir des IDOC à partir du système SAP. Dans un scénario classique, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] reçoit un appel IDOC à partir du système SAP, traite la demande et transmet la réponse au système SAP. Pour cela dans le cadre d’une orchestration, l’orchestration doit contenir :  
  
-   Un double port de réception pour recevoir des IDOC à partir du système SAP et envoyer la réponse.  
  
-   Envoyer et recevoir des formes.  
  
-   Forme construire un Message, dans laquelle une forme assignation du Message, pour générer une réponse à envoyer au système SAP.  
  
    > [!NOTE]
    >  Si l’orchestration inclut un double port de réception (requête-réponse) pour recevoir des IDOC à partir du système SAP, l’orchestration doit envoyer une réponse au système SAP. Si ce n’est pas le cas, le système SAP n’envoie pas l’IDOC suivant. Toutefois, si le port de réception unidirectionnel, l’orchestration n’a pas envoyer une réponse au système SAP.  
  
-   Un port d’envoi unidirectionnel pour envoyer l’IDOC reçus à partir du système SAP dans un dossier.  
  
 Un exemple d’orchestration pour recevoir un IDOC à partir d’un système SAP ressemble à :  
  
 ![Orchestration permettant de recevoir des IDOC](../../adapters-and-accelerators/adapter-sap/media/20d4f251-2474-4fd5-becd-2915f9efa81b.gif "20d4f251-2474-4fd5-becd-2915f9efa81b")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ListenToSAP|Recevoir|-Définissez **nom** à *ListenToSAP*<br /><br /> -Définissez **activer** à *True*|  
|SaveIDOC|Send|-Définissez **nom** à *SaveIDOC*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-construct-message-shape"></a>Ajout de forme construire un Message  
 Dans l’orchestration, vous devez générer une réponse et envoyez-le au système SAP. Pour ce faire, vous devez ajouter une forme construire un Message et dans ce la forme assignation du Message à votre orchestration. La forme assignation du Message appelle le code qui génère un message de réponse est envoyé au système SAP. La forme assignation du Message définit également l’action pour la réponse à envoyer au système SAP.  
  
> [!IMPORTANT]
>  Si l’orchestration inclut un double port de réception (requête-réponse) pour recevoir des IDOC à partir du système SAP, l’orchestration doit envoyer une réponse au système SAP. Si ce n’est pas le cas, le système SAP n’envoie pas l’IDOC suivant. Toutefois, si le port de réception unidirectionnel, l’orchestration n’a pas envoyer une réponse au système SAP.  
  
 Pour la forme construire un message, définissez la **Message construit** propriété **réponse**.  
  
 Le code pour générer la réponse peut faire partie de la même solution Visual Studio en tant que votre projet BizTalk. Un exemple de code pour générer un message de réponse ressemble à ceci.  
  
```  
namespace IdocReceiveResponseMessageCreator  
{  
    public class IdocReceiveResponseMessageCreator  
    {  
        private static XmlDocument Message;  
        private static string XmlFileLocation;  
        private static string ResponseDoc;  
  
        public static XmlDocument XMLMessageCreator()  
        {  
            XmlFileLocation = "C:\\test\\in";  
            try  
            {  
                ResponseDoc = (Directory.GetFiles(XmlFileLocation, "*.xml", SearchOption.TopDirectoryOnly))[0];  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Trying to get XML from: " + XmlFileLocation);  
                Console.WriteLine("EXCEPTION: " + ex.ToString());  
                throw ex;  
            }  
            //Create Message From XML  
            Message = new XmlDocument();  
            Message.PreserveWhitespace = true;  
            Message.Load(ResponseDoc);  
            return Message;  
        }   
    }  
}  
```  
  
> [!NOTE]
>  Une fois que vous générez le projet, IdocReceiveResponseMessageCreator.dll sera créé dans le répertoire du projet. Vous devez ajouter cette DLL dans le global assembly cache (GAC).  
  
 Ajoutez l’expression suivante pour appeler ce code à partir de la forme assignation du Message et définir l’action de la réponse envoyée au système SAP. Pour ajouter une expression, double-cliquez sur la forme assignation du Message pour ouvrir l’éditeur d’Expression.  
  
```  
Response = IdocReceiveResponseMessageCreator.IdocReceiveResponseMessageCreator.XMLMessageCreator();  
Response(WCF.Action)= "http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response";  
```  
  
> [!IMPORTANT]
>  Vous devez définir explicitement l’action du message de réponse. Si vous ne définissez pas l’action, l’adaptateur WCF-Custom arrive sur le message d’action en ajoutant « Réponse » à l’action de demande. Par conséquent, l’action pour le message de réponse devient `http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/ReceiveResponse`. Toutefois, le sapBinding attend l’action de réponse en ajoutant « / réponse » à l’action de la demande, par exemple `http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS03//620/Receive/response`.  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour le port logique. Le nom indiqué dans le *Port* colonne est le nom du port, tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|ReceiveIDOCPort|-Définissez **identificateur** à *ReceiveIDOCPort*<br /><br /> -Définissez **Type** à *ReceiveIDOCPortType*<br /><br /> -Définissez **modèle de Communication** à *demande-réponse*<br /><br /> -Définissez **Direction de Communication** à *de réception-envoi*|  
|GetIDOCPort|-Définissez **identificateur** à *GetIDOCPort*<br /><br /> -Définissez **Type** à *GetIDOCPortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
> [!IMPORTANT]
>  Si l’orchestration inclut un double port de réception (requête-réponse) pour recevoir des IDOC à partir du système SAP, l’orchestration doit envoyer une réponse au système SAP. Si ce n’est pas le cas, le système SAP n’envoie pas l’IDOC suivant.  
  
### <a name="adding-a-flat-file-assembler"></a>Ajout d’un assembleur de fichier plat  
 Vous devez ajouter un assembleur pour convertir le message entrant IDOC vers un fichier plat.  
  
##### <a name="to-add-a-flat-file-assembler"></a>Pour ajouter un assembleur de fichier plat  
  
1.  Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis sélectionnez **un nouvel élément**.  
  
2.  À partir de la boîte de dialogue, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Catégories|Fichiers de pipeline|  
    |Modèles Visual Studio installés|Pipeline d'envoi|  
    |Nom|SendIDOC|  
  
3.  Le Concepteur de Pipeline s’ouvre. À partir de la **composants de Pipeline BizTalk** boîte à outils, faites glisser le **assembleur de fichier plat** composant de pipeline dans le **assemblage** étape du pipeline d’envoi.  
  
4.  À partir de la **propriétés du composant de Pipeline** afficher, spécifiez une valeur pour le **schéma de Document** propriété. Dans la liste déroulante. Veillez à sélectionner le schéma correspondant à l’IDOC opération de réception.  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ListenToSAP|-Définissez **Message** à *demande*<br /><br /> -Définissez **opération** à *ReceiveIDOCPort.ReceiveIDOC.Request*|  
|SaveIDOC|-Définissez **Message** à *demande*<br /><br /> -Définissez **opération** à *GetIDOCPort.ReceiveIDOC.Request*|  
|SendResponse|-Définissez **Message** à *réponse*<br /><br /> -Définissez **opération** à *ReceiveIDOCPort.ReceiveIDOC.Response*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md)
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir les emplacements d’envoi et de port d’envoi physique. Cet emplacement contient l’IDOC provenant du système SAP.  
  
        > [!IMPORTANT]
        >  Pour le pipeline XMLTransmit, veillez à sélectionner ***SendIDOC***. Vous avez créé ce pipeline dans le cadre du projet BizTalk.  
  
    -   Définir un WCF-Custom ou port de réception WCF-SAP. Ce port recevra un IDOC entrant à partir du système SAP et passez-la à l’orchestration. Ce port envoie également la réponse au système SAP. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).
  
        > [!IMPORTANT]
        >  Assurez-vous que la propriété de liaison **ReceiveIDocFormat** a la valeur **typé**.  
  
        > [!IMPORTANT]
        >  Si la propriété de liaison **EnableBizTalkCompatibilityMode** a la valeur est true, assurez-vous d’ajouter le fichier DLL du schéma de propriété BizTalk pour le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] en tant que ressource dans votre application BizTalk, autrement dit, l’application dans laquelle votre projet est déployé. Pour obtenir des instructions sur l’ajout de ressources, consultez [dépanner les problèmes opérationnels avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/troubleshoot-operational-issues-with-the-sap-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
 Vous devez également ajouter l’assembly pour le projet IdocReceiveResponseMessageCreator à votre application BizTalk. Vous avez créé ce projet pour générer la réponse à envoyer au système SAP. Pour cela :  
  
1.  Dans l’arborescence de la console sur le côté gauche de la console Administration de BizTalk Server, sous l’application BizTalk où vous avez importé les liaisons, cliquez sur **ressources**, pointez sur **ajouter** puis cliquez sur **Assemblys BizTalk**.  
  
2.  Dans le **ajouter des ressources** boîte de dialogue, cliquez sur **ajouter** et accédez au dossier contenant IdocReceiveResponseMessageCreator.dll. Sélectionnez le fichier, puis cliquez **ouvrir**.  
  
3.  Dans le **ajouter des ressources** boîte de dialogue, cliquez sur **OK**.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour la réception d’un IDOC à partir du système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md), ou [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).
  
 À ce stade, vérifiez que :  
  
-   Le port d’envoi de fichier pour enregistrer l’IDOC entrant vers un emplacement de fichier est en cours d’exécution.  
  
-   Le WCF-Custom ou WCF-SAP port de réception pour recevoir des IDOC de SAP système est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez accéder au système SAP et envoyer un IDOC dans l’adaptateur. L’adaptateur reçoit l’IDOC et l’enregistre dans un emplacement de fichier spécifié dans le cadre de l’orchestration.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de la réception d’un IDOC à partir d’un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)