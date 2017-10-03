---
title: "Étape 3d : L’activation de BizTalk Server envoyer et recevoir des Messages de Salesforce | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 470c4a72-1e97-4493-8958-33a13f793ffd
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c38a58e376bbc8908ff0fe578aa54cbb009c58d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce"></a><span data-ttu-id="6f009-102">Étape 3d : L’activation de BizTalk Server envoyer et recevoir des Messages de Salesforce</span><span class="sxs-lookup"><span data-stu-id="6f009-102">Step 3d: Enabling BizTalk Server to Send and Receive Messages from Salesforce</span></span>
<span data-ttu-id="6f009-103">Nous devons nous authentifier auprès de Salesforce lors l'envoi de messages à l'aide de l'interface REST.</span><span class="sxs-lookup"><span data-stu-id="6f009-103">We must authenticate with Salesforce while sending messages using the REST interface.</span></span> <span data-ttu-id="6f009-104">Les méthodes d'authentification pour les appels REST pris en charge par Salesforce ne sont pas immédiatement prêts à l'emploi avec l'adaptateur WCF-WebHtt, que nous allons utiliser pour appeler l'interface REST de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-104">The authentication methods for REST calls supported by Salesforce are not available out of the box with the WCF-WebHttp adapter, which we’ll use to invoke Salesforce’s REST interface.</span></span> <span data-ttu-id="6f009-105">Ainsi, nous allons créer un comportement de point de terminaison WCF personnalisé, puis l'attacher à l'adaptateur d'envoi WCF-WebHttp que nous allons configurer pour appeler l'interface REST de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-105">So, we’ll create a custom WCF endpoint behavior and then attach it to WCF-WebHttp send adapter that we’ll configure to invoke the Salesforce REST interface.</span></span>  
  
 <span data-ttu-id="6f009-106">De même, la réponse XML reçue de Salesforce ne contiendra aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6f009-106">Similarly, the XML response received from Salesforce will not contain any namespace.</span></span> <span data-ttu-id="6f009-107">Pour que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message de réponse par rapport au schéma de réponse, le message de réponse doit inclure l'espace de noms cible.</span><span class="sxs-lookup"><span data-stu-id="6f009-107">For [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to process the response message against the response schema, the response message must include the target namespace.</span></span> <span data-ttu-id="6f009-108">Nous allons donc créer un pipeline personnalisé à l'aide du [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] pour ajouter un espace de noms au message de réponse.</span><span class="sxs-lookup"><span data-stu-id="6f009-108">So, we’ll create a custom pipeline using the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message.</span></span> <span data-ttu-id="6f009-109">Nous utiliserons ensuite ce pipeline personnalisé comme pipeline de réception pour le port d'envoi WCF-WebHttp requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="6f009-109">We’ll then use this custom pipeline as the receive pipeline for request-response WCF-WebHttp send port.</span></span>  
  
## <a name="add-a-custom-wcf-behavior-for-salesforce-authentication"></a><span data-ttu-id="6f009-110">Ajouter un comportement WCF personnalisé pour l'authentification Salesforce</span><span class="sxs-lookup"><span data-stu-id="6f009-110">Add a Custom WCF Behavior for Salesforce Authentication</span></span>  
 <span data-ttu-id="6f009-111">Salesforce propose différentes options pour permettre aux applications clientes de s'authentifier auprès de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-111">Salesforce provides different options for client applications to authenticate with Salesforce.</span></span> <span data-ttu-id="6f009-112">Nous allons utiliser le termes du contrat de Salesforce en tant que le [nom d’utilisateur-mot de passe](http://go.microsoft.com/fwlink/?LinkId=287082) flux.</span><span class="sxs-lookup"><span data-stu-id="6f009-112">We’ll use what Salesforce terms as the [Username-password](http://go.microsoft.com/fwlink/?LinkId=287082) flow.</span></span> <span data-ttu-id="6f009-113">Du côté client, WCF vous permet de créer [inspecteurs de Message](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx) pour modifier les messages avant leur envoi ou après leur réception.</span><span class="sxs-lookup"><span data-stu-id="6f009-113">On the client side, WCF enables you to create [Message Inspectors](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx) to alter messages before they are sent or after they are received.</span></span> <span data-ttu-id="6f009-114">Un inspecteur de message est une extension du runtime client et est configuré comme un comportement.</span><span class="sxs-lookup"><span data-stu-id="6f009-114">A message inspector is an extension to the client runtime and is configured as a behavior.</span></span> <span data-ttu-id="6f009-115">Un comportement est, à son tour, ajouté à un élément d'extension de comportement.</span><span class="sxs-lookup"><span data-stu-id="6f009-115">A behavior, in turn, is added to a behavior extension element.</span></span> <span data-ttu-id="6f009-116">Cet élément d'extension de comportement est inscrit dans machine.config avec un nom d'élément, ce qui le rend disponible pour être configuré comme comportement personnalisé sur un port WCF.</span><span class="sxs-lookup"><span data-stu-id="6f009-116">This behavior extension element is registered in the machine.config with an element name, which makes it available to be configured as a custom behavior on a WCF port.</span></span> <span data-ttu-id="6f009-117">Pour plus d’informations, consultez [extension de WCF grâce aux comportements personnalisés](http://msdn.microsoft.com/magazine/cc163302.aspx).</span><span class="sxs-lookup"><span data-stu-id="6f009-117">For more information, see [Extending WCF with Custom Behaviors](http://msdn.microsoft.com/magazine/cc163302.aspx).</span></span> <span data-ttu-id="6f009-118">Nous allons utiliser cette approche pour incorporer le flux nom d'utilisateur-authentification pour nous authentifier auprès de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-118">We are going to use this approach to incorporate the username-authentication flow for authenticating with Salesforce.</span></span> <span data-ttu-id="6f009-119">Les grandes étapes que nous allons suivre sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="6f009-119">The broad steps that we’ll follow are:</span></span>  
  
-   <span data-ttu-id="6f009-120">Créer un inspecteur de message qui lance un appel HTTP POST au point de terminaison d'authentification Salesforce et reçoit un jeton d'accès.</span><span class="sxs-lookup"><span data-stu-id="6f009-120">Create a message inspector that makes an HTTP POST call to the Salesforce authentication endpoint and receives an access token.</span></span> <span data-ttu-id="6f009-121">L'inspecteur de message ajoute ensuite le jeton d'authentification comme valeur d'en-tête d'autorisation du message de requête envoyé à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-121">The message inspector then adds the authentication token as the value of the Authorization header of the query message being sent to Salesforce.</span></span> <span data-ttu-id="6f009-122">L'inspecteur de message ajoute également l'en-tête Accepter pour le message de la requête de sorte que la réponse reçue soit au format XML.</span><span class="sxs-lookup"><span data-stu-id="6f009-122">The message inspector also adds the Accept header to the request message so that the response received is in an XML format.</span></span> <span data-ttu-id="6f009-123">Dans le cas contraire, Salesforce envoie le message au format JSON par défaut.</span><span class="sxs-lookup"><span data-stu-id="6f009-123">Otherwise, Salesforce sends the message in the default JSON format.</span></span>  
  
-   <span data-ttu-id="6f009-124">Créer un comportement de point de terminaison pour appliquer l'inspecteur de message au point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="6f009-124">Create an endpoint behavior to apply the message inspector to the client endpoint.</span></span>  
  
-   <span data-ttu-id="6f009-125">Créer un élément d'extension de comportement pour activer la configuration du comportement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6f009-125">Create a behavior extension element to enable configuration of the endpoint behavior.</span></span>  
  
#### <a name="to-create-a-message-inspector"></a><span data-ttu-id="6f009-126">Pour créer un inspecteur de message</span><span class="sxs-lookup"><span data-stu-id="6f009-126">To create a message inspector</span></span>  
  
1.  <span data-ttu-id="6f009-127">Dans le cadre de la **BtsSalesforceIntegration** solution dans Visual Studio, créez une bibliothèque de classes c#.</span><span class="sxs-lookup"><span data-stu-id="6f009-127">As part of the **BtsSalesforceIntegration** solution in Visual Studio, create a C# Class Library.</span></span> <span data-ttu-id="6f009-128">Nommez-le `Microsoft.BizTalk.Adapter.Behaviors` et ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="6f009-128">Name it `Microsoft.BizTalk.Adapter.Behaviors` and add the following namespaces:</span></span>  
  
    ```  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Dispatcher;  
    using System.ServiceModel.Channels;  
    using System.Xml;  
    using System.Net;  
    using System.IO;  
    using System.ServiceModel.Configuration;  
    using System.Configuration;  
    using System.Web.Script.Serialization;  
    ```  
  
2.  <span data-ttu-id="6f009-129">À partir de l'Explorateur de solutions, ajoutez des références à `System.ServiceModel`, `System.Web.Extensions` et `System.Configuration`.</span><span class="sxs-lookup"><span data-stu-id="6f009-129">From the Solution Explorer, add references to `System.ServiceModel`, `System.Web.Extensions`, and `System.Configuration`.</span></span>  
  
3.  <span data-ttu-id="6f009-130">Ajoutez une classe `SalesforceOAuthToken` ayant les propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="6f009-130">Add a class `SalesforceOAuthToken` with the following properties.</span></span> <span data-ttu-id="6f009-131">Cette classe représente le jeton d'autorisation qui est reçu de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-131">This class represents the authorization token that is received from Salesforce.</span></span>  
  
    ```  
    public class SalesforceOAuthToken  
    {  
        public string id { get; set; }  
        public string issued_at { get; set; }  
        public string refresh_token { get; set; }  
        public string instance_url { get; set; }  
        public string signature { get; set; }  
        public string access_token { get; set; }  
    }  
    ```  
  
4.  <span data-ttu-id="6f009-132">Ajoutez une classe `SalesforceRESTSecurityBehavior` qui implémente l'`IClientMessageInspector` et le `IEndpointBehavior`.</span><span class="sxs-lookup"><span data-stu-id="6f009-132">Add a class `SalesforceRESTSecurityBehavior` that implements the `IClientMessageInspector` and the `IEndpointBehavior`.</span></span> <span data-ttu-id="6f009-133">Cette classe inclut les méthodes `HttpPost()` et `FetchOAuthToken()` qui lancent un appel HTTP POST au point de terminaison d'authentification Salesforce pour extraire le jeton d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="6f009-133">This class includes the `HttpPost()` and `FetchOAuthToken()` methods that make an HTTP POST call to the Salesforce authentication endpoint to retrieve the authorization token.</span></span>  
  
     <span data-ttu-id="6f009-134">Comme la classe `SalesforceRESTSecurityBehavior` implémente l'interface `IClientMessageInspector`, elle doit implémenter les deux méthodes, `AfterReceiveReply()` et `BeforeSendRequest()`.</span><span class="sxs-lookup"><span data-stu-id="6f009-134">Because the `SalesforceRESTSecurityBehavior` class implements the `IClientMessageInspector` interface, it must implement the two methods, `AfterReceiveReply()` and `BeforeSendRequest()`.</span></span> <span data-ttu-id="6f009-135">Pour ce scénario, nous n'avons besoin de rien faire dans le cadre de la méthode `AfterReceiverReply()`.</span><span class="sxs-lookup"><span data-stu-id="6f009-135">For this scenario we do not need to do anything as part of the `AfterReceiverReply()` method.</span></span> <span data-ttu-id="6f009-136">Cependant, la méthode `BeforeSendRequest()` appelle la méthode `FetchOAuthToken()`, laquelle à son tour appelle la méthode `HttpPost()`.</span><span class="sxs-lookup"><span data-stu-id="6f009-136">However, the `BeforeSendRequest()` method invokes the `FetchOAuthToken()` method, which in turn calls the `HttpPost()` method.</span></span> <span data-ttu-id="6f009-137">La méthode `BeforeSendRequest()` ajoute alors le jeton d'autorisation dans l'en-tête du message.</span><span class="sxs-lookup"><span data-stu-id="6f009-137">The `BeforeSendRequest()` method then adds the authorization token as part of the message header.</span></span> <span data-ttu-id="6f009-138">Il ajoute également le **accepter** en-tête pour vous assurer que la réponse reçue de Salesforce est au format XML.</span><span class="sxs-lookup"><span data-stu-id="6f009-138">It also adds the **Accept** header to ensure that that the response received from Salesforce is in an XML format.</span></span>  
  
     <span data-ttu-id="6f009-139">L'implémentation de `IEndpointBehavior` ajoute simplement la classe d'inspecteur de message au comportement d'un point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="6f009-139">The `IEndpointBehavior` implementation simply adds the message inspector class to the client endpoint behavior.</span></span>  
  
    ```  
    public class SalesforceRESTSecurityBehavior : IClientMessageInspector, IEndpointBehavior  
    {  
        // Some constants  
        private static string SalesforceAuthEndpoint = "https://login.salesforce.com/services/oauth2/token";  
  
        // Configuration Properties  
        private string username_;  
        private string password_;  
        private string consumerKey_;  
        private string consumerSecret_;  
        private int sessionTimeout_;  
  
        // Private Properties  
        private SalesforceOAuthToken token_;  
        private DateTime tokenExpiryTime_;  
  
        public SalesforceRESTSecurityBehavior(  
            string username,  
            string password,  
            string consumerKey,  
            string consumerSecret,  
            int sessionTimeout)  
        {  
            this.username_ = username;  
            this.password_ = password;  
            this.consumerKey_ = consumerKey;  
            this.consumerSecret_ = consumerSecret;  
            this.sessionTimeout_ = sessionTimeout;  
        }  
  
        private void FetchOAuthToken()  
        {  
            if ((tokenExpiryTime_ == null) || (tokenExpiryTime_.CompareTo(DateTime.Now) <= 0))  
            {  
                StringBuilder body = new StringBuilder();  
                body.Append("grant_type=password&")  
                    .Append("client_id=" + consumerKey_ + "&")  
                    .Append("client_secret=" + consumerSecret_ + "&")  
                    .Append("username=" + username_ + "&")  
                    .Append("password=" + password_);  
  
                string result;  
  
                try  
                {  
                    result = HttpPost(SalesforceAuthEndpoint, body.ToString());  
                }  
                catch (WebException)  
                {  
                    // do something  
                    return;  
                }  
  
                // Convert the JSON response into a token object  
                JavaScriptSerializer ser = new JavaScriptSerializer();  
                this.token_ = ser.Deserialize<SalesforceOAuthToken>(result);  
                this.tokenExpiryTime_ = DateTime.Now.AddSeconds(this.sessionTimeout_);  
            }  
        }  
  
        public string HttpPost(string URI, string Parameters)  
        {  
            WebRequest req = WebRequest.Create(URI);  
            req.ContentType = "application/x-www-form-urlencoded";  
            req.Method = "POST";  
  
            // Add parameters to post  
            byte[] data = Encoding.ASCII.GetBytes(Parameters);  
            req.ContentLength = data.Length;  
            System.IO.Stream os = req.GetRequestStream();  
            os.Write(data, 0, data.Length);  
            os.Close();  
  
            // Do the post and get the response.  
            System.Net.WebResponse resp = null;  
            resp = req.GetResponse();  
  
            StreamReader sr = new StreamReader(resp.GetResponseStream());  
            return sr.ReadToEnd().Trim();  
        }  
        #region IClientMessageInspector  
  
        public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
        {  
            // do nothing  
        }  
        public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
        {  
            // We are going to send a request to Salesforce  
            // Overview:  
            // This behavior will do the following:  
            // (1) Fetch Token from Salesforce, if required  
            // (2) Add the token to the message  
            // (3) Insert an Http Accept header so we get XML data in response, instead of JSON, which is default  
            // Reference: http://www.salesforce.com/us/developer/docs/api_rest/index.htm  
            //  
            // (1) Authentication with Salesforce  
            // (2) The token is added to the HTTP Authorization Header   
            // (3) Add the Accept Header  
            //  
  
            HttpRequestMessageProperty httpRequest = null;  
  
            if (request.Properties.ContainsKey(HttpRequestMessageProperty.Name))  
            {  
                httpRequest = request.Properties[HttpRequestMessageProperty.Name] as HttpRequestMessageProperty;  
            }  
  
            if (httpRequest == null)  
            {  
                // NOTE: Ideally, we shouldn’t get here for WebHttp  
                httpRequest = new HttpRequestMessageProperty()  
                {  
                    Method = "GET",  
                    SuppressEntityBody = true  
                };  
                request.Properties.Add(HttpRequestMessageProperty.Name, httpRequest);  
            }  
  
            WebHeaderCollection headers = httpRequest.Headers;  
            FetchOAuthToken();  
  
            headers.Add(HttpRequestHeader.Authorization, "OAuth " + this.token_.access_token);  
            headers.Add(HttpRequestHeader.Accept, "application/xml");  
  
            return null;  
        }  
  
        #endregion IClientMessageInspector  
  
        #region IEndpointBehavior  
  
        public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
        {  
            // do nothing  
        }  
  
        public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
        {  
            clientRuntime.MessageInspectors.Add(this);  
        }  
  
        public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
        {  
            // do nothing  
        }  
  
        public void Validate(ServiceEndpoint endpoint)  
        {  
            // do nothing  
        }  
  
        #endregion IEndpointBehavior  
    }  
    ```  
  
5.  <span data-ttu-id="6f009-140">Dans l'étape précédente, nous avons créé une classe de comportement qui applique l'inspecteur de message au point de terminaison client.</span><span class="sxs-lookup"><span data-stu-id="6f009-140">In the previous step we created a behavior class that applies the message inspector to the client endpoint.</span></span> <span data-ttu-id="6f009-141">Nous devons maintenant mettre ce comportement à la disposition de l'expérience de la configuration pour l'adaptateur WCF-WebHttp qui enverra le message de la requête à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-141">We now need to make this behavior available to the configuration experience for the WCF-WebHttp adapter that will send the request message to Salesforce.</span></span> <span data-ttu-id="6f009-142">Pour rendre ce comportement disponible pour la configuration, nous devons faire deux choses :</span><span class="sxs-lookup"><span data-stu-id="6f009-142">To make this behavior available for configuration we need to do two things:</span></span>  
  
    -   <span data-ttu-id="6f009-143">Créer une classe qui dérive de `BehaviorExtensionElement`</span><span class="sxs-lookup"><span data-stu-id="6f009-143">Create a class that derives from the `BehaviorExtensionElement`</span></span>  
  
    -   <span data-ttu-id="6f009-144">Inscrire votre BehavaiorExtensionElement dans le \<extensions >\\< behaviorExtensions\> élément dans le fichier machine.config à l’aide d’un nom d’élément.</span><span class="sxs-lookup"><span data-stu-id="6f009-144">Register your BehavaiorExtensionElement in the \<extensions>\\<behaviorExtensions\> element in the machine.config using an element name.</span></span>  
  
     <span data-ttu-id="6f009-145">Nous allons également ajouter des propriétés de configuration à cette classe afin qu'elles soient disponibles à partir de l'interface utilisateur de configuration de l'adaptateur WCF-WebHttp.</span><span class="sxs-lookup"><span data-stu-id="6f009-145">We’ll also add configuration properties to this class so that they are available from the WCF-WebHttp adapter configuration UI.</span></span>  
  
    ```  
    public class SalesforceRESTBehaviorElement : BehaviorExtensionElement  
    {  
        public override Type BehaviorType  
        {  
            get { return typeof(SalesforceRESTSecurityBehavior); }  
        }  
  
        protected override object CreateBehavior()  
        {  
            return new SalesforceRESTSecurityBehavior(Username, Password, ConsumerKey, ConsumerSecret, SessionTimeout);  
        }  
  
        [ConfigurationProperty("username", IsRequired = true)]  
        public string Username  
        {  
            get { return (string)this["username"]; }  
            set { this["username"] = value; }  
        }  
  
        [ConfigurationProperty("password", IsRequired = true)]  
        public string Password  
        {  
            get { return (string)this["password"]; }  
            set { this["password"] = value; }  
        }  
  
        [ConfigurationProperty("consumerKey", IsRequired = true)]  
        public string ConsumerKey  
        {  
            get { return (string)this["consumerKey"]; }  
            set { this["consumerKey"] = value; }  
        }  
  
        [ConfigurationProperty("consumerSecret", IsRequired = true)]  
        public string ConsumerSecret  
        {  
            get { return (string)this["consumerSecret"]; }  
            set { this["consumerSecret"] = value; }  
        }  
  
        [ConfigurationProperty("sessionTimeout", IsRequired = false, DefaultValue = 300)]  
        public int SessionTimeout  
        {  
            get { return (int)this["sessionTimeout"]; }  
            set { this["sessionTimeout"] = value; }  
        }  
    }  
    ```  
  
6.  <span data-ttu-id="6f009-146">Ajoutez un fichier de clé de nom fort pour le projet et construisez le projet.</span><span class="sxs-lookup"><span data-stu-id="6f009-146">Add a strong name key file to the project and build the project.</span></span> <span data-ttu-id="6f009-147">Une fois le projet construit avec succès, ajoutez l'assembly `Microsoft.BizTalk.Adapter.Behaviors` au GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="6f009-147">Once the project builds successfully, add the assembly `Microsoft.BizTalk.Adapter.Behaviors` to the GAC.</span></span>  
  
7.  <span data-ttu-id="6f009-148">Ajoutez l'entrée suivante dans machine.config sous System.ServiceModel\Extensions\BehaviorExtensions.</span><span class="sxs-lookup"><span data-stu-id="6f009-148">Add the following entry in the machine.config under System.ServiceModel\Extensions\BehaviorExtensions.</span></span>  
  
    ```  
    <add name="Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce" type="Microsoft.BizTalk.Adapter.Behaviors.SalesforceRESTBehaviorElement, Microsoft.BizTalk.Adapter.Behaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=45bd7fe67ef032db"/>  
    ```  
  
     <span data-ttu-id="6f009-149">Vous pouvez récupérer le jeton de clé publique pour l'assembly à partir du GAC.</span><span class="sxs-lookup"><span data-stu-id="6f009-149">You can retrieve the public key token for the assembly from the GAC.</span></span> <span data-ttu-id="6f009-150">En outre, si vous créez cette application sur un ordinateur 64 bits, vous devez ajouter cette entrée à la fois aux versions 32 bits et 64 bits de machine.config.</span><span class="sxs-lookup"><span data-stu-id="6f009-150">Also, if you are creating this application on a 64-bit computer, you must add this entry to both 32-bit and 64-bit versions of the machine.config.</span></span>  
  
## <a name="add-a-custom-pipeline-to-add-namespace-to-the-salesforce-response"></a><span data-ttu-id="6f009-151">Ajouter un pipeline personnalisé pour ajouter un espace de noms à la réponse de Salesforce</span><span class="sxs-lookup"><span data-stu-id="6f009-151">Add a Custom Pipeline to Add Namespace to the Salesforce Response</span></span>  
 <span data-ttu-id="6f009-152">La réponse reçue de Salesforce ne comprend pas d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6f009-152">The response received from Salesforce does not include a namespace.</span></span> <span data-ttu-id="6f009-153">Toutefois, pour traiter le message de réponse par rapport au schéma de réponse (QueryResult.xsd) nous devons inclure l'espace de noms dans la réponse Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-153">However, to process the response message against the response schema (QueryResult.xsd) we must include the namespace in the Salesforce response.</span></span> <span data-ttu-id="6f009-154">Dans cette section, nous créons un pipeline personnalisé et utilisons un composant de pipeline personnalisé livré avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] pour ajouter un espace de noms au message de réponse.</span><span class="sxs-lookup"><span data-stu-id="6f009-154">In this section, we create a custom pipeline and use a custom pipeline component shipped with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] to add a namespace to the response message.</span></span> <span data-ttu-id="6f009-155">Ce pipeline personnalisé est déployé avec l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et servira de pipeline de réception lors de la configuration de l'adaptateur WCF-WebHttp.</span><span class="sxs-lookup"><span data-stu-id="6f009-155">This custom pipeline is deployed with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application and will be used as the receive pipeline while configuring the WCF-WebHttp adapter.</span></span>  
  
 <span data-ttu-id="6f009-156">Avant d'effectuer les étapes de cette procédure, assurez-vous que [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est installé et configuré sur l'ordinateur où vous créez cette application.</span><span class="sxs-lookup"><span data-stu-id="6f009-156">Before performing the steps in this procedure, ensure that [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is installed and configured on the computer where you are creating this application.</span></span>  
  
#### <a name="to-add-a-custom-pipeline"></a><span data-ttu-id="6f009-157">Pour ajouter un pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="6f009-157">To add a custom pipeline</span></span>  
  
1.  <span data-ttu-id="6f009-158">Dans le **BtsSalesforceIntegration** solution, créer un nouveau [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet.</span><span class="sxs-lookup"><span data-stu-id="6f009-158">Within the **BtsSalesforceIntegration** solution, create a new [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="6f009-159">Nommez le projet `CustomPipeline`.</span><span class="sxs-lookup"><span data-stu-id="6f009-159">Name the project `CustomPipeline`.</span></span>  
  
2.  <span data-ttu-id="6f009-160">Dans le **CustomPipeline** de projet, ajoutez un nouveau pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="6f009-160">Within the **CustomPipeline** project, add a new receive pipeline.</span></span> <span data-ttu-id="6f009-161">Nommez le pipeline en tant que `AddNamespace.btp`.</span><span class="sxs-lookup"><span data-stu-id="6f009-161">Name the pipeline as `AddNamespace.btp`.</span></span>  
  
3.  <span data-ttu-id="6f009-162">Dans le **Decode** étape du pipeline, à partir de la boîte à outils, faites glisser et déposez le **Namespace ajouter d’ESB** composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6f009-162">Within the **Decode** stage of the pipeline, from the toolbox, drag and drop the **ESB Add Namespace** pipeline component.</span></span> <span data-ttu-id="6f009-163">Dans le **désassembler** à l’étape, faites glisser le **désassembleur XML** composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="6f009-163">Within the **Disassemble** stage, drag and drop the **XML disassembler** pipeline component.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6f009-164">Si le **Namespace ajouter d’ESB** composant de pipeline n’est pas répertorié dans la boîte à outils, vous pouvez l’ajouter.</span><span class="sxs-lookup"><span data-stu-id="6f009-164">If the **ESB Add Namespace** pipeline component is not listed in the toolbox, you can add it.</span></span> <span data-ttu-id="6f009-165">Cliquez sur le **composants de Pipeline BizTalk** onglet, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="6f009-165">Right-click the **BizTalk Pipeline Components** tab, and then click **Choose Items**.</span></span> <span data-ttu-id="6f009-166">Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** , sélectionnez la case à cocher **Namespace ajouter d’ESB** composant, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f009-166">In the **Choose Toolbox Items** dialog box, click the **BizTalk Pipeline Components** tab, select the check box for **ESB Add Namespace** component, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="6f009-167">Ajoutez un fichier de clé de nom fort pour le projet et enregistrez le projet.</span><span class="sxs-lookup"><span data-stu-id="6f009-167">Add a strong name key file to the project and save the project.</span></span>  
  
5.  <span data-ttu-id="6f009-168">Cliquez sur le **CustomPipeline** de projet et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="6f009-168">Right-click the **CustomPipeline** project and select **Properties**.</span></span> <span data-ttu-id="6f009-169">Dans le **déploiement** onglet, pour **nom de l’Application**, entrez `SalesforceIntegration`.</span><span class="sxs-lookup"><span data-stu-id="6f009-169">In the **Deployment** tab, for **Application Name**, enter `SalesforceIntegration`.</span></span>  
  
6.  <span data-ttu-id="6f009-170">Enregistrez les modifications apportées au projet.</span><span class="sxs-lookup"><span data-stu-id="6f009-170">Save changes to the project.</span></span>  
  
 <span data-ttu-id="6f009-171">Dans cette rubrique, vous avez ajouté un comportement personnalisé pour vous authentifier auprès de Salesforce et un pipeline personnalisé pour ajouter un espace de noms à la réponse de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="6f009-171">In this topic, added a custom behavior to authenticate with Salesforce and a custom pipeline to add a namespace to the Salesforce response.</span></span> <span data-ttu-id="6f009-172">Nous allons utiliser ces composants personnalisés lors de la configuration de ports physiques dans la console d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6f009-172">We’ll use these custom components while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f009-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f009-173">See Also</span></span>  
 [<span data-ttu-id="6f009-174">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f009-174">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)