---
title: Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, headers
- messages, acknowledgements
- messages, persisting
- messages
- examples, message headers
- properties
- message headers
- EMS messages
ms.assetid: 65bb3431-7186-4d4c-b004-932cdf070e73
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f7313e93029ca75d345aa4e9603699c50399230
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="messages"></a>Messages
Un message Enterprise Message Service (EMS), comme un message JMS, contienne trois parties distinctes : en-tête, les propriétés et les corps. L'en-tête est la seule partie obligatoire d'un message EMS. Cette rubrique décrit le traitement des messages dans l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service.  
  
> [!NOTE]
>  Pour définir ou extraire un champ d’en-tête (par exemple, définir la priorité du Message ou l’ID de corrélation) ou une propriété de message à partir de l’orchestration, vous devez ajouter une référence à la **Microsoft.BizTalk.Adapters.TIBCOEMSProperties.dll** dans votre projet à l’aide de l’Explorateur de solutions.  
  
## <a name="message-header"></a>En-tête de message  
 L'en-tête de message contient une série de champs prédéfinis qui contiennent des valeurs. L'adaptateur BizTalk pour TIBCO Enterprise Message Service sait ce qu'il peut ou non définir dans l'en-tête. Si vous tentez de définir une valeur en lecture seule, l'adaptateur redirige ou définit votre valeur dans la section Properties{}.  
  
### <a name="header-example"></a>Exemple d'en-tête  
 Dans l’exemple suivant, notez que **propriétés = {Destination = {String : Queue [Q2]}}**. `Properties`est une propriété qui contient une chaîne, et le contenu de la chaîne est **Q2**. Cela n'a rien à voir avec la section Destination qui contient des chaînes de valeurs que vous définissez et qui n'ont pas pu aller ailleurs, donc l'adaptateur les a gardées dans cette section.  
  
 La propriété `ReplyTo` peut être définie dans l'orchestration pour dire à un éventuel client où envoyer une réponse. EMS définit la propriété `Destination` lorsque le message est reçu de TIBCOEMS. Cette seconde propriété est en lecture seule dans l'orchestration recevant le message de TIBCOEMS et ne peut pas être éditée dans l'orchestration.  
  
 Par exemple, une orchestration ne peut pas distribuer des messages et définir la destination de manière dynamique au sein d'une orchestration. La valeur de Destination est définie par le port auquel le message est transmis.  
  
 Si vous voulez distribuer des messages à différentes files d'attente, vous devez créer des ports d'envoi pour chaque file d'attente. L'orchestration peut alors décider à quel port attribuer le message.  
  
 Dans l'exemple de message suivant, la Destination = `{Queue[Q1]}` est en lecture seule. Cette valeur est définie par TIBCOEMS lorsque le serveur reçoit le message. La valeur de Destination, Q1, provient des Propriétés du transport.  
  
#### <a name="example"></a>Exemple  
  
```  
TextMessage={   
    Header={ MessageID={ID:EMS-SERVER.824437A58B11C75F4:1}   
    Destination={Queue[Q1]}   
  
        ' This is READONLY. It gets set by the server when the  
        ' message is received by the server (EMS). It is set in the  
        ' Transport Properties when you specify that you want to  
        ' listen for messages on Q1.  
    ReplyTo={}   
    DeliveryMode={Persistent}   
    Redelivered={False}   
    CorrelationID={}   
    MsgType={}   
    Timestamp={12/1/2005 11:59:01 PM}   
    Expiration={0}   
    Priority={1} }   
    Properties={ Destination={String:Queue[Q2]} }   
  
        ' This is a property that contains a string, and the   
        ' contents of the string is Q2. This has nothing to do with  
        ' the Destination section above – it is just another   
        ' property that is set.   
        ' This is in the schema. The adapter knows what it can and   
        ' cannot set in an EMS header. The values that the adapter   
        ' cannot set are put in the Properties section.   
    text={<?xml version="1.0" encoding="utf-16"?>  
    <ns0:Employees xmlns:ns0="http://BizTalk_Server_Project1.Employee">  
        <Emp Id="Id_0">  
            Name>Name_0</Name>  
        </Emp>  
    </ns0:Employees>  
    }  
```  
  
 L'en-tête contient une série de champs prédéfinis qui contiennent des valeurs, que l'adaptateur promeut dans le contexte de message de BizTalk Server pour les utiliser dans l'orchestration. Les propriétés promues sont identiques, en termes de définition, aux propriétés d'en-tête standard telles que définies par la spécification JMS et les extensions TIBCO Enterprise Message Service. Toutes les propriétés à l’exception des deux sont disponibles pour l’orchestration comme reçues d’EMS : `Destination` et `ReplyTo` décrivent une destination ne peut pas être correctement mappée pour une utilisation dans une orchestration en tant qu’une seule propriété.  
  
 L'adaptateur BizTalk pour TIBCO EMS mappe la propriété TIBCOEMS à un type de chaîne et utilise la représentation de chaîne Destination. Cela ressemble à `StaticQueue[queuename]` ou `StatisTopic[topicname]`. L'orchestration peut définir la valeur de `ReplyTo` et l'adaptateur la remplace par un objet de destination valide dans l'en-tête.  
  
 L'adaptateur fournit un schéma et un assembly de référence décrivant toutes les propriétés d'en-tête TIBCO EMS pouvant être utilisées par des orchestrations. Ces propriétés peuvent être utilisées pour filtrer des messages entrants ou s'ajouter au message sortant. Les règles qui régissent le filtre d'orchestration diffèrent de celles du sélecteur de message pour le serveur EMS. Par exemple, les orchestrations peuvent filtrer selon la propriété `TibcoEMS.ReplyTo` ou `TibcoEMS.Destination` mais la spécification JMS ne permet pas de définir le sélecteur de message sur cette même propriété.  
  
 Lorsque ces propriétés sont définies par l'orchestration, elles sont incluses dans les propriétés de l'en-tête du message JMS. Autrement, lorsque le message EMS est reçu, ces propriétés d'en-tête sont copiées dans le contexte de message BizTalk Server.  
  
 Quand une propriété correspond à la configuration du port, la valeur de la propriété sur le message prime sur la configuration du port. Par exemple, si la priorité est définie sur 4 dans le port mais que vous avez défini la priorité du message sur 9 dans la logique de l'orchestration, le message est reçu par TIBCO EMS avec une priorité 9.  
  
### <a name="property-descriptions"></a>Description des propriétés  
 Le tableau suivant décrit comment chaque propriété est utilisée par l'adaptateur BizTalk pour TIBCO Enterprise Message Service.  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|TibcoEMS.MessageID|chaîne|Les appels d'envoi attribuent un ID unique à chaque message et l'enregistrent dans l'en-tête.<br /><br /> Toutes les valeurs d'ID de message commencent par l'ID de préfixe à trois caractères (réservé à cet usage).<br /><br /> En lecture seule. La modification de la valeur n'affecte pas le message.|  
|TibcoEMS.Timestamp|long|Les appels d'envoi enregistrent un horodatage UTC dans l'en-tête. Cela indique l'heure approximative à laquelle le serveur a accepté le message.<br /><br /> La valeur est exprimée en millisecondes depuis le 1er janvier 1970.<br /><br /> En lecture seule. La modification de la valeur n'affecte pas le message.|  
|TibcoEMS.Redelivered|boolean|Le serveur définit l'en-tête pour indiquer si un message risque de créer un doublon avec un message livré précédemment :<br /><br /> -valeur est false, le serveur n’a pas déjà essayé de livrer ce message au client.<br />-valeur est true, il est probable, mais non garanti, que le serveur a déjà tenté de remettre ce message au consommateur, mais le consommateur n’a pas renvoyé d’accusé de réception en temps voulu.<br /><br /> En lecture seule. La modification de la valeur n'affecte pas le message.|  
|TibcoEMS.Destination|chaîne|Les appels d'envoi enregistrent la destination (file d'attente ou rubrique) du message dans cet en-tête. Le format est adapté d'une destination à une chaîne. Le format est décrit précédemment.<br /><br /> En lecture seule. La modification de la valeur n'affecte pas le message.|  
|TibcoEMS.DeliveryMode|chaîne|A deux valeurs possibles : persistant et NON persistant. La valeur par défaut est le mode PERSISTANT.<br /><br /> L'adaptateur attend un accusé de réception du serveur EMS avant d'accuser réception du message envoyé à BizTalk Server. Cet élément de propriété d'en-tête et de configuration de port contrôle le temps mis par EMS pour envoyer cet accusé de réception à l'adaptateur et contrôler la fiabilité de la transmission du message.<br /><br /> Utilisation du mode de livraison PERSISTANT — Le serveur EMS attend que le message ait été conservé avec succès dans le serveur EMS. Cette action garantit que le message est arrivé dans la file d'attente. Lorsque vous utilisez le mode de livraison PERSISTANT, tenez compte des éléments suivants :<br /><br /> Plus les messages sont volumineux, plus BizTalk Serveur met de temps à considérer le message comme envoyé.<br /><br /> Utilisation du mode de livraison NON PERSISTANT — Le serveur EMS renvoie l'accusé de réception avant de conserver le message. En cas d'échec du serveur EMS, le message risque d'être perdu s'il est considéré comme envoyé avec succès par BizTalk Server.|  
|TibcoEMS.Expiration|long|Durée de vie du message avant expiration. Si la valeur est définie sur 0, le message n'expire pas.<br /><br /> La durée de vie est exprimée en millisecondes.|  
|TibcoEMS.Priority|int|Utilise un classement numérique, entre 0 et 9, pour définir la priorité du message sur normale ou accélérée. Plus le chiffre est grand, plus la priorité est élevée.|  
|TibcoEMS.CorrolationID|chaîne|Peut servir à lier des messages, comme un message de réponse à un message de requête.<br /><br /> Il s'agit, en général, de la même valeur que `EMS.JMSMessageID`. Elle est généralement utilisée avec la propriété `EMS.JMSReplyTo`.|  
|TibcoEMS.ReplyTo|chaîne|Une destination à laquelle une réponse à un message doit être envoyée. Le format est identique à `EMS.JMSDestination` et à la configuration du port.|  
|TibcoEMS.Type|chaîne|Ne décrit pas le type de message (text, byte, string, etc.).<br /><br /> Certains fournisseurs JMS utilisent un référentiel de messages destiné à stocker les définitions de types de messages. Des programmes clients peuvent stocker une valeur dans ce champ pour référencer une définition dans le référentiel. EMS prend en charge cet en-tête mais ne l'utilise pas.<br /><br /> La spécification JMS ne définit pas de référentiel de définitions de messages standard ni ne définit une stratégie d'affectation de noms pour les définitions de types de messages.<br /><br /> Certains fournisseurs exigent des définitions de types de messages pour chaque message de l'application. Pour assurer la compatibilité avec de tels fournisseurs, des programmes clients peuvent définir cet en-tête même si l'application cliente ne l'utilise pas.<br /><br /> Pour garantir la portabilité, les clients peuvent définir cet en-tête avec des valeurs symboliques (à la place de littéraux) et les configurer pour correspondre au référentiel du fournisseur.|  
  
## <a name="properties"></a>Propriétés  
 L'intégrateur peut définir un ensemble de propriétés à promouvoir dans le contexte de message BizTalk Server, après l'ajout des propriétés dans la partie Propriétés du message JMS. L'intégrateur s'en charge en cas de définition du type de la propriété lors de la création du schéma. Si cette valeur de propriété est utilisée dans un sélecteur de message, certaines opérations sont valides en fonction du type de propriété. Par exemple, si un sélecteur de message **myMessageProperty > 5** est utilisé, la propriété doit être définie comme une valeur entière, et l’adaptateur place la valeur dans le message en tant que valeur entière. Pour les propriétés à promouvoir, les noms de propriété doivent commencer par EMSX. Elles ne doivent pas avoir le même nom que les propriétés prédéfinies.  
  
 L'adaptateur BizTalk pour TIBCO Enterprise Message Service fournit un schéma et un assembly qui déclarent les propriétés spécifiques à EMS et JMS pouvant apparaître dans cette section. Ils peuvent être augmentés pour inclure les omissions. Toutes les propriétés EMSX référencées dans le contexte de message sont placées dans la section Propriétés du message EMS. Pour plus d'informations, consultez le Guide de l'utilisateur TIBCO EMS.  
  
## <a name="body"></a>Corps  
 EMS prend en charge tous les messages énumérés dans la spécification JMS : texte, octet, flux, mappage et objet. L'adaptateur BizTalk pour TIBCO EMS n'est compatible qu'avec le type de message texte.  
  
 JMS ne requiert pas que les messages de type texte contiennent des corps au format XML. L’adaptateur ne traite pas le corps du message ; Il est fourni à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] comme reçu.  Par conséquent, les messages envoyés à BizTalk par l’adaptateur ne sont pas toujours analysés comme des données XML.  
  
## <a name="persistent-messages"></a>Messages persistants  
 Les messages peuvent être conservés sur le serveur EMS pour garantir une livraison unique à un abonné. Cependant, cela peut avoir un impact considérable sur les performances de l'adaptateur. Lorsque vous envoyez des messages, EMS stocke le message dans un stockage local avant d'accuser réception du message pour l'adaptateur. Vous pouvez définir cette propriété par message dans l'orchestration ou pour tous les messages traités par le port.  
  
 Du point de vue de la réception, l'adaptateur peut manquer des messages s'il n'est pas abonné à la rubrique. Les messages publiés dans les rubriques alors qu'il n'y a aucun abonnement ne sont pas conservés par EMS. L'adaptateur a besoin d'un mécanisme pour recevoir des publications de messages alors qu'il n'est actuellement pas abonné. Cependant, à l'image des messages persistants, cela a un impact considérable sur les performances EMS et n'est pas toujours nécessaire.  
  
> [!NOTE]
>  Il existe un mécanisme de réception du point de vue d'EMS mais il n'est pas implémenté, ni réellement souhaité. Le seul problème avec la rubrique, c'est que les files d'attente ne sont pas affectées. Une rubrique est généralement utilisée pour des données correspondant à un moment précis, comme les cotations boursières, par exemple. Si le prix d'une action manque, vous savez qu'il sera republié plus tard.  
  
 Pour ces raisons, la configuration du port vous permet d'activer ou de désactiver la persistance des messages sur le serveur EMS.  
  
## <a name="message-acknowledgement"></a>Accusé de réception du message  
 L'adaptateur BizTalk pour TIBCO Enterprise Message Service accuse toujours réception d'un message lorsque ce message a été correctement distribué à BizTalk Server. Cela signifie que des messages sans accusé de réception sont renvoyés d'EMS à l'adaptateur. L'adaptateur ne peut pas contrôler le nombre de renvois du message par EMS car cela relève de la configuration de la destination elle-même. Toutefois, l'adaptateur peut contrôler si le message est envoyé ou non à la MessageBox. Le serveur EMS contrôle le nombre maximal de fois qu'un message ayant échoué est envoyé à une file d'attente.  
  
 Pour les messages livrés de nouveau, le serveur EMS définit la propriété `JMSRedelivered` sur True et incrémente `JMSXDeliveryCount`. Les deux valeurs de propriété sont disponibles pour l'orchestration. Vous ne pouvez pas déplacer un message vers la file d'attente EMS des messages non livrés sans le livrer ici. Cela modifierait les propriétés du message.  
  
 Lorsqu'un message atteint son nombre de nouvelles livraisons maximal configuré, le serveur EMS détermine si le message doit être supprimé ou placé dans la file d'attente $sys.undelivered. Le serveur EMS prend la décision en fonction de la propriété `JMS_TIBCO_PRESERVE_UNDELIVERED` : si elle est définie sur True, le message va dans la file d'attente des messages non livrés ou il est supprimé. Cette propriété peut être définie dans l'orchestration avant l'envoi du message. Après la livraison, la propriété de message ne peut pas être modifiée. En cas de réussite, les messages envoyés à EMS sont confirmés à BizTalk Server. En cas d'échec d'envoi à EMS, ils sont interrompus et marqués comme autorisant une nouvelle tentative.  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md)