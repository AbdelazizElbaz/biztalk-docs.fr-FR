---
title: "Adaptateur de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9008833c-5a02-4fb4-a43e-09ca28a21eff
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9f2f309a129c66d11d019b28b8ffc2b51d68e93d
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2018
---
# <a name="http-receive-adapter"></a>Adaptateur de réception HTTP
L'emplacement de réception défini pour l'adaptateur de réception HTTP est une URL distincte configurée via la console Administration de BizTalk Server.  
  
 Vous pouvez configurer l'adaptateur de réception HTTP pour un envoi asynchrone ou synchrone à partir du client. Les envois asynchrones sont des envois unidirectionnels, tandis que les envois synchrones sont des envois bidirectionnels ou de requête-réponse.  
  
 La sécurité IIS est utilisée pour l'authentification et l'autorisation des demandes entrantes.  
  
## <a name="http-get-and-http-post-requests"></a>Requêtes HTTP GET et HTTP POST  
 L'adaptateur de réception HTTP peut recevoir des messages via une requête HTTP POST ou une requête HTTP GET.  
  
 Lorsqu'un adaptateur de réception HTTP reçoit des messages via une requête HTTP POST, la séquence suivante d'événements se produit :  
  
1.  L'URL configurée dans BizTalk Server reçoit un nouveau message à l'emplacement de réception.  
  
2.  L'adaptateur de réception crée un objet message BizTalk pour la transmission du message au serveur.  
  
3.  L'adaptateur de réception crée l'objet message BizTalk avec une seule partie, le corps.  
  
4.  Une fois le message lu et envoyé au serveur, l'adaptateur de réception HTTP renvoie un code HTTP 202 au client indiquant que la demande a été acceptée.  
  
     L'adaptateur de réception HTTP peut également envoyer un jeton de corrélation du message dans la réponse HTTP. Celui-ci représente le message dans BizTalk Server. Si l'emplacement de réception HTTP est situé dans un port de requête-réponse, l'adaptateur renvoie le code de réussite 200 avec le message de réponse.  
  
 Lorsqu'un adaptateur de réception HTTP traite les messages d'une requête HTTP GET, l'adaptateur de réception crée un objet message BizTalk et place la chaîne de requête décodée de la requête HTTP GET dans le corps du message BizTalk. L'adaptateur HTTP sélectionne la chaîne de requête placée dans le corps du message BizTalk à l'aide de l'algorithme suivant :  
  
-   Si l'adaptateur de réception HTTP reçoit une requête HTTP GET, il divise la chaîne d'URI entrante en deux parties en utilisant le point d'interrogation (?) comme délimiteur.  
  
-   La première partie de la chaîne d’URI, la partie avant le séparateur de point d’interrogation est copiée dans le **InboundTransportLocation** propriété dans le contexte du message. Le **InboundTransportLocation** propriété identifie de façon unique l’emplacement où BizTalk Server a reçu le message. Le moteur utilise cette propriété pour identifier l'emplacement de réception à exécuter pour le message.  
  
-   L'adaptateur HTTP extrait le reste de la chaîne d'URI (partie après le point d'interrogation de délimitation), le décode, puis le copie dans le corps du message BizTalk.  
  
-   Si une opération HTTP GET ou HTTP POST vide est reçue par l'adaptateur de réception HTTP, elle est rejetée.  
  
## <a name="http-receive-adapter-processing-of-a-get-request"></a>Traitement d'une demande GET par l'adaptateur de réception HTTP  
 Les exemples suivants illustrent le traitement effectué par l'adaptateur de réception HTTP sur les messages reçus via des requêtes HTTP GET. Ils supposent que l'adaptateur de réception HTTP est configuré avec les deux emplacements de réception suivants :  
  
```  
/vroot/BTSHTTPReceive.dll  
/vroot/BTSHTTPReceive.dll?LocationID=1  
```  
  
1.  Le client reçoit la requête HTTP GET suivante :  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1  
    ```  
  
     L'adaptateur de réception HTTP exécute l'action suivante :  
  
     Définir le **InboundTransportLocation** propriété du contexte de message égal à /vroot/BTSHTTPReceive.dll et la partie du corps d’objet du BizTalk Message sur LocationID = 1.  
  
2.  Le client reçoit la requête HTTP GET suivante :  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll?LocationID=1&MyParam=My%20Value  
    ```  
  
     L'adaptateur de réception HTTP exécute l'action suivante :  
  
     Définir le **InboundTransportLocation** propriété sur /vroot/BTSHTTPReceive.dll et le corps de l’objet BizTalk Message partie sur LocationID = 1 & MyParam = My Value.  
  
3.  Le client reçoit la requête HTTP GET suivante :  
  
    ```  
    http://servername/vroot/BTSHTTPReceive.dll  
    ```  
  
     Adaptateur de réception de l’action effectuée par le protocole HTTP est + comme suit :  
  
     Rejeter la demande en raison de la mise en forme incorrecte de la requête HTTP GET.  
  
## <a name="batching-support-for-the-http-receive-adapter"></a>Prise en charge du traitement par lot pour l'adaptateur de réception HTTP  
 L'adaptateur de réception HTTP envoie des messages au serveur par lots. La taille du lot utilisé pour envoyer les messages au serveur peut être configurée dans le gestionnaire de réception de l'adaptateur HTTP.  
  
## <a name="http-receive-adapter-support-for-suspending-failed-requests"></a>Prise en charge de l'adaptateur de réception HTTP pour la suspension des demandes ayant échoué  
 L’adaptateur de réception HTTP BizTalk Server dispose d’un paramètre de configuration, **suspendre les requêtes ayant échoué**pour contrôler ce qui se passe avec une requête HTTP en cas d’échec du traitement entrant en raison d’une erreur de pipeline de réception, une erreur de mappage, ou un Échec de routage. Il peut prendre deux valeurs :  
  
-   **La valeur est false.** Il s'agit du paramètre par défaut. L'adaptateur de réception HTTP ignore les messages dont le traitement entrant a échoué en raison d'un échec de pipeline de réception, d'une erreur de mappage ou d'un échec de routage. Un code d'état d'erreur 401 ou 500 est également envoyé au client. 
  
-   **True.** L'adaptateur de réception HTTP suspend les messages dont le traitement entrant a échoué en raison d'un échec de pipeline de réception, d'une erreur de mappage ou d'un échec de routage. Pour unidirectionnel ports de réception un **accepté** code d’état 202 est envoyé au client. Pour bidirectionnelle des ports de réception un **erreur** code d’état 500 est envoyé au client.  
  
## <a name="chunked-encoding-support-for-the-http-receive-adapter"></a>Prise en charge du codage mémorisé en bloc pour l'adaptateur de réception HTTP  
 L'adaptateur de réception HTTP accepte les requêtes HTTP avec les messages à corps codé mémorisé en bloc. L'adaptateur de réception utilise le codage mémorisé en bloc pour envoyer des messages de réponse lorsque la taille du corps est supérieure à 4 Ko. Le codage mémorisé en bloc peut être désactivé en définissant l’entrée de Registre DWORD décrite dans [des paramètres de réglage et de Configuration de l’adaptateur HTTP](../core/http-adapter-configuration-and-tuning-parameters.md)  
  
## <a name="client-certificates-for-the-http-receive-adapter"></a>Certificats clients pour l'adaptateur de réception HTTP  
 Lorsqu'une connexion sécurisée avec un certificat client est utilisée pour l'emplacement de réception HTTP, l'adaptateur de réception HTTP obtient l'empreinte de certificat client de Microsoft Internet Information Services (IIS) et ajoute celle-ci au contexte des messages reçus via HTTPS à cet emplacement. L'adaptateur de réception HTTP définit les propriétés système suivantes :  
  
```  
SourcePartyEvidenceQualifier = "Certificate"  
SourcePartyEvidence = <certificate thumbprint>  
```  
  
## <a name="status-codes-returned-by-the-http-receive-adapter"></a>Codes d'état renvoyés par l'adaptateur de réception HTTP  
 La liste suivante indique les codes d'état renvoyés par l'adaptateur de réception HTTP.  
  
-   **200 OK.** L'adaptateur a traité le message de demande et généré une réponse. Il renvoie ce code d'état dans la réponse HTTP à partir du port de requête-réponse HTTP.  
  
-   **202 message accepté.** L'adaptateur a envoyé le message au serveur ou une demande unidirectionnelle est suspendue. L'adaptateur renvoie ce code d'état dans la réponse HTTP à partir du port de réception HTTP unidirectionnel.  
  
-   **401 Accès refusé.** La requête HTTP est reçue sur un port de réception à authentification requise et le contrôle de sécurité pour ce message a échoué. Par exemple, le tiers n'a pas été résolu ou le message n'a pas été déchiffré.  
  
-   **Erreur de serveur interne 500.** Erreur générale dans le cadre du traitement de la requête HTTP. Le message n’est pas interrompu par BizTalk Server, sauf si le paramètre de configuration **suspendre les requêtes ayant échoué** a la valeur **True** pour un double port de réception.  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur HTTP](../core/http-adapter.md)