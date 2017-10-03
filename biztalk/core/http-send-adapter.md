---
title: "Adaptateur d’envoi HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e69308b4-421f-4d7c-b9bb-ee086df03272
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce8bfdfd380fac422f79ba175ae075a94f313dec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-send-adapter"></a>Adaptateur d’envoi HTTP
L'adaptateur d'envoi HTTP obtient des messages de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et les envoie à une URL de destination via une requête HTTP POST. L'adaptateur d'envoi HTTP obtient le contenu du message du corps de l'objet de message BizTalk. L'adaptateur d'envoi HTTP ignore toutes les autres parties de l'objet de message BizTalk.  
  
 Une fois que l'adaptateur a envoyé le message à une URL de destination et que le moteur de messagerie BizTalk a reçu le code d'état de réussite HTTP, l'adaptateur d'envoi HTTP supprime le message de la base de données MessageBox.  
  
 La redirection des messages HTTP est prise en charge et peut être configurée sur le port d'envoi.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] héberge l'adaptateur d'envoi HTTP comme une application BizTalk native. Il prend en charge l'envoi unidirectionnel de messages ainsi qu'une transmission de type sollicitation-réponse. L'emplacement d'envoi de l'adaptateur d'envoi HTTP est une URL distincte que vous configurez par le biais du port d'envoi. Cette URL unique peut inclure des chaînes de requête ajoutées à l'URL de base.  
  
## <a name="batching-support-for-the-http-send-adapter"></a>Prise en charge du traitement par lot pour l'adaptateur d'envoi HTTP  
 L'adaptateur d'envoi HTTP ne prend pas en charge les opérations de traitement par lot.  
  
## <a name="chunked-encoding-support-for-the-http-send-adapter"></a>Prise en charge du codage mémorisé en bloc pour l'adaptateur d'envoi HTTP  
 Si le **activer le codage segmenté** option de configuration est activée, puis l’adaptateur d’envoi HTTP envoie des messages de demande à l’aide du codage mémorisé en bloc si la taille de la demande dépasse 8 Ko. Si le serveur proxy HTTP est utilisé, l'adaptateur d'envoi HTTP n'utilise pas le codage mémorisé en bloc et organise toujours les données avant leur envoi. Le **activer le codage segmenté** option de configuration est activée par défaut.  
  
 Lorsque l'adaptateur d'envoi reçoit un message de réponse, il peut accepter les messages à corps codé mémorisé en bloc.  
  
## <a name="client-authentication-for-the-http-send-adapter"></a>Authentification du client pour l'adaptateur d'envoi HTTP  
 L'adaptateur d'envoi HTTP s'authentifie auprès du serveur de destination à l'aide de l'un des types d'authentification suivants :  
  
-   **Anonyme.** L'adaptateur HTTP n'envoie pas d'informations d'identification lors de la connexion au serveur de destination. Si le serveur de destination autorise l'authentification anonyme, les informations d'identification du compte anonyme configuré sur le serveur de destination sont utilisées.  
  
-   **De base.** L'adaptateur HTTP envoie le nom d'utilisateur et le mot de passe via une connexion HTTP, en texte clair.  
  
-   **Digest.** L'adaptateur HTTP envoie des mots de passe dans un format chiffré via la connexion HTTP.  
  
-   **Kerberos.** Ni le nom d'utilisateur ni le mot de passe n'est envoyé via une connexion HTTP. L'adaptateur HTTP utilise les informations d'identification du processus sous lequel l'adaptateur d'envoi HTTP s'exécute pour ce type d'authentification.  
  
 En outre, l'adaptateur d'envoi HTTP peut fournir un certificat SSL (Secure Sockets Layer) au serveur Web si le serveur le demande ou l'accepte.  
  
## <a name="client-certificates-for-the-http-send-adapter"></a>Certificats clients pour l'adaptateur d'envoi HTTP  
 L'adaptateur d'envoi HTTP peut établir une connexion sécurisée avec les serveurs qui acceptent ou demandent des certificats clients. Si un certificat client est spécifié, l'adaptateur d'envoi HTTP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients. Si le certificat client n'est pas spécifié et que le serveur de destination demande des certificats clients, l'adaptateur d'envoi HTTP ne peut pas envoyer le message et suit la logique standard pour les nouvelles tentatives.  
  
 L'adaptateur d'envoi HTTP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté. Le certificat est spécifié par son empreinte. Si l'adaptateur d'envoi HTTP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.  
  
## <a name="single-sign-on-support-for-the-http-adapter"></a>Prise en charge de l'authentification unique pour l'adaptateur HTTP  
 Vous pouvez configurer l'utilisation de l'authentification unique de l'entreprise (SSO) pour un emplacement de réception ou un port d'envoi HTTP à l'aide de la console Administration de BizTalk. Cette rubrique décrit le fonctionnement de l'authentification unique avec l'adaptateur HTTP.  
  
 **Emplacement de réception unique authentification prise en charge pour le protocole HTTP**  
  
 Lorsqu'une requête HTTP est reçue par Microsoft Internet Information Services (IIS) à partir d'un client Web, IIS authentifie l'utilisateur. L'extension ISAPI (Internet Server Application Programming Interface) se fait passer pour l'utilisateur Microsoft Windows, puis appelle le magasin d'informations d'identification SSO pour obtenir un ticket chiffré. Ce ticket est stocké en tant que le **SSOTicket** propriété dans le contexte du message.  
  
 Dans le scénario de transfert, le moteur de messagerie BizTalk dirige le message vers la base de données MessageBox. Lorsque l’adaptateur reçoit le message à partir de la base de données MessageBox, l’adaptateur HTTP appelle la **méthode ISSOTicket.RedeemTicket** avec le ticket chiffré, ainsi que le nom de l’application pour récupérer les informations d’identification du principal à partir de la Magasin de l’authentification unique. L'adaptateur HTTP utilise alors les informations d'identification externes pour se connecter au système principal et traiter la demande. Pour plus d’informations sur les applications associées, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).  
  
 Dans le cas où une orchestration appelle l'adaptateur, le moteur de messagerie BizTalk envoie ce message à la base de données MessageBox. L’orchestration doit s’assurer à la fois le **SSOTicket** propriété de contexte et le **Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID** sont de la propriété de contexte du message qui contient le ticket conservée. Lorsque l’adaptateur reçoit ce message à partir de la base de données MessageBox, il appelle **RedeemTicket** avec le ticket chiffré pour extraire les informations d’identification du principal à partir du magasin SSO. L'utilisateur concevant la planification doit copier spécifiquement cette propriété dans le message.  
  
 **Seule l’authentification prise en charge pour les adaptateurs d’envoi HTTP**  
  
 Si l’authentification unique est activée, lorsqu’un port d’envoi HTTP reçoit un message avec le **Secure** propriété, il appelle le serveur SSO pour valider et échanger le ticket pour une application associée. L'application d'administration, les administrateurs d'applications associées ou les administrateurs SSO de l'application associée peuvent appeler SSO pour échanger un ticket. SSO déchiffre alors le ticket et obtient les informations d'identification principales. Les scénarios de transfert et d'orchestration sont les mêmes que pour le port d'envoi HTTP.  
  
 Par défaut, SSO est désactivé pour le port d'envoi HTTP. Pour plus d’informations sur l’activation de l’authentification unique pour le port d’envoi HTTP, consultez [configuration d’un Port d’envoi HTTP](../core/configuring-an-http-send-port.md).  
  
> [!NOTE]
>  Vous pouvez utiliser l'authentification unique seulement avec l'authentification De base et Digest.  
  
 Pour implémenter correctement la prise en charge de l'authentification unique pour l'adaptateur d'envoi et de réception HTTP, les conditions suivantes doivent être remplies :  
  
-   Le même compte d'utilisateur doit être spécifié dans les endroits suivants :  
  
    -   L'identité de pool d'applications (IIS 7.0) ou l'identité de l'application COM+ hôte pour le répertoire virtuel IIS qui est surveillé par l'adaptateur de réception HTTP. Pour plus d’informations sur la configuration d’IIS pour HTTP des emplacements de réception, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
    -   Les informations d'identification utilisées pour l'instance de l'hôte isolé dans laquelle l'adaptateur HTTP est exécuté. Pour plus d’informations sur la façon de configurer les informations d’identification d’ouverture de session pour une instance d’hôte, consultez [comment modifier les propriétés d’Instance hôte](../core/how-to-modify-host-instance-properties.md).  
  
-   L'hôte isolé que l'adaptateur HTTP utilise doit être configuré comme Approuvé par authentification. Pour plus d’informations sur la façon de configurer un hôte comme approuvé par authentification, consultez [comment modifier les propriétés de l’hôte](../core/how-to-modify-host-properties.md).  
  
## <a name="negative-acknowledgment-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapter"></a>Messages d’accusé de réception négatif (NACK) générés pour les Transmissions échouées par l’adaptateur HTTP ou SOAP  
 Lorsqu’un message est transmis avec succès, le moteur de messagerie BizTalk publie un message d’accusé de réception associé (ACK) vers la MessageBox si les notifications de remise sont activées. De même, lorsqu'un message est interrompu par le moteur de messagerie BizTalk ou qu'une orchestration est interrompue par le moteur d'orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publie un message d'accusé de réception négatif (NACK) associé dans la MessageBox. Le message d'accusé de réception négatif contient des propriétés de contexte et un corps de message qui consiste en une erreur SOAP. Si le message d'accusé de réception négatif est généré en raison de l'échec d'une transmission à partir de l'adaptateur HTTP ou SOAP, l'erreur SOAP contient l'élément En-têtes et l'élément Corps de la réponse du serveur Web de destination. Voici un exemple d'erreur SOAP dans un accusé de réception négatif généré en raison de l'échec d'une transmission HTTP :  
  
```  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
   <SOAP:Body>  
      <SOAP:Fault>  
         <faultcode>Microsoft BizTalk Server Negative Acknowledgment</faultcode>   
         <faultstring>An error occurred while processing the message, refer to the details section for more information</faultstring>   
         <faultactor>http://localhost/receivestandard.asp</faultactor>   
         <detail>  
            <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
            <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
            <ErrorCode>0x80131600</ErrorCode>  
            <ErrorCategory>0</ErrorCategory>  
            <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
            <ErrorDetail>  
            <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
               <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
               <Body>We could not locate the page you requested. Please check the URL.</Body>  
            </HttpErrorDetail>  
            </ErrorDetail>  
            </ns0:NACK>  
         </detail>  
      </SOAP:Fault>  
   </SOAP:Body>  
</SOAP:Envelope>  
```  
  
> [!NOTE]
>  L'élément En-têtes et l'élément Corps sont limités à 48 Ko. L'élément En-têtes est arrondi à la paire en-tête-valeur complète la plus proche sans dépasser la limite. L'élément Corps est tronqué à 48 Ko.  
  
> [!NOTE]
>  Les messages NACK et ACK sont ignorés si aucun abonnement ne correspond pour eux. Ils ne sont pas interrompus par le moteur de messagerie BizTalk.  
  
 Pour vous abonner à un accusé de réception négatif, vous pouvez effectuer l'une des opérations suivantes :  
  
-   Créer un port d'envoi avec un filtre pour la propriété de contexte de message appropriée. Consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] pour obtenir la liste des propriétés de contexte de message système, y compris ceux liés à accusé de réception de message.  
  
-   Envoyer à partir d’un port d’orchestration marqué avec **accusé de réception = transmis**. Si un port d’orchestration est marqué avec **accusé de réception = transmis**, l’orchestration attend jusqu'à ce qu’il reçoit un accusé de réception ou un accusé de réception négatif pour le message a été transmis. Si un accusé de réception négatif est généré, il est routé vers l'orchestration, qui génère une exception DeliveryFailureException. DeliveryFailureException est désérialisée à partir de l'erreur SOAP contenue dans le corps du message d'accusé de réception négatif. Pour extraire la chaîne de message d'exception de l'erreur SOAP renvoyée à l'orchestration, convertissez DeliveryFailureException en SoapException, puis accédez à InnerXml depuis la section relative aux détails SOAP. L'exemple de code suivant illustre comment procéder :  
  
    ```  
    // Cast the DeliveryFailureException to a SoapException…  
    System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
    System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
    //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
    //object type created in an Exception handler  
  
    ```  
  
     L'exemple de code précédent renvoie un fragment XML semblable à ce qui suit :  
  
    ```  
    <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
    <NAckID>{4E646707-03AA-4493-95C7-A64B09E2987D}</NAckID>  
    <ErrorCode>0x80131600</ErrorCode>  
    <ErrorCategory>0</ErrorCategory>  
    <ErrorDescription>The remote server returned an error: (404) Not Found.</ErrorDescription>  
    <ErrorDetail>  
    <HttpErrorDetail xmlns="http://schema.microsoft.com/BizTalk/2006/HttpErrorDetails.xsd">  
       <Headers>Server: Microsoft-IIS/5.1 Date: Wed, 21 Apr 2005 00:27:47 GMT X-Powered-By: ASP.NET Connection: close Content-Type: text/html Content-Length: 67 </Headers>  
       <Body>We could not locate the page you requested. Please check the URL.</Body>  
    </HttpErrorDetail>  
    </ErrorDetail>  
    </ns0:NACK>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Adaptateur HTTP](../core/http-adapter.md)  
**Objets COM de l’authentification unique**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]