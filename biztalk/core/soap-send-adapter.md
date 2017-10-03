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
# <a name="soap-send-adapter"></a><span data-ttu-id="acfda-102">Adaptateur d’envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="acfda-102">SOAP Send Adapter</span></span>
<span data-ttu-id="acfda-103">Vous utilisez l'adaptateur d'envoi SOAP pour appeler un service Web.</span><span class="sxs-lookup"><span data-stu-id="acfda-103">You use the SOAP send adapter to call a Web service.</span></span> <span data-ttu-id="acfda-104">L'adaptateur d'envoi SOAP lit le contexte du message sur l'objet de message BizTalk afin d'obtenir le nom du proxy et appelle le proxy du service Web externe associé.</span><span class="sxs-lookup"><span data-stu-id="acfda-104">The SOAP send adapter reads the message context on the BizTalk Message object to get the proxy name and calls the associated external Web service proxy.</span></span>  
  
## <a name="client-authentication-for-the-soap-send-adapter"></a><span data-ttu-id="acfda-105">Authentification du client pour l'adaptateur d'envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="acfda-105">Client Authentication for the SOAP Send Adapter</span></span>  
 <span data-ttu-id="acfda-106">L'adaptateur d'envoi SOAP s'authentifie auprès du serveur de destination à l'aide de l'un des types d'authentifications suivants :</span><span class="sxs-lookup"><span data-stu-id="acfda-106">The SOAP send adapter authenticates with the destination server by using one of the following authentication types:</span></span>  
  
-   <span data-ttu-id="acfda-107">**Anonyme.**</span><span class="sxs-lookup"><span data-stu-id="acfda-107">**Anonymous.**</span></span> <span data-ttu-id="acfda-108">Paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="acfda-108">The default setting.</span></span>  
  
-   <span data-ttu-id="acfda-109">**De base.**</span><span class="sxs-lookup"><span data-stu-id="acfda-109">**Basic.**</span></span> <span data-ttu-id="acfda-110">La connexion SOAP envoie le nom d'utilisateur et le mot de passe en texte clair.</span><span class="sxs-lookup"><span data-stu-id="acfda-110">The SOAP connection sends the user name and password in plain text.</span></span>  
  
-   <span data-ttu-id="acfda-111">**Digest.**</span><span class="sxs-lookup"><span data-stu-id="acfda-111">**Digest.**</span></span> <span data-ttu-id="acfda-112">La connexion SOAP envoie le nom d'utilisateur et le mot de passe dans un format chiffré.</span><span class="sxs-lookup"><span data-stu-id="acfda-112">The SOAP connection sends the user name and password in an encrypted format.</span></span>  
  
-   <span data-ttu-id="acfda-113">**Kerberos ou NTLM.**</span><span class="sxs-lookup"><span data-stu-id="acfda-113">**Kerberos or NTLM.**</span></span> <span data-ttu-id="acfda-114">Ni le nom d'utilisateur ni le mot de passe n'est envoyé via une connexion SOAP.</span><span class="sxs-lookup"><span data-stu-id="acfda-114">Neither the user name nor the password is sent over a SOAP connection.</span></span> <span data-ttu-id="acfda-115">L'adaptateur SOAP utilise toujours les informations d'identification du processus sous lequel l'adaptateur d'envoi SOAP s'exécute pour ce type d'authentification.</span><span class="sxs-lookup"><span data-stu-id="acfda-115">The SOAP adapter always uses the credentials of the process under which the SOAP send adapter runs for this authentication type.</span></span>  
  
 <span data-ttu-id="acfda-116">En outre, l'adaptateur d'envoi SOAP peut fournir un certificat SSL (Secure Sockets Layer) au serveur Web si le serveur le demande ou l'accepte.</span><span class="sxs-lookup"><span data-stu-id="acfda-116">Additionally, the SOAP send adapter can provide a client Secure Sockets Layer (SSL) certificate to the Web server if the server requires or accepts it.</span></span>  
  
 <span data-ttu-id="acfda-117">Si vous avez activé Enterprise Single Sign-On (SSO), lorsque l’adaptateur d’envoi SOAP reçoit un message avec la demande à la **SSOTicket** propriété, l’adaptateur se connecte à un serveur SSO pour valider et échanger le ticket.</span><span class="sxs-lookup"><span data-stu-id="acfda-117">If you enabled Enterprise Single Sign-On (SSO), when the SOAP send adapter receives a message with the request to the **SSOTicket** property, the adapter connects to an SSO server to validate and redeem the ticket.</span></span> <span data-ttu-id="acfda-118">Une fois que l'adaptateur SOAP a validé le ticket, celui-ci est déchiffré et les informations d'identification pour le système associé sont récupérées dans le magasin d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="acfda-118">After the SOAP adapter validates the ticket, it is decrypted and the credentials for the affiliate system are retrieved from the credential store.</span></span> <span data-ttu-id="acfda-119">L'adaptateur SOAP utilise ensuite ces informations d'identification pour se connecter au système associé et la demande SOAP est traitée.</span><span class="sxs-lookup"><span data-stu-id="acfda-119">The SOAP adapter then uses the credentials to connect to the affiliate system, and the SOAP request is processed.</span></span>  
  
## <a name="client-certificates-for-the-soap-send-adapter"></a><span data-ttu-id="acfda-120">Certificats clients pour l'adaptateur d'envoi SOAP</span><span class="sxs-lookup"><span data-stu-id="acfda-120">Client Certificates for the SOAP Send Adapter</span></span>  
 <span data-ttu-id="acfda-121">L'adaptateur d'envoi SOAP peut établir une connexion sécurisée avec les serveurs qui acceptent ou demandent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="acfda-121">The SOAP send adapter can establish a secure connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="acfda-122">Si un certificat client est spécifié, l'adaptateur d'envoi SOAP utilise le certificat lors de la connexion aux serveurs qui demandent ou acceptent des certificats clients.</span><span class="sxs-lookup"><span data-stu-id="acfda-122">If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="acfda-123">Si le certificat client n'est pas spécifié et que le serveur de destination demande des certificats clients, l'adaptateur d'envoi SOAP ne peut pas envoyer le message et suit la logique standard pour les nouvelles tentatives.</span><span class="sxs-lookup"><span data-stu-id="acfda-123">If you do not specify a client certificate and the destination server requires client certificates, the SOAP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="acfda-124">L'adaptateur d'envoi SOAP utilise le certificat client du magasin Personnel du compte sous lequel le processus [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est exécuté.</span><span class="sxs-lookup"><span data-stu-id="acfda-124">The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="acfda-125">L'adaptateur SOAP spécifie le certificat par son empreinte.</span><span class="sxs-lookup"><span data-stu-id="acfda-125">The SOAP adapter specifies the certificate by its thumbprint.</span></span> <span data-ttu-id="acfda-126">Si l'adaptateur d'envoi SOAP ne peut pas charger le certificat pour une raison quelconque, le message envoyé est interrompu.</span><span class="sxs-lookup"><span data-stu-id="acfda-126">If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
## <a name="negative-acknowledgement-nack-messages-generated-for-failed-transmissions-by-the-http-or-soap-adapters"></a><span data-ttu-id="acfda-127">Messages d'accusé de réception négatif (NACK) générés pour les transmissions échouées par l'adaptateur HTTP ou SOAP</span><span class="sxs-lookup"><span data-stu-id="acfda-127">Negative Acknowledgement (NACK) Messages Generated for Failed Transmissions by the HTTP or SOAP Adapters</span></span>  
 <span data-ttu-id="acfda-128">Lorsqu'un message est transmis avec succès, le moteur de messagerie BizTalk publie un message d'accusé de réception (ACK) associé dans la MessageBox si les accusés de réception sont activés.</span><span class="sxs-lookup"><span data-stu-id="acfda-128">When a message is successfully transmitted, the BizTalk Messaging Engine publishes an associated Acknowledgement (ACK) message to the MessageBox database if delivery notifications are enabled.</span></span> <span data-ttu-id="acfda-129">De même, lorsqu’un message est interrompu par le moteur de messagerie BizTalk ou une orchestration a été suspendue par le moteur d’orchestration, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publie un message d’accusé de réception négatif (NACK) associé à la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="acfda-129">Likewise, when a message is suspended by the BizTalk Messaging Engine or an orchestration is suspended by the orchestration engine, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] publishes an associated Negative Acknowledgement (NACK) message to the MessageBox.</span></span> <span data-ttu-id="acfda-130">Le message d’accusé de réception négatif contient des propriétés de contexte et une partie du corps de message composé d’une erreur SOAP.</span><span class="sxs-lookup"><span data-stu-id="acfda-130">The NACK message contains context properties and a message body part consisting of a SOAP fault.</span></span> <span data-ttu-id="acfda-131">Si le message d’accusé de réception négatif est généré en raison de l’échec d’une transmission des adaptateurs HTTP ou SOAP, l’erreur SOAP contient le **en-têtes** élément et la **corps** élément de la réponse à partir du site Web de destination serveur.</span><span class="sxs-lookup"><span data-stu-id="acfda-131">If the NACK message is generated due to a failed transmission from the HTTP or SOAP adapters, the SOAP fault contains the **Headers** element and the **Body** element of the response from the destination Web server.</span></span> <span data-ttu-id="acfda-132">Voici un exemple d'erreur SOAP dans un accusé de réception négatif généré en raison de l'échec d'une transmission SOAP :</span><span class="sxs-lookup"><span data-stu-id="acfda-132">The following is an example of the SOAP fault in a NACK generated for a failed SOAP transmission:</span></span>  
  
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
>  <span data-ttu-id="acfda-133">Le **en-têtes** élément et la **corps** élément sont limités à 48 Ko.</span><span class="sxs-lookup"><span data-stu-id="acfda-133">The **Headers** element and the **Body** element are limited to 48 KB.</span></span> <span data-ttu-id="acfda-134">Le **en-têtes** élément est arrondi à la paire de valeur d’en-tête complet le plus proche sans dépasser la limite.</span><span class="sxs-lookup"><span data-stu-id="acfda-134">The **Headers** element is rounded to the nearest complete header value pair without exceeding the limit.</span></span> <span data-ttu-id="acfda-135">Le **corps** élément est tronqué à 48 Ko.</span><span class="sxs-lookup"><span data-stu-id="acfda-135">The **Body** element is truncated to 48 KB.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acfda-136">Les messages NACK et ACK sont ignorés si aucun abonnement ne correspond pour eux.</span><span class="sxs-lookup"><span data-stu-id="acfda-136">NACK and ACK messages are discarded if there are no matching subscriptions for them.</span></span> <span data-ttu-id="acfda-137">Ils ne sont pas interrompus par le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="acfda-137">NACK and ACK messages are not suspended by the Messaging Engine.</span></span>  
  
 <span data-ttu-id="acfda-138">Pour vous abonner à un accusé de réception négatif, vous pouvez effectuer l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="acfda-138">To subscribe to a NACK message, you can do one of the following:</span></span>  
  
1.  <span data-ttu-id="acfda-139">Créer un port d'envoi avec un filtre pour la propriété de contexte de message appropriée.</span><span class="sxs-lookup"><span data-stu-id="acfda-139">Create a send port with a filter for the appropriate message context property.</span></span> <span data-ttu-id="acfda-140">Consultez **propriétés de contexte de Message** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] pour obtenir la liste des propriétés de contexte de message système, y compris ceux liés à accusé de réception de message.</span><span class="sxs-lookup"><span data-stu-id="acfda-140">See **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] for a listing of system message context properties including those related to message acknowledgment.</span></span>  
  
2.  <span data-ttu-id="acfda-141">Envoyer à partir d’un port d’orchestration marqué avec **accusé de réception = transmis**.</span><span class="sxs-lookup"><span data-stu-id="acfda-141">Send from an orchestration port marked with **Delivery Notification = Transmitted**.</span></span> <span data-ttu-id="acfda-142">Si un port d’orchestration est marqué avec **accusé de réception = transmis**, l’orchestration attend jusqu'à ce qu’il reçoit un accusé de réception ou un accusé de réception négatif pour le message a été transmis.</span><span class="sxs-lookup"><span data-stu-id="acfda-142">If an orchestration port is marked with **Delivery Notification = Transmitted**, the orchestration will wait until it receives either an ACK or a NACK for the message that was transmitted.</span></span> <span data-ttu-id="acfda-143">Si un accusé de réception négatif est généré, il est routé vers l'orchestration, qui génère une exception DeliveryFailureException.</span><span class="sxs-lookup"><span data-stu-id="acfda-143">If a NACK is generated then it will be routed to the orchestration and the orchestration will throw a DeliveryFailureException.</span></span> <span data-ttu-id="acfda-144">DeliveryFailureException est désérialisée à partir de l'erreur SOAP contenue dans le corps du message d'accusé de réception négatif.</span><span class="sxs-lookup"><span data-stu-id="acfda-144">The DeliveryFailureException is deserialized from the SOAP fault that is contained within the NACK message body.</span></span> <span data-ttu-id="acfda-145">Pour extraire la chaîne de message d'exception de l'erreur SOAP renvoyée à l'orchestration, convertissez DeliveryFailureException en SoapException, puis accédez à InnerXml depuis la section relative aux détails SOAP.</span><span class="sxs-lookup"><span data-stu-id="acfda-145">To retrieve the exception message string from the SOAP fault that is returned to the orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml from the SOAP Detail section.</span></span> <span data-ttu-id="acfda-146">L'exemple de code suivant illustre comment procéder :</span><span class="sxs-lookup"><span data-stu-id="acfda-146">The following code sample demonstrates how to do this:</span></span>  
  
    ```  
    // Cast the DeliveryFailureException to a SoapException…  
    System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
    System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
    //e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
    //object type created in an Exception handler  
    ```  
  
     <span data-ttu-id="acfda-147">L'exemple de code précédent renvoie un fragment XML semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="acfda-147">The code sample above will return an XML fragment similar to the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="acfda-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acfda-148">See Also</span></span>  
 <span data-ttu-id="acfda-149">[Nouveautés de l’adaptateur SOAP ?](../core/what-is-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="acfda-149">[What Is the SOAP Adapter?](../core/what-is-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="acfda-150">Recommandations de sécurité de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="acfda-150">SOAP Adapter Security Recommendations</span></span>](../core/soap-adapter-security-recommendations.md)