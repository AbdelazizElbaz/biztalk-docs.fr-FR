---
title: "Étape 4 : Configurer l’environnement BizTalk Server pour le test de charge | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f336c5f-5a18-493d-8fc0-a8a475ab47b3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5520062cb6c9bbd937d5c131c41992a7013a9711
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-configure-biztalk-server-environment-for-load-testing"></a>Étape 4 : Configurer l’environnement BizTalk Server pour le test de charge
Cette rubrique fournit des informations pour créer les emplacements de réception d’un serveur BizTalk, Ports de réception, et les Ports d’envoi requis pour exécuter l’exemple de code décrit dans les rubriques [étape 1 : créer un Test unitaire pour envoyer des Documents à BizTalk Server](~/technical-guides/step-1-create-a-unit-test-to-submit-documents-to-biztalk-server.md) et [étape 3 : créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md).  
  
## <a name="configure-biztalk-server-environment-for-load-tests"></a>Configurer l’environnement BizTalk Server pour les Tests de charge  
 Comme décrit dans la rubrique [étape 3 : créer un Test de charge pour exécuter plusieurs Tests unitaires simultanément](~/technical-guides/step-3-create-a-load-test-to-perform-multiple-unit-tests-simultaneously.md), le test de charge **BTS_Messaging_Step** est configuré pour exécuter les tests unitaires  **BTSMessaging** et **BTSMessaging2**. À son tour, ces tests unitaires charger une copie du message C:\Projects\LoadTest\BTSLoad\TestMessages\TestXmlDocument.xml et l’envoyer aux points de terminaison **BTSMessagingEP** et **BTSMessagingEP2** tel que défini dans la section suivante du fichier de configuration (app.config) d’application du projet :  
  
 \<\!--BTSMessagingEP--> \<point de terminaison address="net.tcp://*ordinateur BizTalk Server*: 8123/btsloadtest « liaison = bindingConfiguration de « netTcpBinding » = « netTcpBinding » contrat = » Nom de System.ServiceModel.Channels.IRequestChannel » = « BTSMessagingEP » / > \<point de terminaison address="net.tcp://*ordinateur BizTalk Server*: 8123/btsloadtest « liaison = « netTcpBinding » bindingConfiguration = contract="System.ServiceModel.Channels.IRequestChannel de « netTcpBinding » « nom = « BTSMessagingEP2 » / >  
  
> [!NOTE]
>  Comme indiqué précédemment, *ordinateur BizTalk Server* est un espace réservé pour les noms d’ordinateurs BizTalk Server réels ou, dans le cas que les ordinateurs BizTalk Server sont configurés en tant que membres d’un cluster d’équilibrage de charge réseau (NLB) ; *Ordinateur BizTalk Server* est un espace réservé pour le nom ou l’adresse du serveur virtuel NLB correspondant.  
  
 Pour des raisons de cet exemple, deux ordinateurs BizTalk Server ont été utilisées et la base de données MessageBox de BizTalk Server a été sur un ordinateur SQL Server distant.  
  
### <a name="create-biztalk-server-send-and-receive-hosts"></a>Créer l’envoi de BizTalk Server et des hôtes de réception  
 Suivez les étapes de la rubrique de la Documentation de BizTalk Server [la création d’un nouvel hôte](http://go.microsoft.com/fwlink/?LinkId=208595) (http://go.microsoft.com/fwlink/?LinkId=208595) pour créer un hôte « Envoi » de BizTalk Server pour les Ports d’envoi et les gestionnaires de l’adaptateur d’envoi. Configurer l’hôte avec les propriétés suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|Nom|TxHost|  
|Type|In-Process|  
|Autoriser le suivi de l'hôte|Assurez-vous que cette case est décochée.|  
|Approuvé(e) par authentification|Assurez-vous que cette case est décochée.|  
|32 bits uniquement|Assurez-vous que cette case est décochée.|  
|Transformer en hôte par défaut dans le groupe|Assurez-vous que cette case est décochée.|  
|Groupe Windows|Le groupe Windows utilisé pour contrôler l’accès à cet ordinateur hôte et les instances d’hôte associées. Le groupe de fenêtre créé pour l’hôte in-process par défaut est nommé soit  *\<nom de l’ordinateur >*\BizTalk utilisateurs de l’Application (pour un serveur unique, installation de BizTalk Server) ou  *\<domaine Nom >*\BizTalk utilisateurs de l’Application (pour une installation de BizTalk Server, ce qui nécessite l’utilisation de groupes de domaine avec plusieurs serveurs). **Remarque :***\<nom de l’ordinateur >* et  *\<nom de domaine >* sont des espaces réservés pour le nom d’ordinateur ou le nom de domaine utilisé lors de la création du groupe.   <br /><br /> Si un nouveau groupe est créé pour cet hôte, il doit avoir les droits décrits dans la rubrique [groupes hôtes](http://go.microsoft.com/fwlink/?LinkId=208803) (http://go.microsoft.com/fwlink/?LinkId=208803) dans la documentation de BizTalk Server.|  
  
 Répétez les étapes que vous avez suivi lors de la création de l’hôte « Envoi » pour créer un hôte « Réception ». Configurer l’ordinateur hôte « Réception » avec les valeurs de propriété suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|Nom|RxHost|  
|Type|In-Process|  
|Autoriser le suivi de l'hôte|Assurez-vous que cette case est décochée.|  
|Approuvé(e) par authentification|Assurez-vous que cette case est décochée.|  
|32 bits uniquement|Assurez-vous que cette case est décochée.|  
|Transformer en hôte par défaut dans le groupe|Assurez-vous que cette case est décochée.|  
|Groupe Windows|Le groupe Windows utilisé pour contrôler l’accès à cet ordinateur hôte et les instances d’hôte associées. Le groupe de fenêtre créé pour l’hôte in-process par défaut est nommé soit  *\<nom de l’ordinateur >*\BizTalk utilisateurs de l’Application (pour un serveur unique, installation de BizTalk Server) ou  *\<domaine Nom >*\BizTalk utilisateurs de l’Application (pour une installation de BizTalk Server, ce qui nécessite l’utilisation de groupes de domaine avec plusieurs serveurs). **Remarque :***\<nom de l’ordinateur >* et  *\<nom de domaine >* sont des espaces réservés pour le nom d’ordinateur ou le nom de domaine utilisé lors de la création du groupe.   <br /><br /> Si un nouveau groupe est créé pour cet hôte, il doit avoir les droits décrits dans la rubrique [groupes hôtes](http://go.microsoft.com/fwlink/?LinkId=208803) (http://go.microsoft.com/fwlink/?LinkId=208803) dans la documentation de BizTalk Server.|  
  
### <a name="create-instances-of-the-biztalk-server-send-and-receive-hosts"></a>Créer des Instances de l’envoi de BizTalk Server et des hôtes de réception  
 Suivez les étapes de la rubrique de la Documentation de BizTalk Server [l’ajout d’une Instance d’hôte](http://go.microsoft.com/fwlink/?LinkId=208596) (http://go.microsoft.com/fwlink/?LinkId=208596) pour créer et démarrer des instances de l’hôte « Envoi » de BizTalk Server. Configurer une instance de l’hôte « Envoi » pour exécuter sur chaque serveur BizTalk Server dans le groupe BizTalk Server et configurer chaque instance d’hôte avec les valeurs de propriété suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|**Nom d’hôte**|Sélectionnez **TxHost** dans la liste déroulante liste ensuite **nom d’hôte**.|  
|**Server**|Sélectionnez le serveur BizTalk qui exécutera ensuite à cette instance d’hôte dans la liste déroulante **Server**.|  
|**Ouverture de session**|1.  Cliquez sur le **configurer** bouton pour afficher la **informations d’identification d’ouverture de session** boîte de dialogue.<br />2.  Dans le **informations d’identification d’ouverture de session** boîte de dialogue Entrez les valeurs suivantes pour les propriétés spécifiées :<br />     **Propriété**<br />     **Ouverture de session**: nom du compte d’utilisateur qui est membre du groupe Windows associé à cet hôte BizTalk Server.<br />     **Mot de passe**: mot de passe du compte d’utilisateur spécifié dans le **ouverture de session** zone de texte.<br />3.  Cliquez sur **OK** pour fermer la **informations d’identification d’ouverture de session** boîte de dialogue.|  
|**Désactiver l’instance de l’hôte de démarrer.**|Assurez-vous que cette case est décochée.|  
  
 Après avoir créé l’instance d’hôte, avec le bouton droit sur l’instance d’hôte, puis sélectionnez **Démarrer** dans le menu contextuel.  
  
 Répétez les étapes que vous avez suivi lors de la création d’instances de l’hôte « Envoi » pour créer des instances d’hôte « Réception ». Configurer une instance de l’hôte « Réception » pour exécuter sur chaque serveur BizTalk Server dans le groupe BizTalk Server et configurer chaque instance d’hôte avec les valeurs de propriété suivantes :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|Nom d'hôte|Sélectionnez **RxHost** dans la liste déroulante liste ensuite **nom d’hôte**.|  
|Server|Sélectionnez le serveur BizTalk qui exécutera ensuite à cette instance d’hôte dans la liste déroulante **Server**.|  
|Connexion|1.  Cliquez sur le **configurer** bouton pour afficher la **informations d’identification d’ouverture de session** boîte de dialogue.<br />2.  Dans le **informations d’identification d’ouverture de session** boîte de dialogue Entrez les valeurs suivantes pour les propriétés spécifiées :<br />     **Propriété**<br />     **Ouverture de session**: nom du compte d’utilisateur qui est membre du groupe Windows associé à cet hôte BizTalk Server.<br />     **Mot de passe**: mot de passe du compte d’utilisateur spécifié dans le **ouverture de session** zone de texte.<br />3.  Cliquez sur **OK** pour fermer la boîte de dialogue informations d’identification d’ouverture de session.|  
|Désactiver le démarrage de l'instance de l'hôte|Assurez-vous que cette case est décochée.|  
  
 Après avoir créé l’instance d’hôte, avec le bouton droit sur l’instance d’hôte, puis sélectionnez **Démarrer** dans le menu contextuel.  
  
### <a name="create-a-biztalk-server-receive-port"></a>Créer un serveur BizTalk Server Port de réception  
 Suivez les étapes décrites dans la rubrique [la création d’un Port de réception](http://go.microsoft.com/fwlink/?LinkID=154843) (http://go.microsoft.com/fwlink/?LinkID=154843) dans la documentation de BizTalk Server pour créer un Port de réception unidirectionnel. Lorsque vous créez le port de réception, conservez toutes les propriétés par défaut, sauf comme indiqué dans le tableau ci-dessous :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|General\Name|BTSLoadTestMessaging.OneWay.ReceivePort|  
|Type de General\Port|Unidirectionnel|  
|General\Authentication|Pas d'authentification|  
|General\Enable routage pour les messages ayant échoué|Assurez-vous que cette case est décochée.|  
|General\Description|Laissez vide|  
|Mappages entrants|Aucune|  
|Suivi|Assurez-vous que toutes les cases sont non vérifiés.|  
|Emplacements de réception|Cliquez sur **nouveau**, cette action affiche la **propriétés de l’emplacement de réception** boîte de dialogue qui doit être configuré comme décrit dans la section suivante, **créer un emplacement de réception BizTalk Server** .|  
  
### <a name="create-a-biztalk-server-receive-location"></a>Créer un serveur BizTalk Server l’emplacement de réception  
 Dans le **propriétés de l’emplacement de réception** boîte de dialogue s’affiche lors de la création d’un port de réception BizTalk Server, appliquer des valeurs de propriété spécifiées :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|Nom :|BTSLoadTest.Messaging.OneWay.WCF-Customer.ReceiveLocation|  
|Gestionnaire de réception :|RxHost|  
|Pipeline de réception :|PassThruReceive|  
|Description :|Laissez ce champ vide|  
|Type :|Sélectionnez **WCF-Custom** dans la liste déroulante, puis cliquez sur le **configurer** bouton, cela permet d’afficher le **propriétés du Transport WCF-Custom** boîte de dialogue qui doit être configuré comme décrit dans la section suivante, **configurer le Transport de réception WCF-Custom**.|  
  
### <a name="configure-the-wcf-custom-receive-transport"></a>Configuration du Transport WCF-Custom réception  
 Dans le **propriétés du Transport WCF-Custom** boîte de dialogue s’affiche lors de la création de l’emplacement de réception BizTalk Server, conservez les valeurs par défaut, à l’exception de toutes les propriétés comme indiqué dans le tableau ci-dessous :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|General\Address (URI)|NET.TCP://localhost : 8123/btsloadtest|  
|Type de Binding\Binding|netTcpbinding|  
|Binding\NetTcpBindingElement\listenBacklog|400|  
|Binding\NetTcpBindingElement\maxConnections|400|  
|Binding\Security\NetTcpSecurityElement\mode|Aucune|  
|Behavior\ServiceBehavior\serviceThrottling\ServiceThrottlingElement **Remarque :** pour ajouter le comportement de serviceThrottling à la liste des comportements, ServiceBehavior d’avec le bouton droit, cliquez sur **Ajout d’une Extension**, sélectionnez **serviceThrottling** dans la liste des extensions de comportement, puis cliquez sur **OK**.|Définir le **ServiceThrottlingElement** propriétés les valeurs suivantes :<br /><br /> -   **accélérateur maxConcurrentCalls** 400<br />-   **maxConcurrentInstances** 400<br />-   **maxConcurrentSessions** 400|  
|Behavior\ServiceBehavior\serviceDebug\ServiceDebugElement **Remarque :** pour ajouter le comportement de serviceDebug à la liste des comportements, ServiceBehavior d’avec le bouton droit, cliquez sur **ajouter l’Extension**, sélectionnez **serviceDebug** dans la liste des extensions de comportement, puis cliquez sur **OK**.|Laissez la liste de **ServiceDebugElement** propriétés à leurs valeurs par défaut (vides) sauf pour les propriétés suivantes, qui doivent être remplacés par la valeur True :<br /><br /> -   **httpHelpPageEnabled** True<br />-   **httpsHelpPageEnabled** True<br />-   **includeExceptionDetailInFaults** True|  
  
 Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport WCF-Custom, puis cliquez sur **OK** à nouveau pour fermer la boîte de dialogue Propriétés de l’emplacement de réception.  
  
### <a name="create-a-biztalk-server-send-port"></a>Créer un Port d’envoi de BizTalk Server  
 Suivez les étapes décrites dans la rubrique [la création d’un Port d’envoi](http://go.microsoft.com/fwlink/?LinkID=154845) (http://go.microsoft.com/fwlink/?LinkID=154845) dans la documentation de BizTalk Server pour créer un **unidirectionnel statique** Port d’envoi. Lorsque vous créez le port d’envoi, conservez toutes les propriétés par défaut, sauf comme indiqué dans le tableau ci-dessous :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|General\Name|BTSLoadTest.Messaging.Send.WCF-Custom|  
|Gestionnaire de General\Send|TxHost|  
|Pipeline de General\Send|PassThruTransmit|  
|Filters\Name|BTS.ReceivePortName|  
|Filters\Operator|==|  
|Filters\Value|BTSLoadTest.Messaging.OneWay.ReceivePort|  
|Filters\Group par|Et **Remarque :** si ces propriétés sont configurées avec les valeurs correctes, le filtre doit être affiché comme `BTS.ReceivePortName == BTSLoadTest.Messaging.OneWay.ReceivePort` comme indiqué dans la partie inférieure de la page de filtres de la boîte de dialogue Propriétés de Port d’envoi b Ox. Suite à l’application de ce filtre, ce port d’envoi s’abonne à tous les messages reçus par BizTalk Server via le Port de réception nommé BTSLoadTest.Messaging.OneWay.ReceivePort.|  
|Suivi|Assurez-vous que toutes les cases sont non vérifiés.|  
|General\Type|Sélectionnez **WCF-Custom** dans la liste déroulante, puis cliquez sur le **configurer** bouton, cela permet d’afficher le **propriétés du Transport WCF-Custom** boîte de dialogue qui doit être configuré comme décrit dans la section suivante, **configurer le Transport d’envoi WCF-Custom**.|  
  
### <a name="configure-the-wcf-custom-send-transport"></a>Configurer le Transport d’envoi WCF-Custom  
 Dans le **propriétés du Transport WCF-Custom** boîte de dialogue s’affiche lors de la création du Port d’envoi de BizTalk Server, conservez les valeurs par défaut, à l’exception de toutes les propriétés comme indiqué dans le tableau ci-dessous :  
  
|Propriété|Valeur|  
|--------------|-----------|  
|General\Address (URI)|NET.TCP://*\<nom de l’ordinateur >*: 2001/TCP1 **Important :***\<nom de l’ordinateur >* est un espace réservé pour le nom d’ordinateur pour héberger IndigoService.exe, qui est conçue pour consommer les messages envoyés via WCF.   IndigoService.exe nécessite très peu de ressources, il est souvent parfaitement acceptable pour exécuter IndigoService.exe sur l’ordinateur SQL Server utilisé pour les bases de données du groupe BizTalk Server. IndigoService.exe fait partie de l’Assistant de test d’évaluation de BizTalk, qui est disponible sur [Assistant test d’évaluation de BizTalk](http://go.microsoft.com/fwlink/?LinkID=186347) (http://go.microsoft.com/fwlink/?LinkID=186347).|  
|Type de Binding\Binding|**customBinding**|  
  
 Comme avec la plupart des Types de liaison WCF-Custom, le **customBinding** type de liaison expose plusieurs propriétés, qui doivent être définies sur les valeurs suivantes :  
  
1.  Sous le **liaison** section est un **CustomBindingElement** propriété associé à un **Configuration** section. Laissez toutes les valeurs dans la section de Configuration pour le **CustomBindingElement** propriété à leurs valeurs par défaut.  
  
2.  Ensuite, sous **CustomBindingElement** avec le bouton droit **textMessageEncoding** et sélectionnez **supprimer l’extension (SUPPR)**. De même, avec le bouton droit **httpTransport** et sélectionnez **supprimer l’extension (SUPPR)**.  
  
3.  Maintenant avec le bouton droit **CustomBindingElement** et sélectionnez **ajouter une extension Ins** pour afficher les **sélectionnez Extension d’élément de liaison** boîte de dialogue.  
  
4.  Sélectionnez **binaryMessageEncoding** et cliquez sur **OK** pour ajouter le **binaryMessageEncoding** extension d’élément. Répétez les étapes pour afficher le **sélectionnez Extension d’élément de liaison** boîte de dialogue et faites défiler vers le bas la liste des extensions d’élément disponibles jusqu'à ce que vous voyiez la **tcpTransport** extension d’élément, sélectionnez **tcpTransport** et cliquez sur **OK**.  
  
5.  Sous **CustomBindingElement** sélectionner le **tcpTransport** élément et, dans la section de Configuration pour **tcpTransport**, conservez les valeurs par défaut, sauf en tant que toutes les propriétés indiquée dans le tableau suivant :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |connectionBufferSize|2097152|  
    |maxBufferSize|2097152|  
    |maxPendingAccepts|400|  
    |maxPendingConnections|400|  
    |listenBacklog|400|  
    |maxBufferPoolSize|2097152|  
    |maxReceivedMessageSize|2097152|  
  
6.  Sous le **tcpTransport** élément select le **ConnectionPoolSettings** élément et laissez les valeurs de toutes les propriétés par défaut à l’exception de la **maxOutboundConnectionsPerEndpoint** propriété, qui doit être changée en une valeur de 400.  
  
7.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport WCF-Custom, puis cliquez sur **OK** à nouveau pour fermer la boîte de dialogue Propriétés de Port d’envoi BTSLoadTest.Messaging.Send.WCF-Custom :.  
  
### <a name="configure-a-computer-to-consume-messages-sent-by-the-biztalk-server-send-port"></a>Configurer un ordinateur pour consommer des Messages envoyés par le Port d’envoi de BizTalk Server  
 Comme décrit précédemment, le IndigoService.exe est conçue pour consommer des messages envoyés via WCF. IndigoService.exe fait partie de l’Assistant de test d’évaluation de BizTalk, qui est disponible sur [Assistant test d’évaluation de BizTalk](http://go.microsoft.com/fwlink/?LinkID=186347) (http://go.microsoft.com/fwlink/?LinkID=186347). Le moyen le plus simple à configurer et exécuter IndigoService.exe pour les besoins de cet exemple consiste à simplement télécharger le fichier zip Assistant test d’évaluation de BizTalk à partir de la [page de téléchargement de l’Assistant BizTalk banc d’essai](http://go.microsoft.com/fwlink/?LinkID=209100) (http://go.Microsoft.com/fwlink/?) LinkID = 209100) et extrayez les fichiers suivants 4 sur l’ordinateur que vous souhaitez exécuter IndigoService.exe :  
  
1.  \IndigoService\bin\Release\IndigoService.exe  
  
2.  \IndigoService\bin\Release\IndigoService.exe.config  
  
3.  \IndigoService\bin\Release\Response.Xml  
  
4.  \IndigoService\bin\Release\StartIndigoService.bat  
  
 Ensuite, démarrez IndigoService.exe en double-cliquant sur StartIndigoService.bat. IndigoService.exe consomme des messages envoyés au point de terminaison spécifié dans le fichier IndigoService.exe.config :  
  
 \<adresse de point de terminaison = « NET.TCP://localhost : 2001/TCP1 « liaison = bindingConfiguration de « netTcpBinding » = nom de « Binding1 » = « endpoint1 » contract="IndigoService.IServiceTwoWaysVoidNonTransactional » / >  
  
 C’est pourquoi l’adresse du Port d’envoi est configuré avec une adresse (URI) de net.tcp://*\<nom de l’ordinateur >*: 2001/TCP1  
  
 IndigoService.exe nécessite très peu de ressources, il est souvent parfaitement acceptable pour exécuter IndigoService.exe sur l’ordinateur SQL Server utilisé pour les bases de données BizTalk Server.  
  
### <a name="disable-tracking-and-throttling-for-the-biztalk-server-group"></a>Désactiver le suivi et la limitation pour le groupe BizTalk Server  
 Afin de déterminer le débit maximal acceptable absolu du système, des messages de suivi et limitation doivent être désactivée avant de commencer le test de charge. Cela est possible à l’aide de la console Administration de BizTalk Server en procédant comme suit :  
  
1.  Lancez la console Administration de BizTalk Server. Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **BizTalk Server 2010** puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Sous **Administration de BizTalk Server**, sélectionnez votre groupe BizTalk si elle est répertoriée ou si elle n’est pas répertorié, cliquez sur **Administration de BizTalk Server**, sélectionnez **se connecter au groupe existant** , entrez le nom de SQL Server qui héberge à côté de base de données de gestion BizTalk Server du groupe BizTalk **nom SQL Server :**, entrez le nom du nom de base de données de gestion BizTalk du groupe en regard de **Nom de la base de données :** puis cliquez sur **OK**.  
  
3.  Cliquez sur le nœud groupe BizTalk et sélectionnez **paramètres** pour afficher la **Panneau de configuration BizTalk**.  
  
4.  Cliquez pour sélectionner **hôtes** dans le volet gauche du Panneau de configuration de BizTalk.  
  
5.  Cliquez sur la liste déroulante en regard **hôte** pour sélectionner l’un des hôtes qui seront utilisés pendant le test de performances.  
  
6.  Laissez les propriétés à leurs valeurs par défaut, sauf comme indiqué dans le tableau suivant :  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |**General\Move des données de suivi pour la base de données DTA**|Désactivez cette case à cocher si elle est activée.|  
    |**General\32 bits uniquement**|Désactivez cette case à cocher si elle est activée.|  
    |**General\Polling Intervals\Messaging**|Une valeur de 20000000|  
    |**General\Polling Intervals\Orchestrations**|Une valeur de 20000000|  
    |**Basée sur la ressource Throttling\In-traitement des messages**|Une valeur de 10 000|  
    |**Taille de file d’attente de message Throttling\Internal basée sur la ressource**|Une valeur de 10 000|  
    |**Nombre de Throttling\Message basée sur la ressource dans la base de données**|Une valeur égale à 0|  
    |**Basée sur la ressource Throttling\Memory Usage\Process virtuel**|Une valeur égale à 0|  
    |**Basée sur la fréquence de remplacement de Throttling\Publishing\Throttling**|Ne pas limiter la valeur|  
    |**Basée sur la fréquence de remplacement de Throttling\Delivery\Throttling**|Ne pas limiter la valeur|  
  
7.  Répétez le processus décrit à l’étape 6 pour chaque hôte qui sera utilisé au cours du test de performances.  
  
8.  Cliquez pour sélectionner **Instances d’hôte** dans le volet gauche du Panneau de configuration de BizTalk.  
  
9. Cliquez sur la liste déroulante en regard **Instance d’hôte :** pour sélectionner une des instances d’hôte qui seront utilisés pour les tests de performances.  
  
10. Laissez les valeurs de propriété à leur valeur par défaut, sauf le changement le **.NET CLR maximal de threads de travail** à une valeur de **100** et modifiez le **de threads de travail .NET CLR Minimum** à un valeur de **25**.  
  
11. Répétez le processus décrit à l’étape 10 pour chaque instance d’hôte qui sera utilisé au cours du test de performances.  
  
 Bien que la désactivation de suivi et la limitation n’en aucune façon représente ce qui doit être fait dans un scénario de production, car ces opérations sont très coûteuses à partir d’un point de vue de performances qu'il est judicieux de les désactiver pour déterminer la valeur est true maximale acceptable Débit (débit maximal acceptable) d’un environnement BizTalk Server. Cela permet aux testeurs de voir clairement l’impact des performances d’un ajustement qui a été appliqué à l’environnement. Certainement un argument a pu être établie que le suivi ne doit pas être désactivé et si vous savez dès que votre application BizTalk Server nécessite le suivi vous devez activer le suivi. Cela étant dit, **tout doit être fait pour désactiver la limitation à des fins de tests de performances**. La limitation est très utile pour empêcher un serveur BizTalk Server à partir de « tomber » en raison d’une charge excessive dans un environnement de production. Toutefois, vous ne souhaitez pas activé au cours du test de performances, car il est coûteux à partir d’un point de vue des performances et parce que si la limitation intervient pendant un test de charge vous disposez d’un temps très difficile de déterminer le niveau de performances de limitation votre L’application BizTalk Server peut faire. Les rubriques suivantes décrivent comment effectuer des tests de charge étape pour transmettre votre environnement BizTalk Server au-delà de débit maximal acceptable et ensuite mettre à l’échelle à réel au débit maximal acceptable à des tests de charge constant. Si la limitation est activée il deviendra push de votre environnement BizTalk au-delà de débit maximal acceptable afin que vous pourriez découvrir à son tour la la true au débit maximal acceptable est pratiquement impossible.