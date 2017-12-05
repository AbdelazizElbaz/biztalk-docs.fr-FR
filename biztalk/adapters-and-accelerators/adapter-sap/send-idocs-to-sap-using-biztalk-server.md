---
title: "Envoyer des IDOC à SAP à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDOCs, sample for sending
- IDOCs, sending to SAP using BizTalk Server
- IDOCs, business scenarios for sending
ms.assetid: 92042623-ffbf-472f-9515-e9a77eb320fb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b2e493f5b99c9b100a9683ffb90584a9cfd92b3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="send-idocs-to-sap-using-biztalk-server"></a>Envoyer des IDOC à SAP à l’aide de BizTalk Server
Tous les appels IDOC à SAP sont traitées en interne comme des appels tRFC où l’adaptateur agit comme un client tRFC et appelle une commande RFC dans pour envoyer un IDOC SAP. Cette section fournit des informations sur l’envoi des IDOC à SAP à l’aide de la [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] met en évidence des deux opérations distinctes pour envoyer des IDOC :  
  
-   **Envoyer** opération permet aux clients de l’adaptateur envoyer des IDOC ayant un schéma fortement typé.  
  
-   **SendIdoc** opération permet aux clients de l’adaptateur envoyer des IDOC ayant un schéma faiblement typée. Vous utilisez ce paramètre, les clients de l’adaptateur peuvent envoyer des IDOC de fichier plat au système SAP. Le fichier plat IDOC entière serait une valeur de nœud dans un message SendIdoc XML.  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] prend en charge de l’envoi des IDOC à un système SAP, consultez [opérations sur IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-idocs-in-sap.md). Pour plus d’informations sur la structure de SOAP des messages pour envoyer un IDOC, consultez [des schémas de Message pour des opérations IDOC](../../adapters-and-accelerators/adapter-sap/message-schemas-for-idoc-operations.md).  
  
## <a name="biztalk-scenarios-for-sending-idocs-with-the-sap-adapter"></a>Scénarios de BizTalk pour envoyer des IDOC avec l’adaptateur SAP  
 Le tableau suivant fournit des scénarios clés de BizTalk pour envoyer des IDOC à un système SAP :  
  
|Entrée de BizTalk|Traitement BizTalk|Sortie vers l’adaptateur|  
|----------------------|------------------------|-----------------------|  
|Format de fichier plat IDOC|**Heure de création de métadonnées**<br /><br /> 1.  Définissez la propriété binding GenerateFlatFileCompatibleIdocSchema à **True**.<br />2.  Générer le schéma pour le **envoyer** opération un IDOC spécifique à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Réception de fichier plat IDOC<br />2.  Utilisez le désassembleur de fichier plat pour convertir des IDOC de fichier plat IDOC XML en utilisant le schéma qui vient d’être généré.<br />3.  Action de **envoyer** opération.|Envoyer le message|  
|Format de fichier plat IDOC|**Heure de création de métadonnées**<br /><br /> 1.  Définissez la propriété binding GenerateFlatFileCompatibleIdocSchema à **True**.<br />2.  Générer le schéma pour le **SendIdoc** opération à partir du nœud IDOC avec [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Réception de fichier plat IDOC<br />2.  Utiliser le désassembleur de fichier plat pour convertir le format de fichier plat IDOC en XML (dans ce cas, le message XML contient un \<idocData\> nœud qui contient l’intégralité du message Idoc de fichier plat) en utilisant le schéma qui vient d’être généré.<br />3.  Action de **SendIdoc** opération.|Message de SendIdoc|  
|XML IDOC|**Heure de création de métadonnées**<br /><br /> -Générer le schéma pour le **envoyer** opération un IDOC spécifique à l’aide [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Recevoir des IDOC de XML.<br />2.  Action de **envoyer** opération.|Envoyer le message|  
|IDOC de fichier plat dans le message XML|**Heure de création de métadonnées**<br /><br /> -Générer le schéma pour le **SendIdoc** opération à partir du nœud IDOC avec [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].<br /><br /> **Moment de la conception d’orchestration**<br /><br /> 1.  Recevoir un message XML.<br />2.  Action de **SendIdoc** opération.|Message de SendIdoc|  
  
## <a name="how-to-send-an-idoc-to-an-sap-system"></a>Comment envoyer un IDOC à un système SAP  
 Une opération sur un système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour envoyer un IDOC à un système SAP, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer un schéma pour l’IDOC que vous souhaitez appeler dans le système SAP. Lors de la génération du schéma Assurez-vous que vous définissez les propriétés de liaison requis, comme indiqué dans le tableau précédent. Pour obtenir des instructions sur la façon de définir les propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md).  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système SAP.  
  
3.  Créez une orchestration pour envoyer un IDOC à un système SAP.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, IDOCSend, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur SAP ](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment envoyer un IDOC à un système SAP en générant le schéma pour le *envoyer* opération sous \IDOC\ORDERS\ORDERS05\ORDERS05. V3(620) IDOC. Consultez [Parcourir, rechercher et obtenir des métadonnées pour des opérations IDOC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-idoc-operations-in-sap.md) pour plus d’informations sur la génération de schéma pour un IDOC particulier.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour envoyer un IDOC au système SAP et l’autre pour recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **IDOCSend**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *IDOCSend.SAPBindingSchema3*, où *IDOCSend* est le nom de votre projet BizTalk. *SAPBindingSchema3* est le schéma généré pour l’opération d’envoi.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **IDOCResponse**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *IDOCSend.SAPBindingSchema4*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour envoyer des IDOC à un système SAP. Dans cette orchestration, vous supprimez un fichier plat IDOC à une emplacement de réception. Ce fichier est converti en un message de demande XML à l’aide d’un désassembleur de fichier plat. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consomme ce message et le transmet au système SAP. La réponse avec un GUID est reçue à partir de SAP et est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des IDOC au système SAP et de recevoir des réponses. Vous devez également inclure un désassembleur de fichier plat pour convertir un fichier plat dans un fichier XML. Contient une orchestration classique pour envoyer et IDOC à un système SAP :  
  
-   Envoyer et recevoir des formes pour envoyer des messages au système SAP et de recevoir des réponses.  
  
-   Unidirectionnel port de réception pour recevoir des IDOC de fichier plat à envoyer au système SAP.  
  
-   Un désassembleur de fichier plat pour convertir le format de fichier plat IDOC dans un fichier XML.  
  
-   Un double port d’envoi pour envoyer l’IDOC au système SAP et de recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir du système SAP dans un dossier.  
  
 Un exemple d’orchestration se présente comme suit :  
  
 ![Orchestration permettant d’envoyer des IDOC à SAP](../../adapters-and-accelerators/adapter-sap/media/db1490c8-da52-4af3-8a4f-d93bd815025d.gif "db1490c8-da52-4af3-8a4f-d93bd815025d")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveFile|Recevoir|-Définissez **nom** à *ReceiveFile*<br />-Définissez **activer** à *True*|  
|SendToLOB|Send|-Définissez **nom** à *SendToLOB*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="adding-a-flat-file-disassembler"></a>Ajout d’un désassembleur de fichier plat  
 Vous devez ajouter un désassembleur de fichier plat à votre orchestration pour convertir le format de fichier plat IDOC dans un format XML.  
  
##### <a name="to-add-a-flat-file-disassembler"></a>Pour ajouter un désassembleur de fichier plat  
  
1.  Cliquez sur le projet BizTalk, pointez sur **ajouter**, puis sélectionnez **un nouvel élément**.  
  
2.  À partir de la boîte de dialogue, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Catégories|Fichiers de pipeline|  
    |Modèles Visual Studio installés|Pipeline de réception|  
    |Nom|IDOCReceive|  
  
3.  Le Concepteur de Pipeline s’ouvre. À partir de la **composants de Pipeline BizTalk** boîte à outils, faites glisser le **désassembleur de fichier plat** composant de pipeline dans le **désassembler** étape du pipeline de réception.  
  
4.  À partir de la **propriétés du composant de Pipeline** afficher, spécifiez une valeur pour le **schéma de Document** propriété. Dans la liste déroulante. Veillez à que sélectionner le schéma correspondant à l’opération d’envoi IDOC.  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveFile|-Définissez **Message** à *IDOCSend*<br />-Définissez **opération** à *FileIn.SendIDOC.Request*|  
|SendToLob|-Définissez **Message** à *IDOCSend*<br />-Définissez **opération** à *LOBPort.SendIDOC.Request*|  
|Réception réponse|-Définissez **Message** à *IDOCResponse*<br />-Définissez **opération** à *LOBPort.SendIDOC.Response*|  
|SendResponse|-Définissez **Message** à *IDOCResponse*<br />-Définissez **opération** à *SaveResponse.SendIDOC.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système SAP.  
  
        > [!IMPORTANT]
        >  Pour le pipeline XMLReceive pour ce port, veillez à sélectionner ***IDOCReceive***. Vous avez créé ce pipeline dans le cadre du projet BizTalk.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SAP physique pour envoyer des messages au système SAP. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md).
  
        > [!NOTE]
        >  Vous pouvez également définir le *AutoConfirmSentIdocs* liaison de la propriété à valider automatiquement IDOC dans le système SAP. Si vous procédez ainsi, vous n’avez pas besoin d’appeler explicitement l’opération RfcConfirmTransID pour valider l’IDOC. Pour plus d’informations sur la propriété de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour mySAP Business Suite liaison propriétés](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md). Pour plus d’informations sur l’opération RfcConfirmTransID, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour envoyer un IDOC au système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md), ou [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SAP pour envoyer des messages au système SAP est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour l’orchestration. Pour cet exemple, nous supprimera un fichier plat IDOC à la période définie par emplacement de réception FILE. Les actions suivantes sont exécutées après avoir supprimé le message de demande :  
  
-   L’orchestration récupère cet IDOC de fichier plat et le convertit en message de requête XML, le schéma pour lequel est conforme au schéma que vous avez généré précédemment.  
  
-   Si le message de demande que vous avez fourni contient un GUID, l’adaptateur génère une ID (TID) de la transaction et l’envoie au système SAP.  
  
-   Si le message de demande que vous avez fourni ne contient pas un GUID, l’adaptateur génère un GUID et utilise ce GUID pour générer un TID. Le TID est ensuite envoyé au système SAP.  
  
 Dans les deux cas, le message de réponse du système SAP contient un GUID. Par exemple, un message de réponse pour l’opération d’envoi sur l’IDOC ORDERS05 est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<SendResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Idoc/3/ORDERS05//620/Send">  
  <guid>a5afe162-d5cc-47b0-bf6f-3b0bfe06a97e</guid>  
</SendResponse>  
```  
  
 Après avoir reçu le GUID, vous devez appeler la **RfConfirmTransID** opération pour valider le TID. Pour plus d’informations sur la **RfcConfirmTransID** opération, consultez [opérations sur tRFCs dans SAP](../../adapters-and-accelerators/adapter-sap/operations-on-trfcs-in-sap.md). Vous pouvez créer une nouvelle orchestration pour appeler cette opération ou modifiez l’orchestration existante. Si vous souhaitez créer une nouvelle orchestration, il sera similaire à n’importe quel autre orchestration sur un système SAP. Si vous souhaitez mettre à jour l’orchestration existante, consultez [appeler tRFCs dans SAP à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sap/invoke-trfcs-in-sap-using-biztalk-server.md). L’orchestration permettant d’appeler un tRFC, comme décrit dans la rubrique montre comment appeler un **RfcConfirmTransID** opération à partir de l’orchestration même.  
  
> [!NOTE]
>  Vous ne devez pas appeler l’opération de RfcConfirmTransID si vous définissez la *AutoConfirmSentIdocs* liaison de propriété **True**.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de l’envoi d’un IDOC à un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)