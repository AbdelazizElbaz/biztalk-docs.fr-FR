---
title: "Héberger un adaptateur dans IIS à l’aide de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90b6cd97-01b3-4c98-a190-c6e0ccf24d2b
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77750a3ae6232b842961b83d3b672d2bbb084a73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="host-an-adapter-in-iis-using-the-wcf-lob-adapter-sdk"></a>Héberger un adaptateur dans IIS à l’aide de WCF LOB Adapter SDK
Cette section contient des informations sur l’hébergement d’un adaptateur créé à l’aide de la [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] dans Internet Information Services (IIS). Pour plus d’informations sur les autres options d’hébergement, consultez [Services d’hébergement](https://msdn.microsoft.com/library/ms730158.aspx).
  
## <a name="use-iis-and-aspnet"></a>Utilisez les services IIS et ASP.NET
 Vous pouvez utiliser IIS avec ASP.NET activé pour la publication des cartes créées avec WCF LOB Adapter SDK. Pour héberger un adaptateur créé par le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous configurez Internet Information Services (IIS) pour la publication de services WCF. Ensuite, envisagez l’utilisation de votre adapterwith WCF ASP.NET.
 
 Lorsque vous hébergez un service WCF dans IIS, il existe deux modes d’hébergement disponibles : **côte-à-côte** et**le mode de compatibilité ASP.NET**. La valeur par défaut en mode d’hébergement est côte-à-côte. Mode côte-à se comporte de manière cohérente avec d’autres solutions d’hébergement de WCF. Par conséquent, un service WCF hébergé dans IIS comporte comme un hébergé dans une application console. Toutefois, cela peut être pas souhaitable, car les développeurs web peuvent attendre comportement similaire à ASP.NET. Par exemple, dans le mode côte à côte, WCF n’est pas conforme à toutes les règles d’autorisation basée sur l’URL spécifiées dans le `<system.web> <authorization>` élément de configuration du fichier web.config.  
  
 Mode de compatibilité ASP.NET autorise le service WCF pour utiliser toutes les fonctionnalités d’ASP.NET et se comportent comme une page ASPX. Toutefois, vous devez prendre des étapes supplémentaires lors de la création de votre adaptateur WCF pour activer cette fonctionnalité. Pour plus d'informations, consultez : 
 
 [Services WCF et ASP.NET](https://msdn.microsoft.com/library/aa702682.aspx)
 
[Hébergement dans Internet Information Services](https://msdn.microsoft.com/library/ms734710.aspx)

[Hébergement de Services WCF](https://msdn.microsoft.com/library/ms730158.aspx)

## <a name="use-the-wcf-adapter-service-development-wizard"></a>Utilisez l’Assistant développement d’adaptateurs WCF

Utilisez le [!INCLUDE[afsvcdevwizlong](../../includes/afsvcdevwizlong-md.md)] pour automatiser la création d’un projet Web pour l’hébergement de votre adaptateur dans Internet Information Services (IIS). L’adaptateur hébergé peut ensuite être consommé par les clients à l’aide de Windows Communication Framework (WCF) ou des services Web.  
  
### <a name="publish-an-adapter-as-a-wcf-service-hosted-in-iis"></a>Publier un adaptateur sous la forme d’un service WCF hébergé dans IIS  
  
1.  Ouvrez [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)]. Sur le **fichier** menu, sélectionnez **nouveau**, puis sélectionnez **Site Web**.  
  
2.  Dans **modèles**, sélectionnez **Visual C#**, puis sélectionnez **Service d’adaptateur WCF**.  
  
3.  Entrez le dossier pour enregistrer la solution, puis sélectionnez **OK**. Le **Assistant développement d’adaptateurs WCF** démarre.  
  
4.  Sur le **Introduction** , cliquez sur **suivant**.  
  
5.  Sur le **choisissez les opérations** , spécifiez la liaison, contrat et les opérations à utiliser pour ce service hébergé.  
  
    1.  Dans le **sélectionner une liaison** , sélectionnez la liaison de la carte à utiliser, puis cliquez sur **configurer**. Cela permet d’afficher le **configurer l’adaptateur** boîte de dialogue. Indiquez les valeurs nécessaires pour invoquer l’adaptateur et pour récupérer les métadonnées de l’opération.  
  
    2.  Sur le **sécurité** onglet, sélectionnez le **type d’informations d’identification du Client** à utiliser lors du passage d’informations d’identification du client à l’adaptateur.  
  
        |Type d'informations d'identification| Description|  
        |---------------------|-----------------|  
        |**Aucun**|Le client n’a pas besoin de présenter des informations d’identification.|  
        |**Windows**|Le client utilisera les informations d’identification Windows.|  
        |**Nom d’utilisateur**|Le client fournit un nom d’utilisateur et un mot de passe.|  
        |**Certificat**|Le client est authentifié à l’aide d’un certificat X.509. Si cette valeur est définie, cliquez sur **Parcourir** dans les **certificat Client** zone, puis sélectionnez le certificat à utiliser.|  
  
    3.  Sur le **propriétés URI** onglet, spécifiez les paramètres d’URI requis par l’adaptateur. Les entrées affichées sous cet onglet varient selon les propriétés exposées dans la `ConnectionUri Properties` classe de l’adaptateur.  
  
    4.  Sur le **propriétés de liaison** onglet, spécifiez des valeurs pour les propriétés de liaison requises pour l’adaptateur. Le **général** section contient des paramètres communs tels que des valeurs de délai d’attente. Propriétés supplémentaires sont répertoriées selon les propriétés personnalisées exposées dans votre `AdapterBinding` classe.  
  
6.  Une fois que vous avez spécifié les valeurs de configuration, cliquez sur **connexion**.  
  
    1.  À partir de la **type de contrat Select** , sélectionnez le contrat à utiliser. Cette opération remplit le **sélectionner une catégorie** arborescence contrôle avec une liste de catégories et opérations disponibles à partir de cet adaptateur. Si l’adaptateur implémente les fonctionnalités de recherche via un `MetadataRetrievalClient` (classe), vous pouvez entrer un terme à rechercher dans le **recherche dans la catégorie** champ pour retourner uniquement les catégories et les opérations qui contiennent le terme de recherche.  
  
        > [!NOTE]
        >  Seules les opérations sortantes sont disponibles pour la sélection.  
  
    2.  À partir de la **catégories et opérations disponibles** , sélectionnez les éléments à ajouter, puis cliquez sur **ajouter**. Une fois que vous avez ajouté les éléments souhaités, cliquez sur **suivant**.  
  
7.  Sur le **configurer le Service et les comportements de point de terminaison** , définissez les comportements souhaités pour cet adaptateur.  
  
    1.  Le **Configuration de comportement de Service** section contient des entrées qui contrôlent le comportement de service. Après avoir exécuté l’Assistant, vous pouvez modifier les comportements de service sélectionné en modifiant le fichier web.config.  
  
        |Propriété| Description|  
        |--------------|-----------------|  
        |**EnableMetadataExchange**|La valeur **True** permet aux services de publication des métadonnées aux demandes du client. Cela peut également être définie en modifiant \< **serviceMetadata httpGetEnabled = » «**> dans le fichier web.config. Valeur par défaut est **False**|  
        |**IncludeExceptionDetailsinFault**|La valeur **True** entraîne des informations d’exception gérées retourné au client dans les erreurs SOAP. Cela peut également être définie en modifiant \< **serviceDebug usingincludeExceptionDetailInFaults = » «**> dans le fichier web.config. Valeur par défaut est **False**.|  
        |**Nom**|Nom de la configuration de comportement de service.|  
        |**UseServiceCertificate**|Cette valeur détermine si le service utilise un certificat X.509 pour s’authentifier auprès du processus client. Valeur par défaut est **True**.|  
        |**FindValue**|Cette valeur est utilisée pour rechercher un certificat X.509 spécifique dans le magasin de certificats. Cela peut également être définie en modifiant \< **serviceCredentials findValue = » «**> dans le fichier web.config **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** est définie sur **True**.|  
        |**StoreLocation**|Cette valeur spécifie l’emplacement du magasin système pour rechercher le certificat spécifié. Cela peut également être définie en modifiant \< **serviceCredentials storeLocation = » «**> dans le fichier web.config. **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** a la valeur **True**.|  
        |**StoreName**|Cette valeur spécifie le magasin système spécifique pour rechercher le certificat spécifié. Cela peut également être définie en modifiant \< **serviceCredentials storeName = » «**> dans le fichier web.config **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate** est définie sur **True**.|  
        |**X509FindType**|Le type de recherche à utiliser avec le FindValue spécifié précédemment afin de trouver le certificat spécifique à utiliser. Cela peut également être définie en modifiant \< **serviceCredentials x509FindType = » «**> dans le fichier web.config **Remarque :** spécifier une valeur pour cette propriété uniquement si **UseServiceCertificate**  a la valeur **True**.|  
  
    2.  Le **Configuration de comportement de point de terminaison** section contrôle le comportement de point de terminaison.  
  
        |Propriété| Description|  
        |--------------|-----------------|  
        |**Nom**|Le nom du comportement de point de terminaison|  
        |**AuthenticationType**|Cette valeur indique à la carte où obtenir le client les informations d’identification du document entrant. Pour activer les clients à spécifier un certificat client pour s’authentifier auprès du service, affectez la valeur **ClientCredentialUsernamePassword**. Pour activer les clients à spécifier le nom d’utilisateur et un mot de passe dans le cadre de l’en-tête HTTP, affectez la valeur **HTTPUsernamePassword**. Pour activer les clients à spécifier les informations d’identification via l’interface ClientCredential, affectez la valeur **automatique**. En cas d’échec, les clients peuvent passer des informations d’identification dans le cadre de l’en-tête HTTP.<br /><br /> Cette valeur peut également être définie en modifiant \< **endpointBehavior adapterSecurityBridgeType**> dans le fichier web.config. Valeur par défaut est **automatique**.|  
        |**UsernameHeader**|Spécifie le nom de l’en-tête qui sera utilisé pour transmettre le nom d’utilisateur pour le service. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour les en-têtes personnalisés HTTP et SOAP » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> Cette valeur peut également être définie en modifiant \< **endpointBehavior usernameHttpHeader**> dans le fichier web.config. **Remarque :** vous devez spécifier une valeur pour cette propriété si le **AuthenticationType** a la valeur **HTTPUserNamePassword**.  Si la valeur **automatique**, cette propriété est facultative.|  
        |**PasswordHeader**|Spécifie le nom de l’en-tête qui sera utilisé pour passer le mot de passe pour le service. Pour plus d’informations sur les en-têtes HTTP, consultez « Prise en charge pour HTTP et SOAP en-têtes personnalisés » à [http://go.microsoft.com/fwlink/?LinkId=106692](http://go.microsoft.com/fwlink/?LinkId=106692)<br /><br /> Cette valeur peut également être définie en modifiant <**endpointBehavior passwordHttpHeader**< dans le fichier web.config. **Remarque :** vous devez spécifier une valeur pour cette propriété si le **AuthenticationType** a la valeur **HTTPUserNamePassword**. Si la valeur **automatique**, cette propriété est facultative.|  
  
    3.  Après avoir défini le comportement souhaité, cliquez sur **suivant** pour continuer.  
  
8.  Sur le **configurer une liaison de point de terminaison de Service et l’adresse** page, vous pouvez configurer les propriétés de liaison et une adresse pour les contrats. Sélectionnez le contrat dans le **sélectionner un contrat pour configurer** liste, puis entrez les valeurs souhaitées dans les **configurer l’adresse et la liaison pour le contrat** boîte de dialogue.  
  
    1.  Sélectionnez le **BindingConfiguration** entrée sous propriétés de liaison. L’Assistant prend uniquement en charge liaison HTTP de base pour le champ de configuration de liaison est automatiquement défini sur **System.ServiceModel.Configuration.BasicHttpBindingElement**. Pour modifier les propriétés de configuration pour cette liaison, cliquez sur le bouton de sélection **...** . Pour utiliser un canal de communication sécurisé, vous devez toujours définir la **Mode** propriété **Transport**. Ceci est la valeur par défaut.  
  
    2.  Sélectionnez le **EndpointName**, puis entrez le nom souhaité du point de terminaison.  
  
    3.  Pour appliquer vos modifications, cliquez sur **appliquer**.  
  
9. Pour continuer, cliquez sur **Suivant**. La page Résumé répertorie une arborescence des opérations de carte qui a été sélectionné.  
  
10. Passez en revue le résumé, puis cliquez sur **Terminer**.  
  
11. L’Assistant crée un projet Web et ajoute les fichiers suivants.  
  
    |Fichier| Description|  
    |----------|-----------------|  
    |.svc|Fichier de service qui fait référence au proxy WCF.|  
    |.cs|Implémente le proxy WCF.|  
    |web.config|Contient \< **point de terminaison**>, \< **liaisons**>, et \< **comportements**> éléments pour \< **système. ServiceModel**>|  
  
12. Publiez le projet de service WCF.  
  
    1.  Cliquez sur le projet dans l’Explorateur de solutions, puis cliquez sur **publier**.  
  
    2.  Dans le **publier le Site Web** boîte de dialogue, spécifiez l’URL cible pour le service WCF.  
  
    3.  Sélectionnez **autoriser ce site précompilé à être mis à jour**.  
  
    4.  Sélectionnez **utiliser fixe pour les assemblys d’affectation de noms et une page**.  
  
    5.  Sélectionnez **activer de noms forts sur les assemblys précompilés**, puis spécifiez la clé de signature à utiliser.  
  
13. Pour publier le site Web, cliquez sur **OK**.  
  
14. Vérifiez que le service est publié avec succès.  
  
    1.  Démarrez la Console de gestion IIS.  Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Internet Information Services**.  
  
    2.  Accédez au nœud sur lequel vous avez publié le service.  Si le service a été publié en tant que http://localhost/myservice, accédez à **Internet Information Services**> **nom de l’ordinateur**> **Web Sites** >  **Site Web par défaut**> **myservice**.  
  
    3.  Dans le volet droit, cliquez sur le fichier .svc, puis cliquez sur **Parcourir**. La page Web affiche des informations sur le service. Vous pouvez désormais utiliser ce service en utilisant des appels de service Web ou WCF à partir d’applications clientes. 

## <a name="security"></a>Sécurité
Lorsque l’adaptateur est hébergé dans un service, appels à partir d’applications clientes utilisent le pont de sécurité de carte pour passer des informations d’identification du client à l’adaptateur.  
  
 Lorsqu’un client WCF envoie l’authentification à un service WCF, normalement le service utilise l’authentification. Toutefois, dans le cas d’un adaptateur, l’idée est pour capturer les informations d’authentification pour une utilisation avec le système métier sous-jacent. Cela est implémenté via le pont de sécurité de carte, qui est présenté comme un comportement de point de terminaison. En tant que développeur d’adaptateur, il n’y a rien qui doit être implémentée pour tirer parti de cette fonctionnalité ; Toutefois, lors du déploiement de la carte, vous devez considérer comment le client va fournir des informations d’identification pour le service.  
  
 Si vous utilisez la sécurité au niveau du message, le pont de sécurité de l’adaptateur peut récupérer l’élément ClientCredentials envoyé par l’application cliente sur n’importe quelle liaison. Si vous utilisez une liaison HTTP de base, vous pouvez sélectionner à la place un en-tête personnalisé permet de passer les informations de nom et mot de passe utilisateur. Il est recommandé d’utiliser la classe ClientCredential fournie par WCF pour passer des informations d’identification, mais de nombreuses applications clientes de Service Web devez utiliser un en-tête personnalisé pour passer des informations d’identification.  
  
 Voici un exemple de configuration dans lesquels l’adaptateur recherche les informations d’identification dans l’élément ClientCredentials qui fournit de l’application cliente. Si aucun n’est trouvé, l’adaptateur recherche ensuite dans les en-têtes de demande HTTP qui sont spécifiés.  
  
```  
<endpointBehaviors>  
   <behavior name="customEndpointBehavior">  
      <endpointBehavior usernameHttpHeader="UNHdr" passwordHttpHeader="PWHdr"  
         adapterSecurityBridgeType="Auto" />  
    </behavior>  
</endpointBehaviors>  
```      
  
## <a name="see-also"></a>Voir aussi  
 [Activités de développement](../../esb-toolkit/development-activities.md)