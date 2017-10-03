---
title: "Exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples à l’aide de BizTalk Server et de l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c5db211-76a2-4c27-97f4-382302c722da
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4f2e1f867ba4f7759afa67a271bc6523b93e9a67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-business-components-with-mvg-fields-using-biztalk-server-and-the-siebel-adapter"></a>Exécuter des opérations sur les composants d’entreprise avec des champs de groupe à valeurs multiples à l’aide de BizTalk Server et de l’adaptateur Siebel
Cette section fournit des instructions sur l’exécution d’opération sur un composant d’entreprise contenant des champs à valeurs multiples. Pour illustrer une opération de bout en bout sur ces composants d’entreprise, vous devez effectuer :  
  
-   Une opération d’insertion sur un composant d’entreprise parent  
  
-   Une opération d’insertion sur un composant d’entreprise enfant  
  
-   Une opération d’association sur les liens à valeurs multiples entre le composant de gestion parents et enfants  
  
-   Une opération de Query_ [MVG_Child_Business_Comp] sur un enregistrement de composant d’entreprise parent  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] prend en charge les opérations sur les composants d’entreprise, consultez [opérations sur les composants d’entreprise](../../adapters-and-accelerators/adapter-siebel/operations-on-business-components-in-siebel.md). Pour plus d’informations sur la structure de SOAP des messages pour effectuer ces opérations, consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md).  
  
## <a name="how-to-perform-operations-on-a-business-component-with-multi-value-fields"></a>Comment effectuer des opérations sur un composant d’entreprise avec des champs de valeurs multiples ?  
 Une opération sur un système Siebel à l’aide du [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications Siebel](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md). Pour effectuer une opération sur un composant d’entreprise, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour toutes les opérations que vous souhaitez appeler sur le composant de gestion. Comme décrit précédemment, pour effectuer des opérations sur un composant d’entreprise avec des champs de valeurs multiples, vous devez générer le schéma d’opération Insert sur les composants d’entreprise parent et enfant, associer l’opération sur les liens de valeurs multiples entre parent et enfant composants d’entreprise et une opération de requête sur le composant de gestion parent.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système Siebel.  
  
3.  Créer l’orchestration pour appeler les différentes opérations dans le système Siebel.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, MVLDemo, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/samples-for-the-siebel-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment associer le composant parent de l’entreprise, **compte** à un composant métier enfant, **Contact**, nous allons générer le schéma pour les éléments suivants :  
  
-   L’opération d’insertion sur la **compte** composant d’entreprise. Consultez [exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md).  
  
-   L’opération d’insertion sur la **Contact** composant d’entreprise.  
  
-   Opération d’ASSOCIATE sur le **compte** composant d’entreprise.  
  
-   Opération QUERY_CONTACT sur la **compte** composant d’entreprise.  
  
 Consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer les quatre jeux de messages de demande et de réponse, une pour chaque opération que vous appellerez sur le système Siebel. Chaque jeu doit avoir un message de demande et un message de réponse. Par exemple, la procédure suivante fournit des instructions pour créer un message de demande et de réponse pour l’opération d’association. Vous devez effectuer des étapes similaires pour créer des messages pour d’autres opérations.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
### <a name="create-messages-and-link-to-schema"></a>Créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si ce n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créer le message et sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **AccountAssociate_Request**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *MVLDemo.SiebelBindingSchema.Associate*, où *MVLDemo* est le nom de votre projet BizTalk. *SiebelBindingSchema* est le schéma généré pour l’appel de la *associer* opération sur *compte* composant d’entreprise.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **AccountAssociate_Response**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *MVLDemo.SiebelBindingSchema.AssociateResponse*.|  
  
## <a name="set-up-the-orchestrations"></a>Configurer les orchestrations  
 Vous devez maintenant configurer les orchestrations à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer des opérations sur les composants de gestion de compte et de Contact.  
  
-   Configurer une orchestration pour effectuer une opération d’insertion sur la **compte** composant d’entreprise. Consultez [exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md).  
  
-   Configurer une orchestration pour effectuer une opération d’insertion sur la **Contact** composant d’entreprise. Ceci est similaire à l’opération d’insertion sur la **compte** composant d’entreprise.  
  
-   Configurer une orchestration pour effectuer une opération d’association sur le **compte** composant d’entreprise.  
  
-   Configurer une orchestration pour effectuer une opération QUERY_CONTACT sur la **compte** composant d’entreprise.  
  
 Cette rubrique va vous montrer comment configurer une orchestration pour l’opération d’association sur le **compte** composant d’entreprise. Vous devez effectuer des tâches similaires pour configurer les orchestrations restantes également.  
  
 L’orchestration pour l’opération d’association sur le composant de gestion de compte l’aspect suivant :  
  
 ![Orchestration permettant de travailler avec MVL dans Siebel](../../adapters-and-accelerators/adapter-siebel/media/6c7d548d-dc80-490f-89fe-12aff10fa3cf.gif "6c7d548d-dc80-490f-89fe-12aff10fa3cf")  
  
 La section suivante fournit des informations sur la façon de configurer cette orchestration en déposant les formes de message, ports, messages de liaison à des schémas, etc.. Vous devez effectuer des tâches similaires pour configurer les autres orchestrations.  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|AccountAssociateXML|Recevoir|-Définissez **nom** à *AccountAssociateXML*<br />-Définissez **activer** à *True*|  
|SendToLOB|Send|-Définissez **nom** à *SendToLOB*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|FileIn_AccountAssociate|-Définissez **identificateur** à *FileIn_AccountAssociate*<br />-Définissez **Type** à *FileInAccountAssociateType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort_AccountAssociate|-Définissez **identificateur** à *LOBPort_AccountAssociate*<br />-Définissez **Type** à *LOBPortAccountAssociateType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse_AccountAssociate|-Définissez **identificateur** à *SaveResponse_AccountAssociate*<br />-Définissez **Type** à *SaveResponseAccountAssociateType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration ci-dessus.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|AccountAssociateXML|-Définissez **Message** à *AccountAssociate_Request*<br />-Définissez **opération** à *FileIn_AccountAssociate.Associate.Request*|  
|SendToLOB|-Définissez **Message** à *AccountAssociate_Request*<br />-Définissez **opération** à *LOBPort_AccountAssociate.Associate.Request*|  
|Réception réponse|-Définissez **Message** à *AccountAssociate_Response*<br />-Définissez **opération** à *LOBPort_AccountAssociate.Associate.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse_AccountAssociate.Associate.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [comment générer des Orchestrations](../../core/how-to-build-orchestrations.md) et [déploiement des assemblys BizTalk à partir de Visual Studio dans une Application BizTalk](../../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [la création d’une Application](../../core/how-to-create-an-application.md).  
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système Siebel. Vous pouvez avoir le même port pour toutes les quatre orchestrations.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir du système Siebel. Vous pouvez avoir le même port pour toutes les quatre orchestrations.  
  
    -   Définissez physiques ports d’envoi WCF-Custom ou WCF-Siebel pour envoyer des messages au système Siebel. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/manually-configure-a-physical-port-binding-to-the-siebel-adapter.md). Vous devez disposer des ports différents pour toutes les quatre orchestrations.  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la Console Administration de BizTalk pour créer des ports d’envoi (pour les appels sortants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour associer un composant d’entreprise parent pour le composant d’activité enfant. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [démarrer une Application BizTalk](../../core/how-to-start-and-stop-a-biztalk-application.md) ou [démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Les quatre WCF-Custom ou WCF-Siebel ports d’envoi, un pour envoyer des messages au système Siebel, sont en cours d’exécution.  
  
-   Les orchestrations BizTalk quatre pour différentes opérations sont en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Vous devez supprimer la demande de port de réception de messages dans le fichier. Le schéma pour les messages de demande doit être conforme au schéma que vous avez généré précédemment dans la rubrique. Consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md) pour plus d’informations sur le schéma du message de demande pour différentes opérations. Vous devez supprimer les messages de demande dans l’ordre suivant :  
  
-   Supprimer un message de demande d’insérer un enregistrement dans le **compte** composant d’entreprise. Le message de demande doit être similaire à celle supprimée pour l’insertion d’un enregistrement dans le composant de gestion de compte dans la rubrique [exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md). L’orchestration consomme le message et l’envoie au système Siebel. La réponse à partir du système Siebel est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
-   Supprimer un message de demande d’insérer un enregistrement dans le **Contact** composant d’entreprise. Le message de demande doit être similaire à celle supprimée pour l’insertion d’un enregistrement dans le composant de gestion de compte dans la rubrique [exécuter des opérations sur les composants de métier à l’aide de BizTalk Server et de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-using-the-siebel-adapter-in-biztalk.md). L’orchestration consomme le message et l’envoie au système Siebel. La réponse à partir du système Siebel est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
-   Supprimer un message de demande pour effectuer une opération d’association sur le **compte** composant d’entreprise. Cela permettra d’associer les composants d’entreprise parents et enfants en fonction de l’expression de recherche et le nom du champ à valeurs multiples, que vous spécifiez dans le code XML d’entrée. Sachez que :  
  
    -   L’expression de recherche dans l’opération d’association parent doit correspondre à un enregistrement unique dans la table parente.  
  
    -   L’expression de recherche enfant dans l’opération d’association doit correspondre à un enregistrement unique dans la table enfant.  
  
     Par exemple, le message de demande d’effectuer une opération d’association sur le composant de gestion de compte est :  
  
    ```  
    <Associate xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <ViewMode>3</ViewMode>  
      <ParentSearchExpr>[Name] LIKE "SampleName1"</ns0:ParentSearchExpr>   
      <ParentMVGField>Bill To First Name</ns0:ParentMVGField>   
      <ChildSearchExpr>[First Name] LIKE "SampleName2"</ns0:ChildSearchExpr>   
    </Associate>  
    ```  
  
     L’orchestration consomme le message et l’envoie au système Siebel. La réponse à partir du système Siebel est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse pour le message de demande ci-dessus est la suivante :  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <AssociateResponse xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <AssociateResult>  
        <ChildID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8AO09</ChildID>  
        <ParentID xmlns="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">1-8ANZ5</ParentID>  
      </AssociateResult>  
    </AssociateResponse>  
    ```  
  
-   Supprimer un message de demande pour effectuer une opération QUERY_CONTACT sur la **compte** composant d’entreprise. Par exemple, le message de demande pour une opération QUERY_CONTACT est la suivante :  
  
    ```  
    <Query_Contact xmlns ="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects/Account/Account/Operation">  
      <ViewMode>3</ViewMode>   
      <ParentSearchExpr>[Name] LIKE "SampleName1"</ParentSearchExpr>   
      <ParentMVGField>Bill To First Name</ParentMVGField>   
      <ContactQueryInputRecord>  
        <SearchExpr xmlns:ns1="http://Microsoft.LobServices.Siebel/2007/03/BusinessObjects">[Id] LIKE '*'</SearchExpr>   
      </ContactQueryInputRecord>  
    </Query_Contact>  
    ```  
  
     L’orchestration consomme le message et l’envoie au système Siebel. La réponse à partir du système Siebel est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
 Consultez [des schémas de Message pour des opérations de composant Business](../../adapters-and-accelerators/adapter-siebel/message-schemas-for-business-component-operations.md) pour plus d’informations sur le schéma du message de demande.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’exécution d’une opération sur le composant d’entreprise avec des champs à plusieurs valeurs à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-siebel/exceptions-and-error-handling-with-the-siebel-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-siebel/reuse-adapter-bindings-in-the-siebel-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md)