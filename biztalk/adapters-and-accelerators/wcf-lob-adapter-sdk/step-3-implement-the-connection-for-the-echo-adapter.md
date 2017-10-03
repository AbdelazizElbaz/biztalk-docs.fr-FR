---
title: "Étape 3 : Implémenter la connexion de l’adaptateur d’écho | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc223901-3ad3-4e71-8672-fea6bb4efe65
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a735654fd03f5efb39fe73eb845f4db3632d283
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-implement-the-connection-for-the-echo-adapter"></a>Étape 3 : Implémenter la connexion de l’adaptateur d’écho
![Étape 3 de 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-3of9.gif "Step_3of9")  
  
 **Durée :** 45 minutes  
  
 Dans cette étape, vous implémentez la capacité de connexion de la carte de l’écho. Conformément à la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez implémenter la classe abstraite suivant et les interfaces lors de la connexion au système cible.  
  
-   `Microsoft.ServiceModel.Channels.Common.ConnectionUri`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnection`  
  
-   `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`  
  
 Au lieu de dériver à partir de la liste ci-dessus abstraite des classes et interfaces, les [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère automatiquement les trois classes dérivées, EchoAdapterConnection, EchoAdapterConnectionUri et EchoAdapterConnectionFactory. En plus de la création des classes, chacune dispose d’une méthode par défaut qui lève une exception spécifique, `System.NotImplementedException`.  Cette instruction rappelle au développeur d’implémenter chaque classe.  Lorsque la classe est implémentée, cette instruction de levée d’exceptions doit être supprimée.  
  
 Dans la section suivante, vous mettez à jour ces trois classes pour mieux comprendre comment gérer une connexion, ce qui est la structure de l’URI et comment récupérer par programme des différents éléments de l’URI, puis utilisez ces éléments au sein de la carte.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Avant de commencer cette étape, vous devez avoir terminé avec succès [étape 2 : classer l’adaptateur et les propriétés de connexion](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-2-categorize-the-adapter-and-connection-properties.md). Et vous devez avoir une vision claire de la `Microsoft.ServiceModel.Channels.Common.IConnection`, `Microsoft.ServiceModel.Channels.Common.IConnectionFactory`, et `Microsoft.ServiceModel.Channels.Common.ConnectionUri` classes.  
  
## <a name="connection-related-classes"></a>Classes liées à la connexion  
 Le [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] génère trois classes dérivées, EchoAdapterConnection, EchoAdapterConnectionUri et EchoAdapterConnectionFactory. Les éléments suivants fournissent une vue d’ensemble des méthodes associées à chacun.  
  
### <a name="echoadapterconnection"></a>EchoAdapterConnection  
 Selon la complexité de votre carte, vous devrez peut-être implémenter toutes les cinq méthodes suivantes. Adaptateur d’écho, la plupart n'est pas prises en charge, car l’exemple d’adaptateur Echo n’implique pas de n’importe quel système cible.  
  
|**Méthode**|**Description**|  
|----------------|---------------------|  
|Fermer void publique (délai d’expiration de l’intervalle de temps)|Ferme la connexion au système cible. L’adaptateur d’écho utilise cette méthode pour ajouter uniquement des événements de trace à l’écouteur de trace.|  
|public bool IsValid (délai d’expiration de l’intervalle de temps)|Retourne une valeur qui indique si la connexion est toujours valide.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
|Ouvrez void publique (délai d’expiration de l’intervalle de temps)|Ouvre la connexion au système cible.<br /><br /> Non applicable pour l’adaptateur de l’écho. Toutefois, l’exemple montre comment utiliser un élément d’URI appelé enableAuthentication les utilisateurs à fournir un nom d’utilisateur.|  
|ClearContext() void publique|Efface le contexte de la connexion. Cette méthode est appelée lorsque la connexion est redéfinie pour le pool de connexions.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
|Abort() void publique|Abandonne la connexion au système cible.<br /><br /> Non pris en charge par l’adaptateur de l’écho.|  
  
### <a name="echoadapterconnectionfactory"></a>EchoAdapterConnectionFactory  
 La fabrique de connexion est responsable de la création de la connexion. Par défaut, vous devez modifier cette classe uniquement lors de la connexion à un système cible. Bien que l’adaptateur Echo n’implique pas de n’importe quel système cible, il vous montre comment utiliser un élément URI personnalisé appelé enableAuthentication si votre connexion requiert une authentification utilisateur.  
  
> [!NOTE]
>  L’enableAuthentication n’est pas un mot clé, il est simplement un nom de variable. Par conséquent, vous pouvez choisir n’importe quel nom pour celle-ci.  
  
### <a name="echoadapterconnectionuri"></a>EchoAdapterConnectionUri  
 Cela représente une chaîne de connexion au système cible.  
  
|**Méthode**|**Description**|  
|----------------|---------------------|  
|substitution public Uri Uri|Obtient et définit l’Uri. Obtient générer la chaîne d’Uri et définit pour analyser la chaîne d’Uri.|  
|EchoAdapterConnectionUri() public|Initialise une nouvelle instance de la classe ConnectionUri.|  
|chaîne de substitution public SampleUriString|Retourne EchoAdapter.SCHEME + » : //{hostname}/{application}?enableAuthentication={True &#124; False} ».<br /><br /> Cette chaîne de retour affiche en tant que le **exemple** dans les [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] d’outils, comme indiqué dans l’illustration suivante.|  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4b9d0b8-f07f-4342-815f-9ef1507b0980.gif "e4b9d0b8-f07f-4342-815f-9ef1507b0980")  
  
## <a name="echo-adapter-connection-uri"></a>URI de connexion de l’adaptateur d’écho  
 L’exemple de connexion de l’adaptateur Echo URI se présente comme suit : EchoAapter.SCHEME://{hostname}/{application}?enableAuthentication={true &#124; false}  
  
 Le EchoAapter.SCHEME étant echov2, la connexion est :  
  
 echo2 : / lobhostname/lobapplication ? enableAuthentication = {true &#124; false}  
  
 Vous pouvez lire l’URI de connexion précédente lorsque enableAuthentication = false comme suit :  
  
 À l’aide du schéma de transport echov2, accédez à un ordinateur nommé lobhostname, où une application nommée lobapplication qui ne nécessite pas d’authentification est en attente pour votre connexion.  
  
 Ou bien, lorsque enableAuthentication = true, la connexion comme suite :  
  
 À l’aide du schéma de transport echov2, accédez à un ordinateur nommé lobhostname, où une application nommée lobapplication attend que l’authentification est en attente pour votre connexion. Pour l’adaptateur d’écho uniquement un nom d’utilisateur est requis.  
  
 Avec un URI défini, vous pouvez par programmation consommer et analyser pour la connectivité et de configuration. Si la connexion nécessite des données sensibles telles qu’un nom d’utilisateur et un mot de passe, ne contiennent pas ces informations dans l’URI. Au lieu de cela, ajoutez ces informations dans le `System.ServiceModel.Description.ClientCredentials` objet. L’exemple de code que vous ajoutez vous montre comment procéder.  
  
 Dans le code suivant, l’adaptateur Echo construit l’URI de deux façons pour vous expliquent comment l’adaptateur peut utiliser différents éléments de l’URI pour modifier la fonctionnalité de l’adaptateur.  
  
 echo2 : / lobhostname/lobapplication ? enableAuthentication = [true &#124; false]  
  
 echo2 : / lobhostname/lobapplication ? enableAuthentication = [true &#124; false] & echoInUpperCase = true  
  
### <a name="retrieving-the-uri-element"></a>La récupération de l’élément URI  
 Vous pouvez analyser chaque élément d’URI dans l’adaptateur d’écho URI echo2 : / lobhostname/lobapplication ? enableAuthentication = false & echoInUpperCase = false.  Les valeurs d’élément URI et les méthodes associées sont répertoriées dans le tableau suivant :  
  
|**Valeur de l’élément URI**|**Méthode**|  
|---------------------------|----------------|  
|lobhostname|`System.Uri.Host%2A`pour récupérer le nom d’hôte|  
|Lobapplication|`System.Uri.AbsolutePath%2A`pour récupérer le nom de l’application cible|  
|enableAuthentation = false|GetQueryStringValue("enableAuthentication")<br /><br /> Utilisez cet élément URI pour valider les informations d’identification utilisateur **Remarque :** GetQueryStringValue est une méthode statique définie dans le`Microsoft.ServiceModel.Channels.Common.ConnectionUri`|  
|echoInUpperValue = false|GetQueryStringValue("echoInUpperValue")<br /><br /> Utilisez cet élément de l’URI à convertir la chaîne entrante en majuscules.|  
  
### <a name="enableauthentication-uri-element"></a>Élément EnableAuthentication URI  
 Votre système cible souvent vous oblige à fournir des informations d’identification du client pour établir une connexion au système cible. Comme indiqué, l’adaptateur Echo n’implique pas de n’importe quel système cible. Bien que sous forme d’exemple, il montre comment utiliser un élément URI personnalisé appelé enableAuthentication pour fournir les informations d’identification.  
  
```  
 public class EchoAdapterConnection : IConnection   
{  
….  
   public void Open(TimeSpan timeout)  
  {  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
  }  
}  
```  
  
 Le code vérifie si enableAuthentication a la valeur true et si un nom d’utilisateur n’est pas fourni ; Si un nom d’utilisateur n’est pas fourni, il lève une exception, qui est interceptée par le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, comme indiqué ci-dessous :  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/901095c7-c70d-491a-a1ae-8f37f22a61a7.gif "901095c7-c70d-491a-a1ae-8f37f22a61a7")  
  
 Pour fournir le nom d’utilisateur, vous pouvez l’entrer dans la boîte de dialogue Configurer l’adaptateur dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] outil, tel qu’indiqué dans l’illustration suivante :  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/e4069a7d-1403-4195-b0b5-21ad97dbc3ce.gif "e4069a7d-1403-4195-b0b5-21ad97dbc3ce")  
  
### <a name="echoinuppercase-uri-element"></a>Élément EchoInUpperCase URI  
 L’élément EchoInUpperCase URI peut être référencé comme un indicateur booléen. Si l’indicateur est true, l’adaptateur convertit la chaîne d’entrée de l’opération EchoStrings en majuscules.  
  
 Pour modifier la valeur par défaut de l’élément d’URI echoInUpperCase, utilisez l’onglet Propriétés de l’URI de l’adaptateur à configurer dans le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], comme illustré ci-dessous.  
  
 ![](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/f22511b2-3fca-4875-ac65-8e61f4367e94.gif "f22511b2-3fca-4875-ac65-8e61f4367e94")  
  
## <a name="updating-echoadapterconnection"></a>Mise à jour EchoAdapterConnection  
 Vous implémentez la méthode IsValid, Open et Close de la classe EchoAdapterConnection.  
  
#### <a name="to-update-the-echoadapterconnection-class"></a>Pour mettre à jour de la classe EchoAdapterConnection  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnection.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.  
  
3.  Dans l’éditeur Visual Studio, recherchez le **IsValid** (méthode). À l’intérieur de la **IsValid** méthode, remplacez l’implémentation existante avec celui présenté ci-dessous :  
  
    ```csharp  
    return true;  
    ```  
  
4.  Dans l’éditeur Visual Studio, recherchez le **ouvrir** (méthode). À l’intérieur de la **ouvrir** (méthode), remplacez l’implémentation existante avec l’implémentation suivante. Cet exemple montre comment utiliser l’élément d’enableAuthentication URI pour vérifier le nom d’utilisateur est fourni :  
  
    ```csharp  
    // only validate the credentials if EnableAuthentication  
    // connection property value is true  
    if (this.ConnectionFactory.ConnectionUri.EnableAuthentication)  
    {  
        // this adapter expects a value in username  
        // it just logs the credentials in the trace file  
        if (this.connectionFactory.ClientCredentials != null &&  
            string.IsNullOrEmpty(this.connectionFactory.ClientCredentials.UserName.UserName))  
        {  
            throw new CredentialsException("Username is expected.");  
        }  
        // got the username, log it in trace file  
        EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Username is " + this.connectionFactory.ClientCredentials.UserName.UserName);  
    }  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Open", "Connection successfully established!");  
    ```  
  
5.  Dans l’éditeur Visual Studio, recherchez le **fermer** (méthode). À l’intérieur de la **fermer** (méthode), ajoutez l’instruction suivante :  
  
    ```csharp  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Information, "EchoAdapterConnection::Close", "Connection successfully closed!");  
    ```  
  
## <a name="updating-the-echoadapterconnectionfactory"></a>Mise à jour de la EchoAdapterConnectionFactory  
 Vous implémentez le constructeur de EchoAdapterConnectionFactory et que vous ajoutez deux propriétés appelées ClientCredentials et ConnectionUri.  
  
#### <a name="to-update-the-echoadapterconnectionfactory-class"></a>Pour mettre à jour de la classe EchoAdapterConnectionFactory  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionFactory.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.  
  
3.  Dans l’éditeur Visual Studio, recherchez le **champs privés** région. Ajoutez l’instruction suivante :  
  
    ```csharp  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
     La liste des champs privés doit correspondre à la suivante :  
  
    ```csharp  
    // Stores the client credentials  
    private ClientCredentials clientCredentials;  
    // Stores the adapter class  
    private EchoAdapter adapter;  
    private EchoAdapterConnectionUri connectionUri;  
    ```  
  
4.  Dans l’éditeur Visual Studio, recherchez le **EchoAdapterConnectionFactory** (méthode). À l’intérieur de la **EchoAdapterConnectionFactory** méthode de constructeur, avant «} », ajoutez l’instruction suivante en tant que la dernière instruction.  
  
    ```csharp  
    this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    ```  
  
     L’implémentation de la **EchoAdapterConnectionFactory** (méthode) doit correspondre à ce qui suit :  
  
    ```csharp  
    /// <summary>  
    /// Initializes a new instance of the EchoAdapterConnectionFactory class  
    /// </summary>  
    public EchoAdapterConnectionFactory(ConnectionUri connectionUri  
        , ClientCredentials clientCredentials  
        , EchoAdapter adapter)  
    {  
        this.clientCredentials = clientCredentials;  
        this.adapter = adapter;  
        //added  
        this.connectionUri = connectionUri as EchoAdapterConnectionUri;  
    }  
    ```  
  
5.  Dans l’éditeur Visual Studio, recherchez le **propriétés publiques** région. Ajoutez le code suivant :  
  
    ```csharp  
    /// <summary>  
    /// Returns the client credentials  
    /// </summary>  
    public ClientCredentials ClientCredentials  
    {  
        get  
        {  
            return this.clientCredentials;  
        }  
    }  
  
    /// <summary>  
    /// Returns the Connection Uri for this adapter  
    /// </summary>  
    public EchoAdapterConnectionUri ConnectionUri  
    {  
        get  
        {  
            return this.connectionUri;  
        }  
    }  
    ```  
  
## <a name="updating-the-echoadapterconnectionuri"></a>Mise à jour de la EchoAdapterConnectionUri  
 Vous implémentez le constructeur par défaut de EchoAdapterConnectionUri et EchoAdapterConnectionUri(Uri uri) surchargé constructeur public substituer la propriété Uri de l’Uri.  
  
#### <a name="to-update-the-echoadapterconnectionuri-class"></a>Pour mettre à jour de la classe EchoAdapterConnectionUri  
  
1.  Dans **l’Explorateur de solutions**, double-cliquez sur le **EchoAdapterConnectionUri.cs** fichier.  
  
2.  Dans l’éditeur Visual Studio, avec le bouton droit n’importe où dans l’éditeur, dans le menu contextuel, pointez sur **mode plan**, puis cliquez sur **arrêter le mode plan**.  
  
3.  Dans l’éditeur Visual Studio, recherchez le **constructeurs** région. À l’intérieur de la **EchoAdapterConnectionUri()** un constructeur par défaut, ajoutez l’instruction suivante :  
  
    ```csharp  
    Uri = new Uri("echov2://lobhostname/lobapplication?enableauthentication=False");  
    ```  
  
4.  Dans l’éditeur Visual Studio, à l’intérieur de la **EchoAdapterConnectionUri (Uri uri)** surchargées de constructeur et ajoutez l’instruction suivante :  
  
    ```csharp  
    Uri = uri;  
    ```  
  
     Votre implémentation de la méthode EchoAdapterConnectionUri(Uri uri) doit correspondre à la suivante :  
  
    ```csharp  
    public EchoAdapterConnectionUri(Uri uri)  
        : base()  
    {  
        Uri = uri;  
    }  
    ```  
  
5.  Dans l’éditeur Visual Studio, à l’intérieur de la **public remplacer Uri Uri** (méthode), remplacer l’avec la logique suivante. La méthode get génère l’Uri avec echoInUpperCase ou sans lui. Le jeu d’analyse de l’URI pour récupérer le nom d’hôte, nom de la base de données et valeurs de requête.  
  
    ```csharp  
    get  
    {  
        // Build the uri  
        if (String.IsNullOrEmpty(this.hostname)) throw new InvalidUriException("Invalid target system host name.");  
        if (String.IsNullOrEmpty(this.application)) throw new InvalidUriException("Invalid target system data source name.");  
        if (EchoInUpperCase)  
        {  
            // build the uri with echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication + "&" + "echoInUpperCase=" + echoInUpperCase);  
        }  
        else  
        {  
            // build the uri without echoInUpperCase= query string  
            return new Uri(EchoAdapter.SCHEME + "://" + Hostname + "/" + Application + "?" + "enableAuthentication=" + EnableAuthentication);  
        }  
    }  
    set  
    {  
        // Parse the uri  
        String[] enableAuthValue = GetQueryStringValue(value, "enableAuthentication");  
        if (enableAuthValue.Length > 0) this.enableAuthentication = Boolean.Parse(enableAuthValue[0]);  
        String[] echoInUpperValue = GetQueryStringValue(value, "echoInUpperCase");  
        if (echoInUpperValue.Length > 0) this.echoInUpperCase = Boolean.Parse(echoInUpperValue[0]);  
  
        this.hostname = value.Host;  
        String[] applicationValue = value.AbsolutePath.Split('/');  
        if (applicationValue.Length > 1) this.Application = applicationValue[1];  
    }  
    ```  
  
6.  Dans Visual Studio, sur le **fichier** menu, cliquez sur **Enregistrer tout**.  
  
7.  Dans le menu **Générer** , cliquez sur **Générer la solution**. Vous devez correctement compiler le projet. Dans le cas contraire, vérifiez que vous avez suivi toutes les étapes ci-dessus.  
  
> [!NOTE]
>  Vous avez enregistré votre travail. Vous pouvez en toute sécurité fermer Visual Studio pour l’instant ou accédez à l’étape suivante, [étape 4 : implémenter le Gestionnaire de parcourir des métadonnées de l’adaptateur Echo](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md).  
  
## <a name="what-did-i-just-do"></a>Quoi simplement ?  
 Vous avez implémenté la connexion de l’adaptateur de l’écho. Vous avez appris les composants de connexion de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], la structure de base de l’URI de connexion, comment les éléments de l’URI d’analyser par programme et comment vous pouvez utiliser l’élément URI pour modifier la fonctionnalité de l’adaptateur.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous implémentez l’exploration des métadonnées, la recherche et la résolution de fonctionnalités et l’échange de messages sortants. Enfin, vous générez et déployez l’adaptateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Implémenter le Gestionnaire de recherche de métadonnées de l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-4-implement-the-metadata-browse-handler-for-the-echo-adapter.md)   
 [Didacticiel 1 : Développer l’adaptateur d’écho](../../adapters-and-accelerators/wcf-lob-adapter-sdk/tutorial-1-develop-the-echo-adapter.md)