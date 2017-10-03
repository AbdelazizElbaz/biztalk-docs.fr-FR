---
title: "Adaptateur d’envoi SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d65218d-516b-4e45-a824-272ef6ef298c
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f59babb164458f7a5d072809d038fb253482553d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-send-adapter"></a>Adaptateur d’envoi SOAP
Vous utilisez l'adaptateur d'envoi SOAP pour appeler un service Web. L'adaptateur d'envoi SOAP lit le contexte du message sur l'objet de message BizTalk afin d'obtenir le nom du proxy et appelle le proxy du service Web externe associé.  
  
## <a name="client-authentication-for-the-soap-send-adapter"></a>Authentification du client pour l'adaptateur d'envoi SOAP  
 L'adaptateur d'envoi SOAP s'authentifie auprès du serveur de destination à l'aide de l'un des types d'authentifications suivants :  
  
-   **Anonyme.** Paramètre par défaut.  
  
-   **De base.** La connexion SOAP envoie le nom d'utilisateur et le mot de passe en texte clair.  
  
-   **Digest.** La connexion SOAP envoie le nom d'utilisateur et le mot de passe dans un format chiffré.  
  
-   **Kerberos ou NTLM.** Ni le nom d'utilisateur ni le mot de passe n'est envoyé via une connexion SOAP. L'adaptateur SOAP utilise toujours les informations d'identification du processus sous lequel l'adaptateur d'envoi SOAP s'exécute pour ce type d'authentification.  
  
 En outre, l'adaptateur d'envoi SOAP peut fournir un certificat SSL (Secure Sockets Layer) au serveur Web si le serveur le demande ou l'accepte.  
  
 Si vous avez activé Enterprise Single Sign-On (SSO), lorsque l’adaptateur d’envoi SOAP reçoit un message avec la demande à la **SSOTicket** propriété, l’adaptateur se connecte à un serveur SSO pour valider et échanger le ticket. Une fois que l'adaptateur SOAP a validé le ticket, celui-ci est déchiffré et les informations d'identification pour le système associé sont récupérées dans le magasin d'informations d'identification. L'adaptateur SOAP utilise ensuite ces informations d'identification pour se connecter au système associé et la demande SOAP est traitée.  
  
## <a name="client-certificates-for-the-soap-send-adapter"></a>Certificats clients pour l'adaptateur d'envoi SOAP  
 L'adaptateur d'envoi SOAP peut établir une connexion sécurisée avec les serveurs qui acceptent ou demandent des certificats clients. Si un certificat client est spécifié, l'adaptateur d'envoi SOAP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients. Si le certificat client n'est pas spécifié et que le serveur de destination demande des certificats clients, l'adaptateur d'envoi SOAP ne peut pas envoyer le message et suit la logique standard pour les nouvelles tentatives.  
  
 L'adaptateur d'envoi SOAP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté. L'adaptateur SOAP spécifie le certificat par son empreinte. Si l'adaptateur d'envoi SOAP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.  
  
## <a name="negative-acknowledgement-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapters"></a>Messages d'accusé de réception négatif (NACK) générés pour les transmissions échouées par l'adaptateur HTTP ou SOAP  
 Lorsqu'un message est transmis avec succès, le moteur de messagerie BizTalk publie un message d'accusé de réception (ACK) associé dans la MessageBox si les accusés de réception sont activés. De même, lorsqu’un message est interrompu par le moteur de messagerie BizTalk ou une orchestration a été suspendue par le moteur d’orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publie un message d’accusé de réception négatif (NACK) associé à la base de données MessageBox. Le message d’accusé de réception négatif contient des propriétés de contexte et une partie du corps de message composé d’une erreur SOAP. Si le message d’accusé de réception négatif est généré en raison de l’échec d’une transmission des adaptateurs HTTP ou SOAP, l’erreur SOAP contient le **en-têtes** élément et la **corps** élément de la réponse à partir du site Web de destination serveur. Voici un exemple d'erreur SOAP dans un accusé de réception négatif généré en raison de l'échec d'une transmission SOAP :  
  
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
>  Le **en-têtes** élément et la **corps** élément sont limités à 48 Ko. Le **en-têtes** élément est arrondi à la paire de valeur d’en-tête complet le plus proche sans dépasser la limite. Le **corps** élément est tronqué à 48 Ko.  
  
> [!NOTE]
>  Les messages NACK et ACK sont ignorés si aucun abonnement ne correspond pour eux. Ils ne sont pas interrompus par le moteur de messagerie.  
  
 Pour vous abonner à un accusé de réception négatif, vous pouvez effectuer l'une des opérations suivantes :  
  
1.  Créer un port d'envoi avec un filtre pour la propriété de contexte de message appropriée. Consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] pour obtenir la liste des propriétés de contexte de message système, y compris ceux liés à accusé de réception de message.  
  
2.  Envoyer à partir d’un port d’orchestration marqué avec **accusé de réception = transmis**. Si un port d’orchestration est marqué avec **accusé de réception = transmis**, l’orchestration attend jusqu'à ce qu’il reçoit un accusé de réception ou un accusé de réception négatif pour le message a été transmis. Si un accusé de réception négatif est généré, il est routé vers l'orchestration, qui génère une exception DeliveryFailureException. DeliveryFailureException est désérialisée à partir de l'erreur SOAP contenue dans le corps du message d'accusé de réception négatif. Pour extraire la chaîne de message d'exception de l'erreur SOAP renvoyée à l'orchestration, convertissez DeliveryFailureException en SoapException, puis accédez à InnerXml depuis la section relative aux détails SOAP. L'exemple de code suivant illustre comment procéder :  
  
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
 [Nouveautés de l’adaptateur SOAP ?](../core/what-is-the-soap-adapter.md)   
 [Recommandations de sécurité de l’adaptateur SOAP](../core/soap-adapter-security-recommendations.md)