---
title: "Appeler les RFC dans SAP à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: RFCs, invoking using BizTalk Server
ms.assetid: cc859ca2-aa9a-48fd-a941-ae28bee96f06
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3db5180d8b4183a2a48c726fd5e73b3347f82dc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-rfcs-in-sap-using-biztalk-server"></a>Appeler les RFC dans SAP à l’aide de BizTalk Server
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence les RFC exposées par un système SAP en tant qu’opérations qui peuvent être appelées par un client de carte. Cette section fournit des instructions sur l’appel d’une commande RFC dans un système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge de l’appel d’une commande RFC dans un système SAP, consultez [opérations sur les documents RFC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-rfcs-in-sap.md). Pour plus d’informations sur la structure du message SOAP pour appeler une commande RFC, consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md).  
  
## <a name="how-to-invoke-an-rfc-in-an-sap-system"></a>Explique comment appeler une commande RFC dans un système SAP ?  
 Une opération sur un système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour appeler une commande RFC dans un système SAP, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma de la RFC que vous souhaitez appeler dans le système SAP.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système SAP.  
  
3.  Créez une orchestration pour appeler une commande RFC dans le système SAP.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment appeler une commande RFC dans un système SAP, nous générer le schéma pour *RFC_CUSTOMER_GET*. Consultez [Parcourir, rechercher et d’obtenir les métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma que vous avez généré pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour envoyer une demande au système SAP et l’autre pour recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GET*, où *InvokeRFC* est le nom de votre projet BizTalk.  *SAPBindingSchema* est le schéma généré pour *RFC_CUSTOMER_GET*.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *InvokeRFC.SAPBindingSchema.RFC_CUSTOMER_GETResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler les RFC dans le système SAP. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consomme le message et le transmet au système SAP. La réponse du système SAP est enregistrée dans un autre emplacement. Contiendrait une orchestration classique pour appeler les RFC dans un système SAP :  
  
-   Envoyer et recevoir des formes pour envoyer des messages au système SAP et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer au système SAP de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande au système SAP et de recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir du système SAP dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration avec ports connectés](../../adapters-and-accelerators/adapter-sap/media/c228e79f-02e8-4de3-b447-8703caa28d3b.gif "c228e79f-02e8-4de3-b447-8703caa28d3b")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|Receive_Request|Recevoir|-Définissez **nom** à *Receive_Request*<br />-Définissez **activer** à *True*|  
|Send_LOB|Send|-Définissez **nom** à *Send_LOB*|  
|Receive_LOB|Recevoir|-Définissez **nom** à *Receive_LOB*<br />-Définissez **activer** à *False*|  
|Send_Response|Send|-Définissez **nom** à *Send_Response*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Spécifier les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|ReceiveMsgPort|-Définissez **identificateur** à *ReceiveMsgPort*<br />-Définissez **Type** à *ReceiveMsgPortType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|SendToLOBPort|-Définissez **identificateur** à *SendToLOBPort*<br />-Définissez **Type** à *SendToLOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SendMsgPort|-Définissez **identificateur** à *SendMsgPort*<br />-Définissez **Type** à *SendMsgPortType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|Receive_Request|-Définissez **Message** à *demande*<br />-Définissez **opération** à *ReceiveMsgPort.Operation_1.Request*|  
|Send_LOB|-Définissez **Message** à *demande*<br />-Définissez **opération** à *SendToLOBPort.Operation_1.Request*|  
|Receive_LOB|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SendToLOBPort.Operation_1.Response*|  
|Send_Response|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SendMsgPort.Operation_1.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système SAP.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SAP physique pour envoyer des messages au système SAP. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour l’appel d’une demande de changement dans le système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md) ou [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SAP pour envoyer des messages au système SAP est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour l’orchestration à un emplacement prédéfini. Consultez [des schémas de Message pour des opérations RFC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-rfc-operations.md) savoir sur le schéma du message de demande pour l’appel d’une commande RFC dans un système SAP. Par exemple, le message de demande pour appeler RFC_CUSTOMER_GET est la suivante :  
  
```  
<RFC_CUSTOMER_GET xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <KUNNR>0000001390</KUNNR>  
  <NAME1>*</NAME1>  
  <CUSTOMER_T/>  
</RFC_CUSTOMER_GET>  
```  
  
 L’orchestration consomme le message et l’envoie au système SAP. La réponse du système SAP est enregistrée à un autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir du système SAP pour le message de demande ci-dessus est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<RFC_CUSTOMER_GETResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <CUSTOMER_T>  
    <RFCCUST xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <KUNNR>0000001390</KUNNR>   
      <ANRED>Firma</ANRED>   
      <NAME1>Contoso, Ltd.</NAME1>   
      <PFACH />   
      <STRAS>4567 Main Street</STRAS>   
      <PSTLZ>98052</PSTLZ>   
      <ORT01>USA</ORT01>   
      <TELF1>555-0101</TELF1>   
      <TELFX>555-0102</TELFX>   
    </RFCCUST>  
  </CUSTOMER_T>  
</RFC_CUSTOMER_GETResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de l’appel d’une commande RFC dans un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)