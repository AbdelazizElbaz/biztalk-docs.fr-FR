---
title: "Considérations relatives à l’utilisation des Services WCF avec WCF des adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- best practices, WCF services
- WCF services, best practices
- consuming, best practices
- WCF services, consuming
ms.assetid: 8bbcfd99-3495-458d-bd7a-6d170a29dde2
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2bb1e512b8a13c3d91b87bbfc410c3d21f334fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-consuming-wcf-services-with-the-wcf-send-adapters"></a>Considérations relatives à l'utilisation de services WCF à l'aide des adaptateurs d'envoi WCF
Cette rubrique fournit des informations à prendre en compte lors de l'utilisation des services WCF à l'aide des adaptateurs WCF.  
  
## <a name="use-the-template----content-specified-by-template-option-when-sending-non-xml-content-as-solicit-messages"></a>Utilisation de l'option « Modèle -- contenu spécifié par le modèle » lors de l'envoi de contenu non-XML en tant que messages de sollicitation  
 Les adaptateurs WCF avec **corps--corps du message de réponse BizTalk** (la valeur par défaut) option n’autorisent pas l’envoi de message non-XML tels que des images bitmap et des données de caractères. Vous pouvez utiliser la **modèle--contenu spécifié par le modèle** option pour les adaptateurs WCF envoyer des messages non XML. Pour plus d’informations sur la façon d’utiliser le modèle, consultez [Considérations lors de la publication des Services WCF avec les adaptateurs de réception WCF](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md).  
  
## <a name="the-wcf-basichttp-and-wcf-wshttp-send-ports-always-ignore-the-proxy-if-the-service-address-begins-with-httplocalhost"></a>Les ports d'envoi WCF-BasicHttp et WCF-WSHttp ignorent toujours le proxy si l'adresse de service commence par http://localhost  
 Le WCF-BasicHttp et WCF-WSHttp ports d’envoi toujours ignorent le proxy si l’adresse de service commence par http://localhost si le proxy est configuré sur le **Proxy** onglet du port d’envoi ou le **Proxy** onglet du Gestionnaire d’envoi. Si vous souhaitez que les clients utilisent un proxy dans le cadre de la communication avec des services sur le même ordinateur, vous devez utiliser le nom de l'hôte (au lieu de « localhost »).  
  
## <a name="the-wcf-basichttp-and-wcf-wshttp-send-adapters-suspend-the-messages-if-the-proxy-setting-is-not-correctly-configured"></a>Les adaptateurs d'envoi WCF-BasicHttp et WCF-WSHttp suspendent les messages si le paramètre de proxy n'est pas correctement configuré  
 Vous pouvez spécifier le paramètre de proxy pour le WCF-BasicHttp et WCF-WSHttp les adaptateurs d’envoi le **Proxy** onglet du port d’envoi ou le **Proxy** onglet du Gestionnaire d’envoi. Si ce paramètre de proxy n'est pas correctement configuré, les adaptateurs WCF suspendent les messages et le message d'erreur « Il n’existait pas de point de terminaison à l’écoute pouvant accepter le message » est affiché dans le journal des événements.  
  
## <a name="setting-up-the-permissions-for-a-wcf-send-port-with-the-wcf-netmsmq-adapter"></a>Configuration des autorisations pour un port d'envoi WCF à l'aide de l'adaptateur WCF-NetMsmq  
 Lorsqu'un port d'envoi WCF utilisant l'adaptateur WCF-NetMsmq envoie un message à un service WCF publié à l'aide de NetMsmqBinding, il adresse le message à la file d'attente cible, qui est la file d'attente gérée par le gestionnaire de files d'attente du service. Le gestionnaire de files d'attente sur le client envoie le message à une file d'attente de transmission (ou sortante). La file d'attente de transmission est une file d'attente, située sur le gestionnaire de files d'attente côté client, qui stocke des messages pour les transmettre à la file d'attente cible.  
  
 Le gestionnaire de files d'attente du service accepte des messages adressés aux files d'attente cibles qu'il possède et stocke les messages. Ensuite, le service lance des demandes de lecture à partir de la file d'attente cible. Le gestionnaire de files d'attente livre alors les messages au service. C'est la raison pour laquelle le compte de service pour l'instance d'hôte BizTalk hébergeant le port d'envoi doit disposer des autorisations d'écriture à partir de la file d'attente de transmission.  
  
## <a name="use-an-empty-xpath-expression-to-receive-a-soap-message-with-character-data-in-the-content-of-the-soap-body-element"></a>Utilisation d'une expression XPath vide pour recevoir un message SOAP contenant des données de type caractère dans l'élément SOAP Body  
 Le port d'envoi WCF de type sollicitation-réponse peut recevoir un message WCF en tant que message de réponse. Pour créer un message BizTalk à partir d’un message de réponse entrante avec des données de caractères dans le contenu de SOAP **corps** élément, comme indiqué dans l’exemple suivant, vous devez laisser la **expression XPath** zone de texte vide sur le **Message** onglet dans la boîte de dialogue Propriétés du transport WCF adaptateur.  
  
```  
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope" xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      ...  
    </s:Header>  
    <s:Body>Contoso</s:Body>  
</s:Envelope>  
```  
  
 Si vous sélectionnez le **enveloppe** ou **corps** option, l’adaptateur ne crée pas le message BizTalk à partir du message entrant. Le message n'est pas interrompu car les messages échouant au cours du traitement de marshaling SOAP entrant ne sont pas interrompus. Pour plus d’informations sur l’utilisation de l’expression XPath sur le **Message** , consultez la rubrique [spécifiant le corps du Message pour les adaptateurs WCF](../core/specifying-the-message-body-for-the-wcf-adapters.md).  
  
> [!NOTE]
>  Vous pouvez utiliser l'outil TraceViewer (SvcTraceViewer.exe) du Kit de développement Windows SDK en configurant le fichier BTSNTSvc.exe.config. Pour plus d’informations sur le Kit de développement logiciel Windows, consultez « Nouveautés dans le Kit de développement logiciel Windows » à [http://go.microsoft.com/fwlink/?LinkId=75219](http://go.microsoft.com/fwlink/?LinkId=75219). Pour plus d’informations sur l’outil TraceViewer, consultez « TraceViewer Tool (SvcTraceViewer.exe) » à [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).  
  
## <a name="biztalk-server-does-not-use-multi-part-message-types-and-root-elements-describing-custom-soap-headers"></a>BizTalk Server n'utilise pas les types de messages à parties multiples et les éléments racines décrivant les en-têtes SOAP personnalisés  
 Si vous exécutez l'Assistant Consommation de service WCF BizTalk avec les métadonnées d'après lesquelles les en-têtes SOAP sont définis, l'Assistant génère les éléments racines dans les schémas générés pour représenter les en-têtes SOAP personnalisés. L'Assistant crée également des types de messages à parties multiples dans les orchestrations pour les en-têtes SOAP personnalisés. Serveur BizTalk Server : Toutefois, BizTalk Server n’utilise pas de types de message à parties multiples et les éléments racines pour gérer les en-têtes SOAP personnalisés.  
  
 Pour accéder aux en-têtes SOAP personnalisés, vous devez utiliser le **InboundHeaders** propriété. Pour plus d’informations sur la réception des en-têtes SOAP personnalisés, consultez [les en-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md). Pour utiliser des en-têtes SOAP personnalisés, vous devez utiliser le **OutboundCustomHeaders** propriété. Pour plus d’informations sur l’envoi des en-têtes SOAP personnalisés, consultez [les en-têtes SOAP avec les Services WCF consommé](../core/soap-headers-with-consumed-wcf-services.md).  
  
## <a name="create-separate-host-instances-for-send-ports-that-use-different-proxy-addresses-andor-proxy-credentials"></a>Création d'instances d'hôte distinctes pour les ports d'envoi utilisant différentes adresses proxy et/ou informations d'identification de proxy  
 Pour que les adaptateurs d'envoi WCF obtiennent des performances optimales, il est recommandé de créer des instances d'hôte distinctes pour les ports d'envoi qui utilisent différentes adresses proxy et/ou informations d'identification de proxy. Ceci permet d'éviter les conflits au niveau des paramètres de proxy.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier BTSNTSvc.exe.config](../core/btsntsvc-exe-config-file.md)