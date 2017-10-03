---
title: "Création d’un programme de résolution personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d2775460-8e04-40be-9557-8278336b031c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef1d583389189e09a0b9e0e5157ce5466004c03a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-resolver"></a>Création d’un programme de résolution personnalisé
L’implémentation du programme de résolution et l’infrastructure d’adaptateurs fournisseur [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] utilise un composant de pipeline nommé répartiteur et pipelines nommés ItineraryReceive et ItinerarySend.  
  
 Le composant de pipeline de répartiteur possède quatre propriétés : **Validate, Enabled, point de terminaison,** et **MapName**. Le **point de terminaison** propriété peut contenir des chaînes de connexion de programme de résolution avec des valeurs telles que la commande suivante, où **UDDI :\\ \\**  représente le type de résolution à utiliser (la racine moniker).  
  
```  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderPurchaseToOrderPost;serviceProvider=Microsoft.Practices.ESB  
```  
  
 Incluent d’autres prises en charge les monikers **XPATH :\\\\statique :\\\\,** et **BRE :\\\\**. Chaque type de moniker utilise une classe spécifique qui implémente le **IResolveProvider** interface. Vous pouvez créer vos propres programmes de résolution personnalisés pour d’autres types de moniker et les enregistrer pour une utilisation par le système de résolution dynamique.  
  
 Le moniker équivaut à une chaîne de connexion du programme de résolution. Les schémas individuels définissent les paramètres et leur moniker racine. Un programme de résolution prend le résolveur de chaîne de connexion, il valide et utilise le résultat pour interroger et remplir un **dictionnaire** objet qui peut être utilisé pour le routage de la transformation, la sélection d’itinéraire ou d’autres fins spécifiques à votre service.  
  
## <a name="resolver-configuration"></a>Configuration du programme de résolution  
 Vous devez inscrire tous les programmes de résolution dans le fichier de configuration Esb.config. Le code XML suivant montre un exemple du contenu du fichier de configuration.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
     <configSections>  
          <section name="esb" type="Microsoft.Practices.ESB.Configuration.ESBConfigurationSection, Microsoft.Practices.ESB.Configuration, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
          <!-- Other Section Definitions Here -->  
     </configSections>  
  
     <esb>  
          <resolvers cacheManager= "Resolver Providers Cache Manager"  absoluteExpiration="3600">  
               <resolver name="UDDI" type="Microsoft.Practices.ESB.Resolver.UDDI.ResolveProvider, Microsoft.Practices.ESB.Resolver.UDDI, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22">  
                    <resolverConfig>  
                         <add name="cacheTimeoutValue" value="120" />  
                         <add name="cacheName" value="UDDI Cache Manager" />  
                    </resolverConfig>  
               </resolver>  
               <resolver name="XPATH" type="Microsoft.Practices.ESB.Resolver.XPATH.ResolveProvider, Microsoft.Practices.ESB.Resolver.XPATH, Version=2.0.0.0, Culture=neutral, PublicKeyToken=c62dd63c784d6e22"/>  
               <!-- Other Resolver Definitions Here -->  
          </resolvers>  
          <!-- Other ESB Configuration Settings Here -->  
     </esb>  
     <!-- Other Configuration Sections Here -->  
</configuration>  
```  
  
 Le **resolverConfig** section sous chaque nœud du programme de résolution permet de configurer des propriétés supplémentaires pour votre programme de résolution peut nécessiter de fonctionner dans un environnement spécifique. Pour accéder à la configuration, votre programme de résolution doit exposer un constructeur qui prend un paramètre de type **Microsoft.Practices.ESB.Configuration.Resolver**. Dans votre implémentation d’un programme de résolution, propriétés de configuration sont ensuite accessible à l’aide de la **ReadResolverConfigByKey** méthode de la **ResolverConfigHelper** classe ; pour ce faire, passez dans le paramètre initialement passée au constructeur, puis passer le nom de la valeur en question. Si aucune paire nom-valeur n’est spécifiés dans le **resolverConfig** nœud, le constructeur sans paramètre par défaut permet d’instancier votre programme de résolution.  
  
 Deux Universal Description, Discovery and Integration (UDDI) 3 programmes de résolution ont été définies dans la configuration : UDDI 3 et UDDI 3-SOASOFTWARE. Les deux de ces programmes de résolution utilisent le même assembly sous-jacent, mais ils fournissent des configurations différentes pour prendre en charge différents registres 3.0 compatible UDDI avec différents formats d’identificateur de ressource uniforme (URI) et des exigences de sécurité. Si vous avez besoin configurer un moniker supplémentaire pour un Registre compatible 3.0 UDDI en plus de ceux déjà pris en charge, les propriétés suivantes de la configuration peuvent être utilisées :  
  
-   **cacheTimeoutValue**  
  
-   **nom du cache**  
  
-   **publisherKey**  
  
-   **useUddiAuth**  
  
-   **baseUri**  
  
-   **inquireUriSuffix**  
  
-   **securityUriSuffix**  
  
-   **securityMode**. Pour connaître les valeurs valides, consultez l’énumération [System.ServiceModel.BasicHttpSecurityMode](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409) ([http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409](http://go.microsoft.com/fwlink/?LinkID=188284&clcid=0x409)). La valeur par défaut est **TransportCredentialOnly**.  
  
-   **credentialType**. Pour connaître les valeurs valides, consultez l’énumération [System.ServiceModel.HttpClientCredentialType](http://go.microsoft.com/fwlink/?LinkId=188285) ([http://go.microsoft.com/fwlink/?LinkId=188285](http://go.microsoft.com/fwlink/?LinkId=188285)). La valeur par défaut est **Windows**.  
  
-   **nom d’utilisateur**  
  
-   **mot de passe**  
  
 Si vous souhaitez créer un programme de résolution qui s’appuie sur les fonctionnalités d’injection de dépendance du bloc Application Unity, une configuration supplémentaire est requise. Pour plus d’informations, consultez [création d’un programme de résolution personnalisé avec un conteneur Unity](../esb-toolkit/creating-a-custom-resolver-with-a-unity-container.md).  
  
## <a name="the-iresolveprovider-interface"></a>L’Interface IResolveProvider  
 Tous les programmes de résolution doivent implémenter la **IResolveProvider** interface. Le **IResolveProvider** interface, situé dans le projet Microsoft.Practices.ESB.Resolver, se compose de trois surcharges de la **résoudre** méthode qui retourne une instance de la  **Dictionnaire** (classe), qui contient des faits de résolution fournis par l’instance de la classe concrète resolver. L’exemple de code suivant montre la signature de ces surcharges de méthode.  
  
```csharp  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from a Microsoft BizTalk   
// Server pipeline component.  
// </summary>  
// <param name="config">Configuration string entered into   
// pipeline component as argument</param>  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">IBaseMessage passed from pipeline</param>.  
// <param name="pipelineContext">IPipelineContext passed from   
// pipeline</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(string config, string resolver,  
              IBaseMessage message, IPipelineContext pipelineContext);  
  
// <summary>  
// This is the main interface that is called from the ResolverMgr   
// class.  
// This interface supports being called from a Web service interface.  
// </summary>  
// <param name="config">Configuration string entered into Web   
// service as argument</param>.  
// <param name="resolver">Moniker representing the resolver   
// to load</param>.  
// <param name="message">XML document passed from Web   
// service</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string,string> Resolve(string config, string resolver, System.Xml.XmlDocument message);  
  
// <summary>  
// This is the main interface that is called from the   
// ResolverMgr class.  
// This interface supports being called from an orchestration.  
// </summary>  
// <param name="resolverInfo">Configuration string containing   
// configuration and resolver</param>.  
// <param name="message">XLANGMessage passed from   
// orchestration</param>.  
// <returns>Dictionary object fully populated</returns>.  
        Dictionary<string, string> Resolve(ResolverInfo resolverInfo, XLANGs.BaseTypes.XLANGMessage message);  
```  
  
 Le **résolution** structure, situé dans le projet de Microsoft.Practices.ESB.Resolver, définit également les paires nom/valeur stockées dans le **dictionnaire** instance. Le **résolution** structure expose plusieurs propriétés ; le tableau suivant répertorie les plus pertinentes. Le **CreateResolverDictionary** méthode de la **ResolutionHelper** classe peut être utilisée pour générer un dictionnaire de programme de résolution qui contient les clés plus utilisés, avec des valeurs de chaîne vide. Le **dictionnaire** instance prend en charge l’ajout de paires nom/valeur de programme de résolution personnalisé via une implémentation concrète de la **résolveur** classe.  
  
|Propriété|Type de données|Type de données|Type de données|  
|--------------|---------------|---------------|---------------|  
|**TransformType**|Chaîne|**ActionField**|Chaîne|  
|**Réussi**|Booléen|**EpmRRCorrelationTokenField**|Chaîne|  
|**TransportNamespace**|Chaîne|**InboundTransportLocationField**|Chaîne|  
|**Type de transport**|Chaîne|**InterchangeIDField**|Chaîne|  
|**TransportLocation**|Chaîne|**ReceiveLocationNameField**|Chaîne|  
|**Action**|Chaîne|**ReceivePortNameField**|Chaîne|  
|**MessageExchangePattern**|Chaîne|**InboundTransportTypeField**|Chaîne|  
|**EndpointConfig**|Chaîne|**IsRequestResponseField**|Chaîne|  
|**TargetNamespace**|Chaîne|**DocumentSpecStrongNameField**|Chaîne|  
|**FixJaxRPC**|Booléen|**DocumentSpecNameField**|Chaîne|  
|**WindowUserField**|Chaîne|**MessageType**|Chaîne|  
|**CacheTimeout**|Chaîne|**OutboundTransportCLSID**|Chaîne|  
|**MethodNameField**|Chaîne|||  
  
## <a name="creating-a-custom-resolver"></a>Création d’un programme de résolution personnalisé  
 Au moment de l’exécution, un pipeline extrait la chaîne de connexion du programme de résolution et appelle le programme de résolution manager (une instance de la **ResolverMgr** classe). Le Gestionnaire de programme de résolution analyse remplit et valide la chaîne de connexion du programme de résolution. Pour cela, procédez comme suit :  
  
-   Il analyse la chaîne de connexion afin de déterminer les **résolveur** type à charger.  
  
-   Elle correspond à ce type en un moniker défini dans le fichier de configuration (la clé est le moniker racine, tel que UDDI).  
  
-   Il lit le nom de l’assembly du programme de résolution de ce moniker.  
  
-   Il charge l’assembly spécifié.  
  
 Le mécanisme de résolution dynamique met en cache chargé de toutes les implémentations de la **IResolveProvider** interface afin d’éviter les répétées de la lecture des informations de configuration et l’assembly à charger lorsque plusieurs messages entrants utilisent le même programme de résolution.  
  
 Enfin, le Gestionnaire de programme de résolution s’exécute le **résoudre** méthode le concrète **IResolveProvider** mise en œuvre et retourne rempli **dictionnaire** instance.  
  
 **Pour créer un programme de résolution personnalisé**  
  
1.  Créer un assembly avec une classe qui implémente le **IResolveProvider** interface et contient un **résoudre** méthode qui retourne les faits de programme de résolution comme une instance de la **dictionnaire**classe.  
  
2.  Enregistrer le programme de résolution en l’ajoutant au fichier de configuration de Esb.config à l’aide un  **\<résolveur >** élément qui contient le moniker racine en tant que le **nom** attribut et qualifié complet nom de l’assembly en tant que le **type** attribut.  
  
3.  (Facultatif) Créer un schéma qui définit le moniker racine et les paramètres de requête, puis enregistrez-le à l’architecture ESB. Schemas.Resolvers dossier. Le nom doit respecter les conventions d’affectation de noms ESB existantes ; Cela signifie qu’il doit utiliser le nom du moniker racine ajouté avec « _Resolution.xsd ».  
  
4.  (Facultatif) Générer une classe dans le nouveau schéma et l’enregistrer dans l’assembly du programme de résolution personnalisé. Cela expose des paramètres typés dans le programme de résolution personnalisé.  
  
5.  Enregistrer le nouvel assembly dans le global assembly cache.