---
title: "Recommandées de développement à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea3a13b-e41f-4920-bf0d-26f7bb145aa3
caps.latest.revision: "28"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9786896a4a5983a438dd855dcc858ba4485cbc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="development-best-practices-using-the-wcf-lob-adapter-sdk"></a>Recommandées de développement à l’aide de WCF LOB Adapter SDK
Vous pouvez utiliser les meilleures pratiques dans cette rubrique afin d’améliorer vos applications et les cartes.  
  
## <a name="call-abort-before-close-on-channel-exception"></a>Abandon de l’appel avant de fermer sur l’Exception de canal  
 Lorsque vous écrivez une application qui utilise le modèle de canal WCF, vous devez appeler `IRequestChannel.Abort` avant d’appeler `ChannelFactory.Close`. Si vous ne le faites pas, `ChannelFactory.Close` lève une exception.  
  
 Dans l’exemple suivant, les opérations de canal sont tentées dans un bloc try/catch. Si une exception se produit, le canal est abandonné.  
  
```csharp  
ChannelFactory<IRequestChannel> cf = new  ChannelFactory<IRequestChannel>();  
IRequestChannel channel = null;  
try  
{  
  cf.Open();  
  channel = cf.CreateChannel();  
  channel.Open();  
  channel.Request();// This causes the channel to go into a faulted state.  
  channel.Close();  
}  
catch (Exception e)  
{  
  // Abort the channel if we have one  
  if(channel != null)  
    channel.Abort();  
}  
finally  
{  
  if (cf.State == CommunicationState.Opened)  
  {  
    cf.Close(); // It throws an exception that the channel is in a faulted state.  
  }  
}  
```  
  
## <a name="implement-both-asynchronous-and-synchronous-handlers"></a>Implémenter des gestionnaires asynchrones ou synchrones  
 Si possible, implémentez les gestionnaires asynchrones ou synchrones dans votre carte. Si votre adaptateur implémente uniquement les appels synchrones, vous risquez de rencontrer des problèmes de blocage lors du traitement d’un volume important de messages ou lorsque l’adaptateur est utilisé dans un environnement multithread.  
  
## <a name="use-connection-pooling"></a>Utiliser le regroupement de connexions  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] prend en charge le regroupement de connexions par défaut. Toutefois, c’est au développeur d’adaptateur pour déterminer les propriétés à exposer en tant que la liaison des propriétés de regroupement de connexions. Les paramètres de Pool de connexions disponibles sont définies dans `Microsoft.ServiceModel.Channels.Common.ConnectionPoolSettings`.  
  
 Il n’existe aucune option dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] exposer facilement ces propriétés en tant que propriétés de connexion de l’adaptateur. Le développeur d’adaptateur doit définir manuellement les propriétés dans l’implémentation de l’adaptateur.  
  
```csharp  
public CustomAdapter(): base()  
{  
   this.Settings.ConnectionPool.EnablePooling = true;  
   this.Settings.ConnectionPool.HandlersShareSameConnection = true;  
   this.Settings.ConnectionPool.MaxConnectionsPerSystem = 50;  
   this.Settings.ConnectionPool.MaxAvailableConnections = 5;  
}  
```  
  
## <a name="ensure-that-the-adapter-supports-two-way-operations"></a>Assurez-vous que l’adaptateur prend en charge les opérations bidirectionnelles  
 Si votre carte est appelée à partir de BizTalk Server, il doit prendre en charge les opérations bidirectionnelles, même si la valeur de retour est void. Cela est, car BizTalk Server attend une réponse retournée à partir de n’importe quel demande sortante et lève une exception si votre adaptateur implémente uniquement les opérations unidirectionnelles.  
  
 Voici un exemple d’un contrat demande-réponse qui retourne void.  
  
```csharp  
[ServiceContract(Namespace=”Http:Microsoft.BizTalk.Samples.WCFAdapterSample”)]  
public interface ICalculator  
{  
   [OperationContract]  
   void Add(double n1, double n2);  
}  
```  
  
## <a name="implement-tracing"></a>Implémenter le suivi  
 Au cours du cycle de développement, il ne semble pas important d’ajouter le suivi à votre carte, étant donné que vous pouvez parcourir le code et déboguer les problèmes. Toutefois, une fois que l’adaptateur est installé dans un environnement de production, vous peut-être pas en mesure d’utiliser le débogage du runtime pour isoler les problèmes. Si vous avez activé le suivi dans l’ensemble de votre adaptateur, il peut être utilisé pour isoler où des échecs sont produisent.  
  
 Consultez [Trace une carte avec WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/trace-an-adapter-with-the-wcf-lob-adapter-sdk.md) pour plus d’informations.  
  
## <a name="use-uri-properties-for-frequently-changed-settings"></a>Utiliser les propriétés de l’URI pour les paramètres modifiés fréquemment  
 Lorsque vous décidez d’exposer une propriété personnalisée en tant qu’une liaison ou une propriété URI, il est recommandé d’utiliser une propriété URI si la valeur change souvent. Propriétés de liaison doivent être réservée pour les valeurs qui changent rarement.  
  
 Un exemple de propriété de liaison est un nom de serveur de base de données qui est utilisé par toutes les connexions. Un exemple de propriété URI serait une table spécifique ou une procédure stockée à utiliser par cette connexion spécifique.  
  
## <a name="do-not-pass-user-name-or-password-values-in-the-uri"></a>Ne passez pas de nom d’utilisateur ou des valeurs de mot de passe dans l’URI  
 Si votre adaptateur requiert des informations d’identification de l’appelant, il est recommandé d’utiliser le **ClientCredentials** classe pour récupérer les informations d’identification des valeurs au lieu de passer les informations d’identification du client dans le cadre de l’URI. Le **ClientCredentials** classe est une fonctionnalité standard de WCF est conçu pour passer des informations d’identification à partir du client au service de manière plus sécurisée. En transmettant les informations utilisateur dans la chaîne d’URI peut exposer les informations utilisateur lors de leur transit.  
  
 Les méthodes recommandées de passer les informations d’identification sont affichés dans le tableau suivant.  
  
|Méthode| Description|  
|------------|-----------------|  
|Moment du design|Lorsque vous utilisez la [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous pouvez spécifier les types d’informations d’identification du client qui prend en charge de la carte.|  
|Durée d’exécution|Lorsque vous utilisez un proxy .NET CLR généré, vous pouvez définir par programme le client informations d’identification.<br /><br /> `static void Main(string[] args) {    EchoServiceClient client = new EchoServiceClient();    client.ClientCredentials.UserName.UserName = "TestUser";    client.ClientCredentials.UserName.Password = "TestPassword";    string response=client.EchoString("Test String"); }`<br /><br /> Si vous avez besoin d’interagir directement avec le canal, vous pouvez également utiliser le modèle de canal WCF pour spécifier les informations d’identification du client lors de la création d’une fabrique de canaux.<br /><br /> `EchoAdapterBinding binding = new EchoAdapterBinding(); binding.Count = 3; ClientCredentials clientCredentials = new ClientCredentials(); clientCredentials.UserName.UserName = "TestUser"; clientCredentials.UserName.Password = "TestPassword"; BindingParameterCollection bindingParms = new BindingParameterCollection(); bindingParms.Add(clientCredentials); EndpointAddress address = new EndpointAddress("echo://"); IChannelFactory<IRequestChannel> requestChannelFactory = binding.BuildChannelFactory<IRequestChannel>(bindingParms); requestChannelFactory.Open();`|  
|Configuration WCF|Dans le fichier de configuration client, ajoutez une \<endpointBehaviors > élément inclut \<clientCredentials >.<br /><br /> `<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">       <system.serviceModel>           . . . . .           <behaviors>             <endpointBehaviors>               <behavior name="clientEndpointCredential">                 <clientCredentials>                   <windows allowNtlm="false" allowedImpersonationLevel="Delegation" />                    </clientCredentials>               </behavior>             </endpointBehaviors>           </behaviors>       </system.serviceModel>   </configuration>`|  
|À l’aide de BizTalk|Lorsque vous utilisez l’adaptateur WCF pour consommer votre carte, vous pouvez ajouter la **clientCredentials** extension de comportement sur le **comportement** onglet. Une fois qu’il a été ajouté, vous pouvez définir des informations d’identification du client souhaité dans le comportement de point de terminaison.|  
  
## <a name="do-not-return-both-strongdatasettype-and-weakdatasettype"></a>Ne retournent pas les deux StrongDataSetType et WeakDataSetType  
 Si votre adaptateur renvoie un `DataSet`, utilisez `Microsoft.ServiceModel.Channels.Common.QualifiedType.StrongDataSetType%2A` ou `Microsoft.ServiceModel.Channels.Common.QualifiedType.WeakDataSetType%2A`, mais n’utilisent pas les deux en même temps. Le nom du nœud racine et espace de noms généré par les deux types sont identiques et ne peut pas exister simultanément dans un WSDL.  
  
 Alors que `WeakDataSetType` et `StrongDataSetType` tous deux représentent un `System.Data.DataSet`, `StrongDataSetType` est plus facile à utiliser dans les applications .NET, étant donné que le proxy généré apparaît sous la forme `System.Data.Dataset`. Le proxy généré par `WeakDataSetType` est `XmlElement[]`, qui est plus difficile à utiliser dans une application .NET.  BizTalk Server ne peut pas utiliser le schéma retourné de `StrongDataSet`, mais est en mesure de consommer `WeakDataSetType`.  
  
> [!NOTE]
>  `StrongDataSetType`et `WeakDataSetType` uniquement contrôler comment l’application client interprète les messages XML transmis par l’adaptateur. Le message XML est le même quel type est spécifié.  
  
> [!NOTE]
>  Lors du retour `StrongDataSetType`, vous devez définir `Microsoft.ServiceModel.Channels.Common.MetadataSettings.CompileWsdl%2A` à `false`. Lorsque la valeur `true`, la valeur par défaut, `XmlSchemaSet::Compile` est appelée au sein de l’adaptateur pour vous assurer qu’aucune erreur dans le WSDL, cependant le schéma produit par `StrongDataSetType` génère une exception dans `XmlSchemaSet`.  
>   
>  Paramètre `CompileWsdl` à `false` ignore la validation de schéma WSDL au sein de l’adaptateur et la validation se produit pendant la génération du proxy.  Utilitaires, tels que svcutil.exe sont en mesure de générer un proxy pour les deux `StrongDataSetType` et `WeakDataSetType`.  
  
 Pour travailler avec les environnements BizTalk et .NET, envisagez d’implémenter une propriété de liaison qui permet de basculer entre les deux types de retournés, comme stipulé par l’environnement.  
  
```csharp  
internal static QualifiedType GetDataSetQualifiedType(MyAdapterBindingProperties bindingProperties)  
{  
   if (bindingProperties.EnableBizTalkCompatibility)  
      return QualifiedType.WeakDataSetType;  
   else  
      return QualifiedType.StrongDataSetType;  
}  
```  
  
## <a name="create-meaningful-xsd-schema-names-in-biztalk-server"></a>Créer des noms de schéma XSD significatives dans BizTalk Server  
 Lors de l’utilisation du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] outil de conception, le nom du schéma XSD généré dans votre projet BizTalk est créé à l’aide de la `DefaultXsdFileNamePrefix` propriété, le `fileNameHint` annotation dans le WSDL et, si nécessaire, une valeur d’entier unique.  
  
 Par exemple, si `DefaultXsdFileNamePrefix` est défini sur « MyAdapter » et le `fileNameHint` annotation est définie sur « Stream », le schéma XSD créé est nommé MyAdapterStream.xsd.  
  
```  
\<xs:schema elementFormDefault='qualified' targetNamespace='http://schemas.microsoft.com/Message' xmlns:xs='http://www.w3.org/2001/XMLSchema' xmlns:tns='http://schemas.microsoft.com/Message'>  
\<xs:annotation>  
\<xs:appinfo>  
\<fileNameHint xmlns='http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd'>Stream</fileNameHint>  
\</xs:appinfo>  
\</xs:annotation>  
\<xs:simpleType name='StreamBody'>  
\<xs:restriction base='xs:base64Binary' />  
\</xs:simpleType>  
\</xs:schema>  
  
```  
  
> [!NOTE]
>  La valeur par défaut de `DefaultXsdFileNamePrefix` est le nom de votre liaison. Pour spécifier une valeur différente, substituez `DefaultXsdFileNamePrefix` dans votre classe d’adaptateur qui est dérivé de `Microsoft.ServiceModel.Channels.Common.AdapterBinding`.  
  
 Il existe deux méthodes pour ajouter la `fileNameHint` annotation au schéma : remplacer l’exportation... Méthodes de schéma sur OperationMetadata\TypeMetadata ou remplacer l’implémentation de IWsdlRetrieval de la carte. Soit la méthode, vous pouvez appeler l’implémentation de base, puis ajoutez l’annotation pour les schémas dans la collection de schémas.  
  
> [!NOTE]
>  Lors de la substitution de l’exportation... Méthodes de schéma, il peut y avoir plusieurs définitions de type d’opération dans le même schéma. l’adaptateur doit vous assurer que plusieurs occurrences de la `fileNameHints` annotation dans le même schéma éviter les conflits. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] utilise la première occurrence de `fileNameHint` si elle apparaît plusieurs fois dans un schéma.  
  
 Dans l’exemple suivant, IWsdlRetrieval est utilisé pour ajouter le `fileNameHint` annotation au service WSDL.  
  
```csharp  
sealed class MyAdapterWsdlRetrieval : IWsdlRetrieval  
{  
   IWsdlRetrieval mBaseWsdlRetrieval;  
   public MyAdapterWsdlRetrieval(IWsdlRetrieval baseWsdlRetrieval)  
   {  
      mBaseWsdlRetrieval = baseWsdlRetrieval;  
   }  
  
   ServiceDescription IWsdlRetrieval.GetWsdl(Microsoft.ServiceModel.Channels.MetadataRetrievalNode[] nodes, Uri uri, TimeSpan timeout)  
   {  
      ServiceDescription baseDesc = mBaseWsdlRetrieval.GetWsdl(nodes, uri, timeout);  
      foreach (XmlSchema schema in baseDesc.Types.Schemas)  
      {  
         CreateFileNameHint(schema);  
      }  
      return baseDesc;  
   }  
  
   void CreateFileNameHint(XmlSchema schema)  
   {  
      string targetNamespace = schema.TargetNamespace;  
      if (string.IsNullOrEmpty(targetNamespace))  
         return;  
      string fileNameHint = null;  
      //determine the filename based on namespace  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadaptpter/HelloWorld"))  
      {  
         fileNameHint = "HelloWorld";  
      }  
      if (targetNamespace.StartsWith("myadapter:// adapters.samples.myadapter/Hello"))  
      {  
         fileNameHint = "Hello";  
      }  
      //create the annotation and populate it with fileNameHint  
      XmlSchemaAnnotation annotation = new XmlSchemaAnnotation();  
      XmlSchemaAppInfo appInfo = new XmlSchemaAppInfo();  
      XmlDocument doc = new XmlDocument();  
      XmlNode[] fileNameHintNodes = new XmlNode[1];  
      fileNameHintNodes[0] = doc.CreateElement(null, "fileNameHint", "http://schemas.microsoft.com/servicemodel/adapters/metadata/xsd");  
      fileNameHintNodes[0].AppendChild(doc.CreateTextNode(fileNameHint));  
      appInfo.Markup = fileNameHintNodes;  
      annotation.Items.Add(appInfo);  
      schema.Items.Insert(0, annotation);  
   }  
```  
  
## <a name="do-not-modify-adapterenvironmentsettings-during-processing"></a>Ne modifiez pas AdapterEnvironmentSettings lors du traitement  
 L’adaptateur doit uniquement définir le **AdapterEnvironmentSettings**, **ConnectionPoolManager**, **ConnectionPool**, et **CommonCacheSize**lors de l’initialisation de carte et ne doit pas tenter de modifier les valeurs pour une instance en cours d’exécution.  
  
 Si ces paramètres sont modifiées sur une instance de la carte en cours d’exécution, cela peut entraîner de nouvelles connexions remplacement des paramètres de configuration pour les connexions en cours d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Recommandées de développement à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)