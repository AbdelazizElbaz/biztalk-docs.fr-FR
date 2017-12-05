---
title: "Procédure pas à pas : Utilisation d’enveloppes XML (Basic) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content-based routing, promoting properties
- promoting properties, routing messages
- promoting properties, content-based routing
- routing, messages
- routing, promoting properties
ms.assetid: 02d0c596-0cfe-4bae-9f1b-d7dbc17e18a9
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9090c4ee7d576bb7ab610cd81637680d837b2cae
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="walkthrough-using-xml-envelopes-basic"></a>Procédure pas à pas : Utilisation d’enveloppes XML (Basic)
Cet exemple illustre le désassemblage de base d'enveloppes XML par l'implémentation en partie d'un système de suivi des erreurs fictif. Cet exemple remplit les conditions suivantes :  
  
1.  les messages d'erreur sont consignés dans divers sites physiques de l'entreprise, puis envoyés vers un emplacement central pour être traités par différents systèmes principaux ;  
  
2.  Les messages d'erreur sont écrits au format XML.  
  
3.  Un message d'erreur peut être envoyé seul sans enveloppe ou en tant que lot contenu dans une enveloppe.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour cet exemple, que vous devez être familiarisé avec la création de projets BizTalk, signature d’un assembly et pour afficher les applications et les ports à l’aide de la console Administration de BizTalk Server. Vous devez également être familiarisé avec les concepts présentés dans [procédure pas à pas : déploiement d’une Application BizTalk base](../core/walkthrough-deploying-a-basic-biztalk-application.md).  
  
## <a name="what-this-example-does"></a>Ce que fait cet exemple  
 Cet exemple traite les messages entrants contenant soit un seul message d'erreur, soit un lot de messages d'erreur par la définition d'un schéma d'enveloppe et l'utilisation du pipeline XmlDisassembler.  
  
## <a name="example"></a>Exemple  
 Pour créer l'exemple, suivez les étapes présentées dans les sections ci-après.  
  
### <a name="create-a-new-biztalk-project"></a>Créez un projet BizTalk  
 Avant de concevoir une solution, vous devez créer un projet BizTalk, vous assurer qu'il porte un nom fort, puis lui attribuer un nom d'application. Attribuer un nom d'application empêche BizTalk Server de déployer la solution dans l'application BizTalk par défaut.  
  
##### <a name="to-create-and-configure-a-new-biztalk-project"></a>Pour créer et configurer un projet BizTalk  
  
1.  Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Appelez le projet **BasicXMLEnvelope**.  
  
2.  Générez un fichier de clé et attribuez-le au projet. Pour plus d’informations, consultez [comment configurer un fichier de clé de Assembly de nom fort](../core/how-to-configure-a-strong-name-assembly-key-file.md).  
  
3.  Dans les propriétés de configuration de déploiement pour le projet, vous devez affecter un **nom de l’Application** et **redémarrer les Instances d’hôte** à `True`. La définition de cet indicateur indique à l'hôte d'effacer toutes les instances mises en cache de l'assembly.  
  
### <a name="create-the-error-schema"></a>Créer le schéma d’erreur  
 Cette étape permet de créer le schéma d'erreur. Il définit le message clé du système.  
  
##### <a name="to-create-the-error-schema"></a>Pour créer le schéma d'erreur  
  
1.  Ajoutez un nouveau schéma intitulé « Error » au projet.  
  
2.  Modifier l’espace de noms cible du schéma à **http://BasicXMLEnvelope**.  
  
3.  Modifier la propriété de schéma **Element FormDefault** sous le **avancé** catégorie **Qualified**. Vous indiquez ainsi que les éléments déclarés localement doivent être qualifiés par l'espace de noms cible dans un document d'instance.  
  
4.  Renommez le nœud racine « Error » et créez cinq éléments enfants avec les types indiqués :  
  
    -   ID, xs:int  
  
    -   Type, xs:int  
  
    -   Priority, xs:string  
  
    -   Description, xs:string  
  
    -   ErrorDateTime, xs:string  
  
     Votre schéma doit présenter l'aspect suivant :  
  
     ![Schéma d’erreur terminé](../core/media/error-schema.gif "error_schema")  
  
5.  Créez un exemple de message pour ce schéma. Vous pouvez ainsi vérifier que les messages seuls hors enveloppe sont correctement traités. Voici un exemple de message :  
  
    ```  
    <Error xmlns="http://BasicXMLEnvelope">  
      <ID>1</ID>  
      <Type>5</Type>  
      <Priority>Low</Priority>  
      <Description>Sprocket widget prints reports slowly.</Description>  
      <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
    </Error>  
    ```  
  
     Enregistrez ce message dans un fichier du répertoire du projet.  
  
### <a name="create-the-envelope-schema"></a>Création du schéma d'enveloppe  
 L'enveloppe contient un ou plusieurs messages d'erreur. Dans cet exemple simple, l'enveloppe ne dispose pas de ses propres propriétés et éléments.  
  
##### <a name="to-create-the-envelope-schema"></a>Pour créer le schéma d'enveloppe  
  
1.  Ajoutez un nouveau schéma intitulé « Envelope » au projet BasicXMLEnvelope.  
  
2.  Modifier l’espace de noms cible **http://BasicXMLEnvelope**.  
  
3.  Modifiez le nom du nœud racine de « Root » en « Envelope ».  
  
4.  Marquez le schéma en tant que schéma d'enveloppe. Cliquez sur le  **\<schéma\>**  nœud. Dans le volet Propriétés, définissez la propriété de référence du schéma **enveloppe** à `OK`.  
  
5.  Définir le **XPath de corps** propriété. Pour ce faire, cliquez sur le **enveloppe** nœud. Dans la fenêtre Propriétés, cliquez sur le bouton de sélection (**...** ) situé dans le **XPath de corps** propriété, sélectionnez **enveloppe**, puis cliquez sur **OK**.  
  
6.  Ajoutez tout élément enfant au nœud Envelope. Le message d'erreur sera contenu dans cet élément. Votre schéma doit présenter l'aspect suivant :  
  
     ![Schéma d’enveloppe terminé](../core/media/envelope-schema.gif "envelope_schema")  
  
7.  Créez un exemple de message contenant une enveloppe et un ou plusieurs exemples de message. Un exemple de message est :  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error>  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
     Enregistrez ce message dans un fichier du répertoire du projet.  
  
### <a name="deploy-and-configure-the-send-and-receive-ports"></a>Déploiement et configuration des ports de réception et d'envoi  
 Une fois les schémas créés, vous devez compiler et déployer le projet. Lorsque le projet est déployé, vous pouvez utiliser la console Administration de BizTalk Server pour configurer les ports d'envoi et de réception.  
  
##### <a name="to-deploy-basicxmlenvelope"></a>Pour déployer BasicXMLEnvelope  
  
1.  À partir de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], choisissez **déployer BasicXMLEnvelope** dans le menu Générer. Il sera généré et déployé sur BizTalk Server en tant qu'application « BasicXMLEnvelope ».  
  
2.  Dans la console Administration de BizTalk Server, développez le **Applications** groupe pour vérifier que **BasicXMLEnvelope** est présent sous la forme d’une application personnalisée.  
  
##### <a name="to-configure-the-receive-port"></a>Pour configurer le port de réception  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « Receive » sous le **BasicXMLEnvelope** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Unidirectionnel Port de réception**.  
  
3.  Dans le **propriétés du Port de réception** boîte de dialogue, définissez le nom du port sur « Réception ».  
  
4.  Cliquez sur les emplacements de réception, puis cliquez sur **nouveau** pour ajouter un port de réception. Nommez le nouveau port « ReceiveError ». Définir le **Pipeline de réception** à **XMLReceive**. Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**.  
  
5.  Sélectionnez le répertoire de réception créé précédemment et cliquez sur **OK**. Votre port de réception devrait à présent être configuré. Cliquez sur **OK** à fermer.  
  
##### <a name="to-configure-the-send-port"></a>Pour configurer le port d'envoi  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « Send » sous le **BasicXMLEnvelope** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « Send ».  
  
4.  Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**. Définissez le dossier de destination sur le répertoire d’envoi que vous avez créé précédemment et cliquez sur **OK**.  
  
5.  Cliquez sur **filtres** et ajouter un filtre :  
  
    -   BIZTALK SERVER. MessageType == **http://BasicXMLEnvelope#Error**  
  
6.  Cliquez sur **OK** pour terminer la configuration de port d’envoi. Votre port d'envoi devrait à présent être configuré.  
  
### <a name="run-the-example"></a>Exécution de l'exemple  
 Il est maintenant temps d'exécuter l'exemple. Après avoir utilisé la console Administration de BizTalk Server pour lancer l'application BasicXMLEnvelope, copiez les fichiers de test dans l'emplacement de réception et observez le résultat produit dans l'emplacement d'envoi.  
  
##### <a name="to-run-the-basicxmlenvelope-example"></a>Pour exécuter l'exemple BasicXMLEnvelope  
  
1.  Dans la console Administration de BizTalk Server, cliquez sur le **BasicXMLEnvelope** application, puis sur **Démarrer**. Ceci inscrit et démarre les ports d'envoi et de réception  
  
2.  Faites glisser le fichier exemple dans le répertoire de réception. Si vous utilisez les exemples fournis plus haut, vous devez trouver trois messages d'erreur distincts dans l'emplacement d'envoi lorsque le traitement est terminé.  
  
## <a name="extending-the-example"></a>Extension de l'exemple  
 Vous pouvez étendre l'exemple afin qu'il réponde à d'autres exigences. Cette section traite deux scénarios communs :  
  
-   Si un lot d'erreurs est envoyé dans une enveloppe, les échecs de messages individuels dans le désassemblage ne doivent pas empêcher le traitement des messages qui ne rencontrent pas d'échec.  
  
-   Les erreurs doivent être remises à différents emplacements en fonction de leur priorité. Les messages dont la priorité est élevée sont expédiés tandis que les autres priorités sont traités via les canaux normaux.  
  
 Les sections suivantes étendent l'exemple pour gérer ces cas.  
  
### <a name="recoverable-interchange-processing"></a>Traitement des échanges récupérables  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge le traitement des échanges récupérables. Grâce à cette fonction, vous pouvez vous assurer que les lots de messages échouent de manière individuelle dans le désassemblage, et non en tant que lot.  
  
##### <a name="to-configure-the-example-for-recoverable-interchange-processing"></a>Pour configurer l'exemple pour le traitement des échanges récupérables  
  
1.  Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, cliquez sur **Ports de réception**, puis double-cliquez sur le port de réception. Il s'agit du port que vous avez précédemment créé.  
  
2.  Dans le **propriétés du Port de réception** boîte de dialogue, cliquez sur **emplacements de réception**. Cliquez sur **propriétés** pour afficher les **propriétés d’emplacement de réception ReceiveError** boîte de dialogue. Cliquez sur le bouton de sélection (**...** ) bouton pour le **Pipeline de réception**.  
  
3.  Dans le **configurer le Pipeline - XMLReceive** boîte de dialogue, définissez la **traitement des échanges récupérables** propriété `True`, puis cliquez sur **OK**.  
  
4.  Cliquez sur **OK** pour fermer la **propriétés de l’emplacement de réception** boîte de dialogue, puis cliquez sur **OK** pour fermer la **propriétés du Port de réception** boîte de dialogue zone.  
  
##### <a name="to-create-a-sample-file-and-run-the-example"></a>Pour créer un fichier exemple et exécuter l'exemple  
  
1.  Pour créer un fichier exemple, faites une copie du fichier d'enveloppe créé dans l'exemple, ajoutez un espace de noms inexistant à l'une des instances Error, puis enregistrez le fichier :  
  
    ```  
    <Envelope xmlns="http://BasicXMLEnvelope">  
      <Error>  
        <ID>102</ID>  
        <Type>0</Type>  
        <Priority>High</Priority>  
        <Description>Sprocket query fails to return any sprockets even though some exist</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
      <Error xmlns="http://ThisIsAnError">  
        <ID>16502</ID>  
        <Type>2</Type>  
        <Priority>Low</Priority>  
        <Description>Time threshold exceeded.</Description>  
        <ErrorDateTime>1999-05-31T13:20:00.000-05:00</ErrorDateTime>  
      </Error>  
    </Envelope>  
    ```  
  
2.  Dans la console Administration de BizTalk Server, cliquez sur **Applications** et vérifiez que le **BasicXMLEnvelope** application est en cours d’exécution.  
  
3.  Déposez le message dans l'emplacement de réception. Après traitement, vous devez trouver le premier message dans l'emplacement d'envoi et le second, avec une priorité basse, dans la file d'attente des messages interrompus.  
  
### <a name="content-based-routing-cbr"></a>Routage basé sur le contenu  
 Vous avez la possibilité d'utiliser le routage basé sur le contenu pour acheminer les messages en fonction de leur contenu. Dans ce scénario, l'acheminement est basé sur la priorité : les messages dont la priorité est élevée sont dirigés vers un emplacement d'envoi, et ceux dont la priorité est moyenne ou basse le sont vers un emplacement d'envoi différent.  
  
 Pour étendre l'exemple, vous devez effectuer les tâches suivantes :  
  
1.  Promouvoir le **priorité** champ du schéma Error dans le projet BasicXMLEnvelope. Le routage basé sur le contenu s'appuie sur les propriétés promues pour acheminer les messages. Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).  
  
2.  Créer et configurer deux ports d'envoi supplémentaires. Les ports utilisent un filtre pour s'assurer qu'ils reçoivent les messages appropriés.  
  
##### <a name="to-promote-the-priority-field-in-the-error-schema"></a>Pour promouvoir le champ Priorité du schéma Error  
  
1.  Avec la **BasicXMLEnvelope** ouvert dans le projet [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ouvrez le **erreur** schéma et développez le **erreur** nœud.  
  
2.  Cliquez sur le **priorité** élément, pointez sur **promouvoir**, puis cliquez sur **promotion rapide**.  
  
3.  Cliquez sur **OK** pour confirmer l’ajout d’un nouveau schéma de propriété pour les propriétés promues.  
  
4.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, ouvrez le schéma de propriété PropertySchema.xsd. Supprimez « Field1 » à partir du schéma.  
  
5.  Recompilez et redéployez la solution. Dans le menu Générer, sélectionnez Déployer BasicXMLEnvelope.  
  
6.  Le projet était configuré pour réinitialiser l'instance hôte une fois la solution redéployée. Si vous avez modifié cet élément, vous devez arrêter et démarrer l'hôte.  
  
##### <a name="to-configure-the-low-and-medium-priority-send-port"></a>Pour configurer le port d'envoi de priorité basse et moyenne  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « SendLowMediumPriority » sous le **BasicXMLEnvelope** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « SendLowMediumPriority ».  
  
4.  Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**. Définissez le dossier de destination sur le répertoire que vous avez créé auparavant. Cliquez sur **OK** à fermer.  
  
5.  Cliquez sur **filtres** et ajouter trois expressions de filtre :  
  
    -   BTS.MessageType == http://BasicXMLEnvelope#Error And  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == Low Or  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == Medium  
  
6.  Cliquez sur **OK** pour terminer la configuration de port d’envoi de faible priorité et moyenne.  
  
##### <a name="to-configure-the-high-priority-send-port"></a>Pour configurer le port d'envoi de priorité élevée  
  
1.  Utilisez l’Explorateur Windows pour créer un répertoire nommé « SendHighPriority » sous le **BasicXMLEnvelope** répertoire du projet.  
  
2.  Dans la console Administration de BizTalk Server, développez le **BasicXMLEnvelope** application, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur  **Unidirectionnel statique**.  
  
3.  Dans le **propriétés de Port d’envoi** boîte de dialogue, définissez le nom du port sur « SendHighPriority ».  
  
4.  Pour **Type de Transport**, sélectionnez **fichier**, puis cliquez sur **configurer**. Définissez le dossier de destination sur le répertoire que vous avez créé auparavant. Cliquez sur **OK** à fermer.  
  
5.  Cliquez sur **filtres** et ajouter deux expressions de filtre :  
  
    -   BTS.MessageType == http://BasicXMLEnvelope#Error And  
  
    -   BasicXMLEnvelope.PropertySchema.Priority == High  
  
6.  Cliquez sur **OK** pour terminer la configuration de port d’envoi de priorité élevée.  
  
##### <a name="to-test-the-routing-solution"></a>Pour tester la solution de routage  
  
1.  Dans la console Administration de BizTalk Server, développez le **Applications** de groupe, cliquez sur le **BasicXMLEnvelope** application, puis sur **Démarrer**. Lorsque vous êtes invité à confirmer, cliquez sur **Démarrer**. Les nouveaux ports d'envoi sont ainsi inscrits.  
  
2.  Déposez le message test dans l'emplacement de réception. Notez la façon dont les messages d'erreur sont acheminés vers les différents emplacements :  
  
    -   Les messages dont la priorité est basse, moyenne ou élevée et dont le traitement n'échoue pas sont acheminés vers l'emplacement d'envoi d'origine (configuré au cœur de l'exemple) et l'emplacement d'envoi par priorité. Pour les messages dont la priorité est basse ou moyenne, une copie s'affiche à la fois dans l'emplacement d'envoi d'origine et dans l'emplacement d'envoi de priorité basse ou moyenne.  
  
    -   Si le traitement des échanges récupérables est activé, le message d'erreur ayant échoué n'est pas acheminé et le message n'ayant pas échoué est acheminé comme prévu. Le message ayant échoué n'est pas acheminé car son type ne correspond pas au type utilisé dans les filtres configurés.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des échanges récupérables](../core/recoverable-interchange-processing.md)   
 [Promotion des propriétés](../core/promoting-properties.md)   
 [CBRSample (exemple BizTalk Server)](../core/cbrsample-biztalk-server-sample.md)