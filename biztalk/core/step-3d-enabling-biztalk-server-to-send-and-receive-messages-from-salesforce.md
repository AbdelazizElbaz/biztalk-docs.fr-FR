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
ms.openlocfilehash: 9d8489c484bdb88a292b998d31e7c6de90e0937c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3d-enabling-biztalk-server-to-send-and-receive-messages-from-salesforce"></a>Étape 3d : L’activation de BizTalk Server envoyer et recevoir des Messages de Salesforce
Nous devons nous authentifier auprès de Salesforce lors l'envoi de messages à l'aide de l'interface REST. Les méthodes d'authentification pour les appels REST pris en charge par Salesforce ne sont pas immédiatement prêts à l'emploi avec l'adaptateur WCF-WebHtt, que nous allons utiliser pour appeler l'interface REST de Salesforce. Ainsi, nous allons créer un comportement de point de terminaison WCF personnalisé, puis l'attacher à l'adaptateur d'envoi WCF-WebHttp que nous allons configurer pour appeler l'interface REST de Salesforce.  
  
 De même, la réponse XML reçue de Salesforce ne contiendra aucun espace de noms. Pour que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite le message de réponse par rapport au schéma de réponse, le message de réponse doit inclure l'espace de noms cible. Nous allons donc créer un pipeline personnalisé à l'aide du [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] pour ajouter un espace de noms au message de réponse. Nous utiliserons ensuite ce pipeline personnalisé comme pipeline de réception pour le port d'envoi WCF-WebHttp requête-réponse.  
  
## <a name="add-a-custom-wcf-behavior-for-salesforce-authentication"></a>Ajouter un comportement WCF personnalisé pour l'authentification Salesforce  
 Salesforce propose différentes options pour permettre aux applications clientes de s'authentifier auprès de Salesforce. Nous allons utiliser le termes du contrat de Salesforce en tant que le [nom d’utilisateur-mot de passe](http://go.microsoft.com/fwlink/?LinkId=287082) flux. Du côté client, WCF vous permet de créer [inspecteurs de Message](http://msdn.microsoft.com/library/aa717047\(v=VS.90\).aspx) pour modifier les messages avant leur envoi ou après leur réception. Un inspecteur de message est une extension du runtime client et est configuré comme un comportement. Un comportement est, à son tour, ajouté à un élément d'extension de comportement. Cet élément d'extension de comportement est inscrit dans machine.config avec un nom d'élément, ce qui le rend disponible pour être configuré comme comportement personnalisé sur un port WCF. Pour plus d’informations, consultez [extension de WCF grâce aux comportements personnalisés](http://msdn.microsoft.com/magazine/cc163302.aspx). Nous allons utiliser cette approche pour incorporer le flux nom d'utilisateur-authentification pour nous authentifier auprès de Salesforce. Les grandes étapes que nous allons suivre sont les suivantes :  
  
-   Créer un inspecteur de message qui lance un appel HTTP POST au point de terminaison d'authentification Salesforce et reçoit un jeton d'accès. L'inspecteur de message ajoute ensuite le jeton d'authentification comme valeur d'en-tête d'autorisation du message de requête envoyé à Salesforce. L'inspecteur de message ajoute également l'en-tête Accepter pour le message de la requête de sorte que la réponse reçue soit au format XML. Dans le cas contraire, Salesforce envoie le message au format JSON par défaut.  
  
-   Créer un comportement de point de terminaison pour appliquer l'inspecteur de message au point de terminaison client.  
  
-   Créer un élément d'extension de comportement pour activer la configuration du comportement du point de terminaison.  
  
#### <a name="to-create-a-message-inspector"></a>Pour créer un inspecteur de message  
  
1.  Dans le cadre de la **BtsSalesforceIntegration** solution dans Visual Studio, créez une bibliothèque de classes c#. Nommez-le `Microsoft.BizTalk.Adapter.Behaviors` et ajoutez les espaces de noms suivants :  
  
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
  
2.  À partir de l'Explorateur de solutions, ajoutez des références à `System.ServiceModel`, `System.Web.Extensions` et `System.Configuration`.  
  
3.  Ajoutez une classe `SalesforceOAuthToken` ayant les propriétés suivantes. Cette classe représente le jeton d'autorisation qui est reçu de Salesforce.  
  
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
  
4.  Ajoutez une classe `SalesforceRESTSecurityBehavior` qui implémente l'`IClientMessageInspector` et le `IEndpointBehavior`. Cette classe inclut les méthodes `HttpPost()` et `FetchOAuthToken()` qui lancent un appel HTTP POST au point de terminaison d'authentification Salesforce pour extraire le jeton d'autorisation.  
  
     Comme la classe `SalesforceRESTSecurityBehavior` implémente l'interface `IClientMessageInspector`, elle doit implémenter les deux méthodes, `AfterReceiveReply()` et `BeforeSendRequest()`. Pour ce scénario, nous n'avons besoin de rien faire dans le cadre de la méthode `AfterReceiverReply()`. Cependant, la méthode `BeforeSendRequest()` appelle la méthode `FetchOAuthToken()`, laquelle à son tour appelle la méthode `HttpPost()`. La méthode `BeforeSendRequest()` ajoute alors le jeton d'autorisation dans l'en-tête du message. Il ajoute également le **accepter** en-tête pour vous assurer que la réponse reçue de Salesforce est au format XML.  
  
     L'implémentation de `IEndpointBehavior` ajoute simplement la classe d'inspecteur de message au comportement d'un point de terminaison client.  
  
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
  
5.  Dans l'étape précédente, nous avons créé une classe de comportement qui applique l'inspecteur de message au point de terminaison client. Nous devons maintenant mettre ce comportement à la disposition de l'expérience de la configuration pour l'adaptateur WCF-WebHttp qui enverra le message de la requête à Salesforce. Pour rendre ce comportement disponible pour la configuration, nous devons faire deux choses :  
  
    -   Créer une classe qui dérive de `BehaviorExtensionElement`  
  
    -   Inscrire votre BehavaiorExtensionElement dans le \<extensions\>\\< behaviorExtensions\> élément dans le fichier machine.config à l’aide d’un nom d’élément.  
  
     Nous allons également ajouter des propriétés de configuration à cette classe afin qu'elles soient disponibles à partir de l'interface utilisateur de configuration de l'adaptateur WCF-WebHttp.  
  
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
  
6.  Ajoutez un fichier de clé de nom fort pour le projet et construisez le projet. Une fois le projet construit avec succès, ajoutez l'assembly `Microsoft.BizTalk.Adapter.Behaviors` au GAC (Global Assembly Cache).  
  
7.  Ajoutez l'entrée suivante dans machine.config sous System.ServiceModel\Extensions\BehaviorExtensions.  
  
    ```  
    <add name="Microsoft.BizTalk.Adapter.Behaviors.Demo.Salesforce" type="Microsoft.BizTalk.Adapter.Behaviors.SalesforceRESTBehaviorElement, Microsoft.BizTalk.Adapter.Behaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=45bd7fe67ef032db"/>  
    ```  
  
     Vous pouvez récupérer le jeton de clé publique pour l'assembly à partir du GAC. En outre, si vous créez cette application sur un ordinateur 64 bits, vous devez ajouter cette entrée à la fois aux versions 32 bits et 64 bits de machine.config.  
  
## <a name="add-a-custom-pipeline-to-add-namespace-to-the-salesforce-response"></a>Ajouter un pipeline personnalisé pour ajouter un espace de noms à la réponse de Salesforce  
 La réponse reçue de Salesforce ne comprend pas d'espace de noms. Toutefois, pour traiter le message de réponse par rapport au schéma de réponse (QueryResult.xsd) nous devons inclure l'espace de noms dans la réponse Salesforce. Dans cette section, nous créons un pipeline personnalisé et utilisons un composant de pipeline personnalisé livré avec [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] pour ajouter un espace de noms au message de réponse. Ce pipeline personnalisé est déployé avec l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et servira de pipeline de réception lors de la configuration de l'adaptateur WCF-WebHttp.  
  
 Avant d'effectuer les étapes de cette procédure, assurez-vous que [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] est installé et configuré sur l'ordinateur où vous créez cette application.  
  
#### <a name="to-add-a-custom-pipeline"></a>Pour ajouter un pipeline personnalisé  
  
1.  Dans le **BtsSalesforceIntegration** solution, créer un nouveau [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] projet. Nommez le projet `CustomPipeline`.  
  
2.  Dans le **CustomPipeline** de projet, ajoutez un nouveau pipeline de réception. Nommez le pipeline en tant que `AddNamespace.btp`.  
  
3.  Dans le **Decode** étape du pipeline, à partir de la boîte à outils, faites glisser et déposez le **Namespace ajouter d’ESB** composant de pipeline. Dans le **désassembler** à l’étape, faites glisser le **désassembleur XML** composant de pipeline.  
  
    > [!NOTE]
    >  Si le **Namespace ajouter d’ESB** composant de pipeline n’est pas répertorié dans la boîte à outils, vous pouvez l’ajouter. Cliquez sur le **composants de Pipeline BizTalk** onglet, puis cliquez sur **choisir des éléments de**. Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** , sélectionnez la case à cocher **Namespace ajouter d’ESB** composant, puis cliquez sur **OK**.  
  
4.  Ajoutez un fichier de clé de nom fort pour le projet et enregistrez le projet.  
  
5.  Cliquez sur le **CustomPipeline** de projet et sélectionnez **propriétés**. Dans le **déploiement** onglet, pour **nom de l’Application**, entrez `SalesforceIntegration`.  
  
6.  Enregistrez les modifications apportées au projet.  
  
 Dans cette rubrique, vous avez ajouté un comportement personnalisé pour vous authentifier auprès de Salesforce et un pipeline personnalisé pour ajouter un espace de noms à la réponse de Salesforce. Nous allons utiliser ces composants personnalisés lors de la configuration de ports physiques dans la console d'administration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer la solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)