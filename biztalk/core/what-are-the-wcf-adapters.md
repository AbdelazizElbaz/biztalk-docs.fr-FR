---
title: Que sont les adaptateurs WCF ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18ca8535-3386-4018-8b5b-d32bdb9ebf70
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41c942c7c2ef870b2a61c519e79fb8a124059f03
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="what-are-the-wcf-adapters"></a>Que sont les adaptateurs WCF ?
Il existe deux adaptateurs WCF (Windows Communication Foundation) : un adaptateur de réception et un adaptateur d'envoi. Vous utilisez l'adaptateur de réception WCF pour recevoir des demandes de service WCF. L'adaptateur de réception WCF reçoit une demande, crée un objet de message BizTalk et promeut les propriétés associées vers le contexte du message. Vous utilisez l'adaptateur d'envoi WCF pour appeler un service WCF. L'adaptateur d'envoi WCF appelle les services WCF via les contrats sans type.  
  
> [!NOTE]
>  Les adaptateurs WCF ne prennent pas en charge l'utilisation de services Web de type RPC (appel de procédure distante) car les parties de message dans des services Web RPC se rapportent aux types de message plutôt qu'aux éléments de message, alors que les adaptateurs WCF utilisent les éléments pour les parties de message. Nous vous recommandons d'ajouter les services Web RPC à l'aide de l'Assistant Ajouter une référence Web afin d'utiliser les services Web dans des projets BizTalk.  
  
## <a name="web-services-standards-support"></a>Prise en charge des normes de services Web  
 Les adaptateurs WCF assurent la prise en charge des normes WS-*, telles que WS-Addressing, WS-Security et WS-AtomicTransaction. La norme WS-ReliableMessaging n'est pas prise en charge dans cette version des adaptateurs WCF. Pour obtenir la liste de spécifications prises en charge par WCF, consultez [ http://go.microsoft.com/fwlink/?LinkId=88314 ](http://go.microsoft.com/fwlink/?LinkId=88314).  
  
### <a name="ws-addressing"></a>WS-Addressing  
 Les adaptateurs WCF s'appuient sur la prise en charge de la norme WS-Addressing qui est assurée par WCF. Les fonctionnalités suivantes sont disponibles dans les adaptateurs WCF :  
  
-   Configuration de l'adresse du point de terminaison du port d'envoi obtenue au cours de la demande d'échange de métadonnées.  
  
-   Configuration des en-têtes d'adressage pour l'adresse du point de terminaison du port d'envoi.  
  
-   Configuration des en-têtes d'adressage pour le point de terminaison exposé dans l'emplacement de réception BizTalk.  
  
### <a name="ws-security"></a>WS-Security  
 Les adaptateurs WCF s'appuient sur la prise en charge de normes de sécurité qui est assurée par WCF. Les normes suivantes sont prises en charge dans les adaptateurs WCF :  
  
-   Web Services Security: SOAP Message Security (WS-Security) 1.0 et 1.1  
  
-   Web Services Secure Conversation Language (WS-SecureConversation)  
  
-   Web Services Trust Language (WS-Trust)  
  
-   Web Services Security X.509 Certificate Token Profile  
  
-   Web Services Security Username Token Profile 1.0  
  
-   Web Services Security Kerberos Token Profile 1.0  
  
#### <a name="service-authentication-types"></a>Types d'authentification de services  
 Les types d'authentification de services WCF suivants sont pris en charge :  
  
-   Aucun  
  
-   Windows  
  
-   Certificat  
  
#### <a name="client-authentication-types"></a>Types d'authentification de clients  
 Les types d'authentification de clients WCF suivants sont pris en charge :  
  
-   Anonyme  
  
-   UserName  
  
-   Windows  
  
-   Certificat  
  
#### <a name="security-modes"></a>Modes de sécurité  
 Les modes de sécurité suivants sont pris en charge :  
  
-   Transport  
  
-   Boîte de  
  
-   Mixte (sécurité de niveau transport et authentification au niveau du message)  
  
### <a name="ws-atomictransaction"></a>WS-AtomicTransaction  
 Les adaptateurs WCF-WsHttp, WCF-NetTcp et WCF-NetMsmq prennent en charge le protocole WS-AtomicTransaction. Cette prise en charge permet les scénarios suivants :  
  
-   Envoi transactionnel de messages à la base de données MessageBox.  
  
-   Transmission transactionnelle de messages à partir de la base de données MessageBox vers une destination transactionnelle.  
  
> [!NOTE]
>  L'étendue transactionnelle est limitée par la MessageBox. Par exemple, une orchestration BizTalk ne peut pas participer à la transaction d'un client. De même, un point de terminaison de destination ne peut pas participer à une transaction initiée par une orchestration BizTalk.  
  
#### <a name="transactional-submission"></a>Envoi transactionnel  
 Pour les adaptateurs WCF-WsHttp et WCF-NetTcp, envoi transactionnel à BizTalk Server est activée en sélectionnant le **activer les transactions** case à cocher dans la boîte de dialogue Propriétés du transport réception emplacement. Pour l’adaptateur WCF-NetMsmq, le **transactionnel** case à cocher est activée par défaut. Si les files d'attente de messages desquelles vous retirez des messages ne sont pas marquées comme transactionnelles, vous devez désactiver cette case à cocher, sinon vous recevrez un message d'erreur.  
  
 Si la fonctionnalité de transaction est activée, les messages sont envoyés à la base de données MessageBox à l'aide de transactions de clients. Si un client tente d'envoyer des messages en dehors de l'étendue transactionnelle, l'adaptateur renvoie une exception au client. Toutefois, aucun message n'est interrompu. Si la fonctionnalité de transaction est désactivée, les messages sont envoyés à la base de données MessageBox sans l'aide de transactions de clients. Si un client tente d'envoyer des messages dans l'étendue transactionnelle, l'adaptateur renvoie une exception au client et aucun message n'est interrompu.  
  
#### <a name="transactions-and-receive-location-type"></a>Transactions et type d'emplacement de réception  
 L'envoi transactionnel n'est disponible que pour les emplacements de réception unidirectionnels. Si un client tente d'envoyer des messages dans une étendue transactionnelle pour un emplacement de réception bidirectionnel, une exception est renvoyée au client et aucun message n'est interrompu.  
  
#### <a name="transactional-transmission"></a>Transmission transactionnelle  
 Pour les adaptateurs WCF-WsHttp et WCF-NetTcp, la transmission transactionnelle à BizTalk Server est activée en sélectionnant le **activer les transactions** case à cocher dans la boîte de dialogue Propriétés du transport envoi port. Pour l’adaptateur WCF-NetMsmq, le **transactionnel** case à cocher est activée par défaut. Si les files d'attente de messages auxquelles vous envoyez des messages ne sont pas marquées comme transactionnelles, vous devez désactiver cette case à cocher, sinon vous recevrez un message d'erreur.  
  
 Si la fonctionnalité de transaction est activée, les messages sont transmis et supprimés de la base de données MessageBox à l'aide de transactions. Si le service de destination a effectué un travail après la réception du message et que le message n'est pas supprimé de la MessageBox, alors la transaction est abandonnée et tout le travail de transaction effectué sur le service est annulé. Si la fonctionnalité de transaction est désactivée, les messages sont transmis et supprimés de la base de données MessageBox sans l'aide de transactions.  
  
## <a name="single-sign-on-support"></a>Prise en charge de l'authentification unique  
 Vous pouvez emprunter une identité et acquérir le ticket d'authentification unique de l'entreprise pour utiliser l'authentification unique avec des adaptateurs WCF. Pour plus d’informations sur l’utilisation de l’authentification unique avec les adaptateurs WCF, consultez [unique authentification prise en charge pour les adaptateurs WCF](../core/single-sign-on-support-for-the-wcf-adapters.md).  
  
 Le tableau suivant récapitule les scénarios qui ne sont pas pris en charge lors de l'utilisation de la prise en charge de l'authentification unique avec les adaptateurs de réception WCF.  
  
|Mode de sécurité|Informations d'identification|  
|-------------------|----------------|  
|Aucun|Aucun|  
|Transport|Aucun|  
|Boîte de|Aucun|  
|TransportWithMessageCredentials|Aucun|  
|TransportCredentialOnly|Aucun|  
  
## <a name="wcf-extensibility"></a>Extensibilité WCF  
 Vous pouvez étendre la fonctionnalité de WCF en développant les extensions suivantes et en les utilisant avec les adaptateurs WCF-Custom et WCF-CustomIsolated :  
  
-   Liaisons personnalisées  
  
-   Éléments de liaison personnalisés  
  
### <a name="custom-bindings"></a>Liaisons personnalisées  
 Les liaisons personnalisées sont développées en empaquetant des éléments de liaison individuels dans un conteneur qui expose un sous-ensemble de propriétés de configuration pour un scénario d'utilisation particulier. Vous devez enregistrer l'extension de liaison en installant l'assembly dans le Global Assembly Cache (GAC), puis ajouter l'élément d'extension au fichier de configuration de l'ordinateur. Pour utiliser les liaisons personnalisées, vous devez configurer la liaison sur chaque serveur du groupe BizTalk. Une fois la liaison installée, elle est visible pour les adaptateurs WCF-Custom et WCF-CustomIsolated. Les adaptateurs WCF-Custom et WCF-CustomIsolated obtiennent les propriétés de configuration de la liaison à l'aide de la réflexion sur les éléments de configuration de la liaison.  
  
### <a name="custom-binding-elements"></a>Éléments de liaison personnalisés  
 Les éléments de liaison personnalisés sont développés en ajoutant ou en modifiant certains composants du canal de transport. Par exemple, un composant de décompression personnalisé est empaqueté en tant qu'élément de liaison ou un transport UDP est représenté en tant qu'élément de liaison. Ces éléments de liaison peuvent être utilisés dans les adaptateurs WCF. Vous pouvez définir une pile de canaux qui utilise l'élément de liaison personnalisé en combinaison avec d'autres éléments de liaison fournis ou personnalisés. Vous devez enregistrer l'extension d'élément de liaison en installant l'assembly dans le Global Assembly Cache (GAC), puis ajouter l'élément d'extension au fichier de configuration de l'ordinateur. Pour utiliser les liaisons personnalisées, vous devez configurer la liaison sur chaque serveur du groupe BizTalk. Pour utiliser les éléments de liaison personnalisée, vous pouvez sélectionner le **CustomBinding** type de liaison et ensuite ajouter, modifier ou réorganiser les éléments de liaison dans l’ordre souhaité.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Adaptateur de réception WCF](../core/wcf-receive-adapter.md)  
  
-   [Adaptateur d’envoi WCF](../core/wcf-send-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
-  [Adaptateurs WCF](../core/wcf-adapters.md)   
-  **Référence de contrat de Service les adaptateurs WCF** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]