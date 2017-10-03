---
title: "Appeler tRFCs dans SAP à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tRFCs, invoking using BizTalk Server
ms.assetid: 9489adca-cf2c-4e15-8573-445acd7ebf73
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c68953a1846e8606df79dbdb8b74920ee4d5015
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoke-trfcs-in-sap-using-biztalk-server"></a>Appeler tRFCs dans SAP à l’aide de BizTalk Server
Appels de fonction distants transactionnelle (tRFCs) garantit une seul d’exécution d’une demande de changement sur un système SAP. Vous pouvez appeler une des RFC exposés par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] comme un tRFC. L’appel d’un tRFC est similaire à l’appel d’une commande RFC (consultez [appeler les RFC dans SAP par à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-rfcs-in-sap-using-biztalk-server.md)) avec les différences suivantes :  
  
-   Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] surfaces tRFCs sous un nœud différent (**TRFC**) que les documents RFC (**RFC**).  
  
-   les opérations tRFC incluent un paramètre GUID qui est mappé à l’ID de Transaction SAP pour le tRFC par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   Une fois que vous appelez un tRFC, vous devez appeler l’opération RfcConfirmTransID pour confirmer (commit) le tRFC sur le système SAP. Cette opération apparaissent directement sous le **TRFC** nœud [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge de l’appel d’un tRFC, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). Pour plus d’informations sur la structure de SOAP des messages pour l’appel d’un tRFC, consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md).  
  
## <a name="how-to-invoke-a-trfc-in-an-sap-system-using-biztalk-server"></a>Explique comment appeler une tRFC dans une SAP système à l’aide de BizTalk Server ?  
 Une opération sur un système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour appeler un tRFC dans un système SAP, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour le tRFC que vous souhaitez appeler dans le système SAP. Vous devez également générer le schéma pour le **RfcConfirmTransID** opération pour valider le TID dans le système SAP.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système SAP.  
  
3.  Créer une orchestration pour appeler un tRFC dans le système SAP puis de valider le TID est créé dans le système SAP en réponse à l’appel de tRFC par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, tRFCClient, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples à partir de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment appeler un tRFC à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)], nous allons générer le schéma pour :  
  
-   *BAPI_SALESORDER_CREATEFROMDAT2* tRFC.  
  
-   Opération RfcConfirmTransID. Vous devez utiliser cette opération pour valider le TID est créé dans le système SAP. Une fois que le système SAP reçoit cet appel, qu'il supprime le TID du système.  
  
 Consultez [Parcourir, rechercher et d’obtenir des métadonnées pour des opérations dans SAP tRFC](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-trfc-operations-in-sap.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma que vous avez généré pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer quatre messages, un message de demande-réponse pour invoquer la tRFC et un autre message de demande-réponse définie pour appeler l’opération RfcConfirmTransID.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez le type de message. Par exemple, sélectionnez *tRFC_Client.SAPBindingSchema1.BAPI_SALESORDER_CREATEFROMDAT2*, où *tRFC_Client* est le nom de votre projet BizTalk. *SAPBindingSchema1* est le schéma généré pour *BAPI_SALESORDER_CREATEFROMDAT2*.|  
  
5.  Répétez l’étape précédente pour créer plus de trois messages. Dans le **propriétés** volet pour les nouveaux messages, procédez comme suit.  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Réponse|*tRFC_Client.SAPBindingSchema1.BAPI_SALESORDER_CREATEFROMDAT2Response*|  
    |TIDRequest|*tRFC_Client.SAPBindingSchema3.RfcConfirmTransID*|  
    |TIDResponse|*tRFC_Client.SAPBindingSchema3.RfcConfirmTransIDResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler tRFCs dans un système SAP. Dans cette orchestration, vous supprimez un message de demande à une emplacement de réception. L’orchestration traite ce message et le transmet au système SAP. La réponse est reçue à partir de SAP et est enregistrée dans un autre emplacement. Le message de réponse contient un GUID. L’orchestration inclut un **construire un Message** forme pour extraire le GUID de la réponse et construire un message qui est conforme au schéma de la **RfcConfirmTransID** opération. Le message pour appeler le **RfcConfirmTransID** opération est envoyée au système SAP avec le GUID comme un paramètre _ une orchestration classique permettant d’appeler tRFCs dans un système SAP, suivi d’un **RfcConfirmTransID**opération contient :  
  
-   Envoyer et recevoir des formes pour envoyer des messages au système SAP et de recevoir des réponses.  
  
-   Forme construire un Message et dans qui forme une assignation du Message de construire un message pour le **RfcConfirmTransID** opération.  
  
-   Port pour recevoir des messages de demande à envoyer au système SAP pour appeler le tRFC de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages à appeler le tRFC et recevoir la réponse.  
  
-   Un double port d’envoi pour envoyer des messages à appeler le **RfcConfirmTransID** opération et recevoir la réponse.  
  
-   Unidirectionnel deux ports d’envoi pour envoyer les réponses à partir du système SAP dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration permettant d’appeler un client tRFC](../../adapters-and-accelerators/adapter-sap/media/369d62dd-9ae4-4673-b346-03d2acfb453a.gif "369d62dd-9ae4-4673-b346-03d2acfb453a")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveXml|Recevoir|-Définissez **nom** à *ReceiveXml*<br />-Définissez **activer** à *True*|  
|SendToLOB|Send|-Définissez **nom** à *SendToLOB*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
|SendTIDMsg|Send|-Définissez **nom** à *SendTIDMsg*|  
|ReceiveTIDRsp|Recevoir|-Définissez **nom** à *ReceiveTIDRsp*<br />-Définissez **activer** à *False*|  
|SendTIDRsp|Send|-Définissez **nom** à *SendTIDRsp*|  
  
### <a name="adding-the-construct-message-shape"></a>Ajout de la forme construire un Message  
 La réponse à partir du système SAP pour l’appel de tRFC contient un GUID. Pour valider l’appel de tRFC, vous devez passer le même GUID pour l’opération RfcConfirmTransID. Pour ce faire, vous devez inclure une forme construire un Message, et dans ce forme assignation du Message, dans l’orchestration. Ici, l’objectif de la forme construire un Message est :  
  
-   Pour extraire le GUID de la réponse est reçue à partir du système SAP pour l’appel de tRFC.  
  
-   Pour construire un message conforme au schéma de message pour l’opération RfcConfirmTransID.  
  
 Pour la forme construire un Message, vous devez définir le **Message construit** propriété **TIDRequest**.  
  
 Vous devez ajouter l’extrait de code suivant à la forme assignation du Message :  
  
```  
XmlDoc = new System.Xml.XmlDocument();  
XmlDoc.LoadXml("\<RfcConfirmTransID xmlns='http://Microsoft.LobServices.Sap/2007/03/RfcApi/'><TransactionalRfcOperationIdentifier /></RfcConfirmTransID>");  
TIDRequest = XmlDoc;  
TIDRequest.TransactionalRfcOperationIdentifier = xpath(Response,"string(/*[local-name()='BAPI_SALESORDER_CREATEFROMDAT2Response']/*[local-name()='TransactionalRfcOperationIdentifier']/text())");  
```  
  
 Pour utiliser l’extrait de code ci-dessus, vous devez :  
  
-   Création d’une variable, **XmlDoc**, dans votre BizTalk de projet et définissez son type sur System.Xml.XmlDocument. Pour plus d’informations sur la création des variables, consultez [à l’aide de Variables dans les Orchestrations](../../core/using-variables-in-orchestrations.md).
  
-   Promouvoir le **TransactionalRfcOperationIdentifier** propriété dans le schéma pour l’opération de RfcConfirmTransID. Pour plus d’informations sur la promotion d’une propriété, consultez [promotion des propriétés](../../core/promoting-properties.md).
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInPortType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|tRFC_Port|-Définissez **identificateur** à *tRFC_Port*<br />-Définissez **Type** à *tRFC_PortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SavetRFCResponse|-Définissez **identificateur** à *SavetRFCResponse*<br />-Définissez **Type** à *SavetRFCResponsePortType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
|TID_Port|-Définissez **identificateur** à *TID_Port*<br />-Définissez **Type** à *TIDPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveTIDResponse|-Définissez **identificateur** à *SaveTIDResponse*<br />-Définissez **Type** à *SaveTIDResponsePortType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveXml|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.tRFC.Request*|  
|SendToLOB|-Définissez **Message** à *demande*<br />-Définissez **opération** à *tRFC_Port.tRFC.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *tRFC_Port.tRFC.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SavetRFCResponse.tRFC.Request*|  
|SendTIDMsg|-Définissez **Message** à *TIDRequest*<br />-Définissez **opération** à *TID_Port.TID.Request*|  
|ReceiveTIDRsp|-Définissez **Message** à *TIDResponse*<br />-Définissez **opération** à *TID_Port.TID.Response*|  
|SendTIDRsp|-Définissez **Message** à *TIDResponse*<br />-Définissez **opération** à *SaveTIDResponse.TID.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk utilise le message de demande à envoyer au système SAP.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.  
  
    -   Définir physique WCF-Custom ou WCF-SAP les ports (une pour le message de demande tRFC et le message RfcConfirmTransID) d’envoi pour envoyer des messages au système SAP. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk permettant d’appeler tRFCs dans un système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md), ou [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Les ports d’envoi WCF-Custom ou WCF-SAP pour envoyer des messages au système SAP sont en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour l’orchestration. Consultez [des schémas de Message pour des opérations tRFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-trfc-operations.md) savoir sur le schéma du message de demande pour l’appel d’un tRFC dans un système SAP. Par exemple, le message de demande pour appeler BAPI_SALEASORDER_CREATEFROMDAT2 comme un tRFC est la suivante :  
  
```  
<BAPI_SALESORDER_CREATEFROMDAT2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Trfc/">  
  <ORDER_HEADER_IN>  
    <DOC_TYPE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">TA</DOC_TYPE>  
    <SALES_ORG xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">1000</SALES_ORG>  
    <DISTR_CHAN xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">10</DISTR_CHAN>  
    <DIVISION xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">00</DIVISION>  
    <SALES_OFF xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">1000</SALES_OFF>  
    <REQ_DATE_H xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006-09-01T23:50:00</REQ_DATE_H>  
    <PURCH_DATE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">2006-08-25T23:50:00</PURCH_DATE>  
    <PURCH_NO_C xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">Cust PO</PURCH_NO_C>  
    <CURRENCY xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">EUR</CURRENCY>  
  </ORDER_HEADER_IN>  
  <ORDER_ITEMS_IN>  
    <BAPISDITM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <MATERIAL>P-109</MATERIAL>  
      <PLANT>1000</PLANT>  
      <TARGET_QU>ST</TARGET_QU>  
    </BAPISDITM>  
  </ORDER_ITEMS_IN>  
  <ORDER_PARTNERS>  
    <BAPIPARNR xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <PARTN_ROLE>AG</PARTN_ROLE>  
      <PARTN_NUMB>0000001390</PARTN_NUMB>  
    </BAPIPARNR>  
  </ORDER_PARTNERS>  
  <RETURN/>  
  <TransactionalRfcOperationIdentifier>def689b1-b514-4627-a861-d6d7f51c84e3</TransactionalRfcOperationIdentifier>  
</BAPI_SALESORDER_CREATEFROMDAT2>  
```  
  
 L’orchestration consomme le message, il transmet une session sur le système SAP et reçoit une réponse à partir du système SAP. Le message de réponse est enregistré dans l’autre emplacement de fichier spécifié en tant que partie de l’orchestration. La réponse du système SAP contient un GUID. L’orchestration puis génère un autre message de demande à partir de la réponse et les transmet au système SAP pour exécuter le RfcConfirmTransID. Une fois la réponse reçue à partir du système SAP pour l’opération RfcConfirmTransID, il est copié dans l’emplacement du fichier. Pour résumer, une fois que l’opération est exécutée avec succès :  
  
-   Un message de réponse à partir de SAP pour appeler le tRFC est copié dans l’emplacement du fichier. Contient le même GUID qui a été envoyé au système SAP. Le message de réponse appel BAPI_SALESORDER_CREATEFROMDAT2 comme un tRFC est :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8"?>  
    <BAPI_SALESORDER_CREATEFROMDAT2Response xmlns="http://Microsoft.LobServices.Sap/2007/03/Trfc/">  
      <TransactionalRfcOperationIdentifier>def689b1-b514-4627-a861-d6d7f51c84e3</TransactionalRfcOperationIdentifier>  
    </BAPI_SALESORDER_CREATEFROMDAT2Response>  
    ```  
  
-   Un message de réponse pour la RfcConfirmTransID est copié vers le même emplacement. Il s’agit d’une réponse vide. Le message de réponse pour la RfcConfirmTransID est la suivante :  
  
    ```  
    \<?xml version="1.0" encoding="utf-8"?>  
    <RfcConfirmTransIDResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/RfcApi/"></RfcConfirmTransIDResponse>  
    ```  
  
> [!NOTE]
>  Vous pouvez utiliser la **ConvertGuidToTid()** méthode publique exposée par l’assembly d’adaptateur SAP pour récupérer le TID dans le système SAP mappé au GUID. Pour plus d’informations, consultez [des opérations spéciales](../../adapters-and-accelerators/adapter-sap/special-operations.md).  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de l’appel d’un tRFC dans un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)