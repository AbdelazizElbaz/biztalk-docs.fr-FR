---
title: "Problèmes connus pour les adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 423c6021-5fb7-48c9-9319-11e7a18c775c
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ccdc0c0f36f2dca474b962d3f108e4f287e378f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-for-the-wcf-adapters"></a>Problèmes connus pour les adaptateurs WCF
Cette rubrique décrit les problèmes connus des adaptateurs WCF inclus avec [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
## <a name="a-message-that-fails-in-the-inbound-soap-marshaling-processing-is-not-suspended-in-wcf-receive-adapters"></a>Un message échouant au cours du traitement de marshaling SOAP entrant n'est pas interrompu dans les adaptateurs de réception WCF.  
 Lorsqu'un message arrive à un adaptateur de réception WCF, ce dernier crée un message BizTalk à partir du message SOAP entrant, puis transmet le message BizTalk au proxy de transport géré par le Gestionnaire des points de terminaison. Si l'adaptateur ne peut pas lire l'enveloppe et le corps SOAP lors de la création du message BizTalk, le message n'est pas interrompu car l'adaptateur utilise le lecteur rapide, non mis en cache et vers l'avant uniquement, pour accéder au message SOAP.  
  
 Vous devez rechercher le message échoué dans le journal des événements. Par exemple, vous pouvez utiliser une expression de chemin de corps sur le **Messages** onglet dans la boîte de dialogue Propriétés WCF adaptateur transport pour spécifier comment créer le corps du message BizTalk entrant à partir d’un message SOAP entrant via l’adaptateur WCF. Lorsqu’une expression de chemin de corps non valide pour le message SOAP entrant est fournie sous la **Messages** onglet, l’adaptateur ne créer le message BizTalk et ne peut pas interrompre le message entrant. Pour plus d’informations sur l’utilisation de l’expression de chemin de corps sur le **Messages** , consultez la rubrique [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
 L’illustration suivante montre le **Messages** onglet sur lequel vous pouvez spécifier comment créer des messages BizTalk entrants à partir des messages SOAP entrants.  
  
## <a name="a-message-that-fails-in-the-inbound-soap-marshaling-processing-is-not-suspended-in-wcf-send-adapters"></a>Un message échouant au cours du traitement de marshaling SOAP entrant n'est pas interrompu dans les adaptateurs d'envoi WCF.  
 Le port d'envoi WCF de type sollicitation-réponse peut recevoir un message WCF en tant que message de réponse. Lorsque le message arrive à l'adaptateur d'envoi WCF, ce dernier crée le message BizTalk à partir du message SOAP entrant, puis transmet le message BizTalk au proxy de transport géré par le Gestionnaire des points de terminaison. Si l'adaptateur ne peut pas lire l'enveloppe et le corps SOAP lors de la création du message BizTalk, le message n'est pas interrompu car l'adaptateur utilise le lecteur rapide, non mis en cache et vers l'avant uniquement, pour accéder au message SOAP.  
  
 Vous devez rechercher le message échoué dans le journal des événements. Par exemple, vous pouvez utiliser une expression XPath sur le **Messages** onglet dans la boîte de dialogue Propriétés WCF adaptateur transport pour spécifier comment créer le corps du message BizTalk entrant à partir d’un message SOAP entrant via l’adaptateur WCF. Lorsqu’une expression XPath non valide pour le message SOAP entrant est fournie sous la **Messages** onglet, l’adaptateur ne créer le message BizTalk et ne peut pas interrompre le message entrant. Pour plus d’informations sur l’utilisation de l’expression XPath sur le **Messages** , consultez la rubrique [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
 L’illustration suivante montre le **Messages** onglet de l’adaptateur d’envoi WCF-NetNamedPipe par exemple.  
  
 ![L’onglet des Messages WCF des adaptateurs d’envoi](../core/media/54623ccf-49a9-4b6a-9487-da0d94bab64d.gif "54623ccf-49a9-4b6a-9487-da0d94bab64d")  
  
## <a name="messages-can-be-lost-when-using-onewaybindingelement-in-a-two-way-transport-with-custom-binding-in-non-transactional-wcf-receive-locations"></a>Des messages peuvent être perdus lors de l'utilisation de OneWayBindingElement dans un transport bidirectionnel avec une liaison personnalisée dans les emplacements de réception WCF non transactionnels.  
 Dans une communication bidirectionnelle, les adaptateurs WCF renvoient la réponse jusqu'à la conservation des messages dans la base de données MessageBox. Toutefois, à l’aide de **OneWayBindingElement** génère une réponse factice juste avant de distribuer le message reçu à l’adaptateur WCF. Par conséquent, si vous configurez une liaison personnalisée avec un **OneWayBindingElement** dans la pile de canal pour un transport bidirectionnel dans non transactionnel emplacements de réception, les messages peuvent être perdus car les adaptateurs WCF traitent les données reçues messages de manière unidirectionnelle.  
  
## <a name="default-values-of-the-readerquotas-attributes-in-the-wcf-custom-and-wcf-customisolated-transport-properties-dialog-boxes-are-used-when-constructing-the-bindings"></a>Des valeurs par défaut des attributs ReaderQuotas dans les boîtes de dialogue Propriétés du transport WCF-Custom et WCF-CustomIsolated sont utilisées lors de la construction des liaisons.  
 Dans WCF-Custom et WCF-CustomIsolated, les boîtes de dialogue des propriétés de transport le **ReaderQuotas** valeurs d’attribut sont affichés comme zéro. Toutefois, lors de la construction des liaisons, les valeurs suivantes sont utilisées :  
  
|Attribut| Description|Valeur|  
|---------------|-----------------|-----------|  
|maxArrayLength|Entier positif qui spécifie la longueur de tableau maximale autorisée.|16384|  
|maxBytesPerRead|Entier positif qui spécifie le nombre maximal autorisé d'octets renvoyés par lecture.|4096|  
|maxDepth|Entier positif qui spécifie la profondeur maximale du nœud imbriqué par lecture.|32|  
|maxNameTableCharCount|Entier positif qui spécifie le nombre maximal de caractères autorisés dans un nom de table.|16384|  
|maxStringContentLength|Entier positif qui spécifie le nombre maximal de caractères autorisés dans le contenu d'un élément XML.|8192|  
  
## <a name="the-wcf-receive-locations-may-be-disabled-if-you-change-the-wcf-adapter-type-and-keep-the-same-address"></a>Les emplacements de réception WCF risquent d'être désactivés si vous modifiez le type d'adaptateur WCF et conservez la même adresse.  
 Si vous modifiez le type d'adaptateur (par exemple, si vous modifiez l'adaptateur WCF de WCF-NetTcp en WCF-Custom avec la liaison NetTcp) et que vous conservez la même adresse, l'emplacement de réception risque d'être désactivé en raison du problème de mise en cache dans le Gestionnaire des points de terminaison. Pour contourner ce problème, vous pouvez effectuer l'une des opérations suivantes :  
  
-   Redémarrez le service BTSNTSvc.  
  
-   Modifiez l'URI en une adresse différente et enregistrez-la, puis remodifiez l'URI en l'adresse d'origine et enregistrez-la de nouveau.  
  
## <a name="the-wcf-action-set-in-the-orchestration-does-not-override-the-action-setting-in-the-static-send-port"></a>L'action WCF définie dans l'orchestration ne remplace pas la définition d'action dans le port d'envoi statique.  
 Si vous définissez la **WCF. Action** propriété de contexte de l’orchestration, vous devez laisser la **Action** champ vide dans la boîte de dialogue Propriétés du transport WCF adaptateur. Si vous spécifiez également une action dans le port d’envoi statique, le **WCF. Action** propriété de contexte que vous définissez dans l’orchestration sera remplacée par la valeur définie dans le port d’envoi statique.  
  
## <a name="propagating-a-fault-message-is-not-supported-in-the-transactional-send"></a>La répercussion d'un message d'erreur n'est pas prise en charge dans l'envoi transactionnel  
 Le **répercuter le message d’erreur** dans les ports d’envoi de sollicitation-réponse permet de router les messages qui échouent le traitement sortant vers une application abonnée. Toutefois, si le **activer les transactions** est également activée dans la boîte de dialogue des propriétés de transport et la transaction est abandonnée ou n’est pas utilisable lors de la réponse d’erreur arrive à la carte, vous seront pas en mesure de se propager le messages d’erreur sur des applications abonnées  
  
## <a name="the-msmq-cluster-resource-group-needs-to-be-restarted-before-restarting-the-biztalk-host-cluster-resource-group-during-the-cluster-failover"></a>Le groupe de ressources en cluster MSMQ doit être redémarré avant le redémarrage du groupe de ressources en cluster de l'hôte BizTalk lors du basculement de cluster.  
 Dans un scénario de cluster de basculement, lorsqu'un basculement a lieu, le groupe de ressources en cluster MSMQ doit être redémarré avant le redémarrage du groupe de ressources en cluster de l'hôte BizTalk. Si vous ne parvenez pas à le faire, les emplacements de réception MSMQ risquent d'être désactivés. Pour contourner ce problème, vous pouvez rendre le groupe de ressources en cluster de l'hôte BizTalk dépendant du groupe de ressources en cluster MSMQ pour garantir le redémarrage du groupe de ressources en cluster MSMQ avant le groupe de ressources en cluster de l'hôte BizTalk. Vous pouvez également redémarrer le groupe de ressources en cluster de l'hôte BizTalk pour contourner ce problème.  
  
## <a name="you-receive-an-error-when-sending-messages-to-a-wcf-service-that-uses-wsfederationhttpbinding-in-the-endpoint"></a>Vous obtenez une erreur lors de l'envoi de messages à un service WCF utilisant wsFederationHttpBinding dans le point de terminaison.  
 Vous obtenez une erreur semblable à celle-ci :  
  
```  
The adapter failed to transmit message going to send port "MySendPort" with URL "http://localohost/MywsFedHttp". It will be retransmitted after the retry interval specified for this Send Port. Details:"The channel is configured to use interactive initializer 'System.ServiceModel.Security.InfocardInteractiveChannelInitializer', but the channel was Opened without calling DisplayInitializationUI.  Call DisplayInitializationUI before calling Open or other methods on this channel.".  
```  
  
 Ce comportement est par défaut. Adaptateurs WCF ne peut pas envoyer des messages aux services WCF qui utilisent **wsFederationHttpBinding** dans leurs points de terminaison.  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-enable-you-to-select-message-types-or-port-types-from-the-wsdl"></a>L'Assistant Consommation de service WCF BizTalk ne vous permet pas de sélectionner les types de messages ou les types de ports à partir de WSDL.  
 L'Assistant Consommation de service WCF BizTalk ne vous permet pas de sélectionner les types de messages ou les types de ports à partir de WSDL, lors de l'importation de services WCF. Pour contourner cette restriction, vous pouvez utiliser le code suivant afin d'obtenir les schémas et ajouter les schémas souhaités à vos projets BizTalk :  
  
```  
svcutil.exe /t:metadata http://service/metadataendpoint  
```  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-allow-the-combination-of-one-way-and-request-response-operations"></a>L'Assistant Consommation de service WCF BizTalk ne permet pas la combinaison d'opérations unidirectionnelles et requête-réponse.  
 L'Assistant Consommation de service WCF BizTalk ne vous permet pas d'importer les types de ports qui ont une combinaison d'opérations unidirectionnelle et requête-réponse. Pour contourner ce problème, vous pouvez utiliser l'outil Service Model Metadata Utility Tool pour générer les types de ports.  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-allow-you-to-set-certificate-credentials-when-retrieving-the-wsdl"></a>L’Assistant de consommation de Service WCF BizTalk n’autorise pas vous permet de définir les informations d’identification de certificat lors de la récupération de WSDL  
 L'Assistant Consommation de service WCF BizTalk ne vous permet pas de définir les informations d'identification des certificats lors de l'extraction du WSDL. Pour contourner ce problème, vous pouvez utiliser le service Model Metadata Utility Tool pour générer le WSDL et les fichiers XSD à partir des services WCF pour utiliser les informations d’identification du certificat défini dans le fichier svcutil.exe.config, puis les importer dans le Service WCF BizTalk Assistant consommation en choisissant **des fichiers de métadonnées (WSDL et XSD)** option dans le **source des métadonnées** page.  
  
## <a name="wcf-adapters-do-not-support-one-way-operations"></a>Les adaptateurs WCF ne prennent pas en charge les opérations unidirectionnelles.  
 Vous recevrez un message d’erreur semblable au suivant lors de l’utilisation des services WCF publiés avec les adaptateurs WCF (sauf l’adaptateur de réception WCF-netmsmq) si le **IsOneWay** est définie sur **true**côté client. C’est parce que le **System.ServiceModel.OperationContractAttribute.IsOneWay** des services WCF publiés avec les adaptateurs WCF (sauf pour l’adaptateur de réception des services publiés avec WCF-NetMsmq) est définie sur **false** même pour les emplacements de réception l’unidirectionnels.  
  
```  
The channel received an unexpected input message while closing. Your Channel.Close() calls are not synchronized.  
```  
  
 Vous recevrez un message d’erreur semblable au suivant lors de l’utilisation des services WCF spécifiés avec le **IsOneWay** propriété **true**. Les messages que vous envoyez à partir de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont interrompus et peuvent être repris.  
  
```  
The request operation at net.tcp://localhost:8088/MyService/tcp did not receive a reply within timeout 00:01:00.  
```  
  
## <a name="a-memory-leak-may-occur-when-sending-messages-to-non-transactional-msmq-queues-using-wcf-netmsmq-binding"></a>Une fuite de mémoire peut se produire lors de l'envoi de messages aux files d'attente MSMQ non transactionnelles à l'aide de la liaison WCF-NetMsmq.  
 Une fuite de mémoire peut se produire dans le service NT BizTalk lors de l'envoi de messages aux files d'attente MSMQ non transactionnelles à l'aide de la liaison WCF-NetMsmq. Cela peut arriver lorsque vous envoyez des messages à une file d'attente MSMQ non transactionnelle à l'aide du transport WCF-NetMsmq ou lorsque vous envoyez des messages à une file d'attente MSMQ non transactionnelle utilisant netMsmqBinding avec le transport WCF-Custom.  
  
 Pour résoudre ce problème, vous devez installer le correctif .NET Framework 3.0 décrit dans l’article 936512 à [http://go.microsoft.com/fwlink/?LinkId=92962](http://go.microsoft.com/fwlink/?LinkId=92962). Le correctif ne requiert pas de redémarrage système mais il est nécessaire de redémarrer le service NT BizTalk qui héberge les ports d'envoi utilisant la liaison WCF-NetMsmq.  
  
## <a name="you-may-receive-exception-when-communicating-with-apache-web-servers-using-wcf-basichttp-adapter"></a>Vous pouvez obtenir une exception lors de la communication avec les serveurs Web Apache à l'aide de l'adaptateur WCF-BasicHttp.  
 Lorsque vous utilisez l'adaptateur WCF-BasicHttp avec la sécurité du transport pour communiquer avec un serveur Web Apache, vous pouvez obtenir une exception semblable à ce qui suit :  
  
```  
System.Net.WebException: The underlying connection was closed: An unexpected error occurred on a send.  
System.IO.IOException: Unable to write data to the transport connection: An established connection was aborted by the software in your host machine. System.Net.Sockets.SocketException: An established connection was aborted by the software in your host machine  
```  
  
 Pour contourner ce problème, vous devez utiliser l'adaptateur WCF-Custom à la place de l'adaptateur WCF-BasicHttp pour communiquer avec les serveurs Web Apache, comme suit :  
  
1.  Créer un port d’envoi et de définir le type de transport sur **WCF-Custom**.  
  
2.  Dans le **propriétés du Transport WCF-Custom** boîte de dialogue le **liaison** onglet, sélectionnez **customBinding** à partir de la **Type de liaison** liste déroulante.  
  
3.  Sous **Custombindingelement**, avec le bouton droit **httpTransport**, puis cliquez sur **supprimer l’extension**.  
  
4.  Avec le bouton droit **Custombindingelement**, puis cliquez sur **ajouter une extension**.  
  
5.  Dans le **sélectionnez Extension d’élément de liaison** boîte de dialogue, sélectionnez **httpTransport** puis cliquez sur **OK**.  
  
6.  Cliquez sur **httpTransport**, puis, dans le **Configuration** volet, définissez la valeur de **keepAliveEnabled** à **False**.  
  
7.  Cliquez sur **textMessageEncoding**, puis, dans le **Configuration** volet, définissez la valeur de **messageVersion** à `Soap11WSAddressing10`.  
  
8.  Vous devrez peut-être configurer des propriétés supplémentaires si nécessaire.  
  
## <a name="biztalk-server-does-not-work-with-wcf-clients-that-using-clientviabehavior-for-multiple-hop-conversations"></a>BizTalk Server ne fonctionne pas avec les clients WCF qui utilisent ClientViaBehavior pour les conversations à tronçons multiples.  
 Les clients WCF utilisent ClientViaBehavior lorsque la destination réseau immédiate n'est pas le processeur prévu du message pour permettre les conversations à tronçons multiples lorsque l'application d'appel ne connaît pas nécessairement la destination ultime. Si vous spécifiez ClientViaBehavior et pointez l'adresse d'expédition sur un service distant où [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] agit comme un intermédiaire, vous obtenez un message d'erreur semblable à ce qui suit :  
  
```  
The message with To 'net.tcp://localhost:5555/test.svc' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher. Check that the sender and receiver's EndpointAddresses agree  
```