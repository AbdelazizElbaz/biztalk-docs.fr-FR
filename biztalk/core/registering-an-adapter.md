---
title: "Inscription d’un adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc85b96e-7b7b-4131-88ec-87b419a61bc2
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cc195a55b38a232880ed04108d5a533afd1a311
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="registering-an-adapter"></a>Inscription d'un adaptateur
Si vous développez un adaptateur personnalisé, vous pouvez l'inscrire auprès du serveur BizTalk Server en modifiant et en exécutant l'un des fichiers de Registre inclus avec l'exemple d'adaptateur FILE dans le Kit de développement (SDK). Vous pouvez également utiliser l'Assistant Registre de l'adaptateur pour créer un fichier de Registre. Cet Assistant est situé dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Utilities\AdapterRegistryWizard.  
  
> [!IMPORTANT]
>  -   Sur un ordinateur 32 bits, le fichier de Registre (.reg) généré par l'Assistant Registre de l'adaptateur doit être exécuté à partir d'une invite de commandes.  
> -   Sur un ordinateur 64 bits, le fichier de Registre (.reg) généré par l'Assistant Registre de l'adaptateur doit être exécuté à partir d'une invite de commandes 32 bits et 64 bits.  
  
 Après avoir créé des entrées de Registre, vous pouvez ajouter l'adaptateur dans la console Administration de BizTalk Server ou procéder de façon programmée en recourant aux méthodes Windows Management Instrumentation (WMI). Cette rubrique aborde chacune des entrées du Registre avant de vous montrer où et comment modifier les fichiers de Registre existants correspondant à votre adaptateur personnalisé.  
  
 Pour obtenir des instructions sur l’utilisation de cet Assistant, consultez [Assistant Registre d’adaptateur](../core/adapter-registry-wizard.md). Pour obtenir des instructions sur la modification des fichiers du Registre exemple inclus dans le SDK, consultez [fichier d’inscription de carte](../core/adapter-registration-file.md).  
  
## <a name="registry-keys"></a>les clés de Registre  
 Pour déployer un adaptateur, vous devez créer les entrées de Registre suivantes :  
  
 **Emplacement de la clé du Registre**  
  
```  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\BizTalk]  
@="BizTalk"  
  
```  
  
 **Nom de type**  
  
 Le nom du type d'adaptateur identifie le type d'adaptateur sur l'ordinateur BizTalk Server. Cette clé est requise pour tout adaptateur.  
  
```  
"TransportType"="MyTransportAdapter"  
  
```  
  
 **Contraintes**  
  
 Les contraintes d'adaptateur définissent les fonctionnalités de l'adaptateur.  
  
 Cette clé est requise pour chaque adaptateur. En fonction du type d'adaptateur que vous créerez, vous pourrez souhaiter modifier la valeur de masque de bits des contraintes.  
  
```  
"Constraints"=dword:00003C0b  
```  
  
 La valeur décrivant les fonctionnalités de l'adaptateur peut être une combinaison de valeurs présentées dans le tableau suivant :  
  
|Valeur|Valeur hexadécimale|Indicateur| Description|  
|-----------|---------------|----------|-----------------|  
|1|0x0001|eProtocolSupportsReceive|L'adaptateur prend en charge les opérations de réception.|  
|2|0x0002|eProtocolSupportsTransmit|L'adaptateur prend en charge les opérations d'envoi.|  
|8|0x0008|eProtocolReceiveIsCreatable|Le gestionnaire de réception de l'adaptateur est hébergé de manière in-process.|  
|128|0x0080|eProtocolSupportsRequestResponse|L'adaptateur prend en charge les opérations de requête-réponse.|  
|256|0x0100|eProtocolSupportsSolicitResponse|L'adaptateur prend en charge les opérations de sollicitation-réponse.|  
|1024|0x4000|eOutboundProtocolRequiresContextInitialization|Indique que l'adaptateur utilise l'interface utilisateur fournie par l'infrastructure d'adaptateurs pour configurer les gestionnaires d'envoi.|  
|2048|0x0800|eInboundProtocolRequiresContextInitialization|Indique que l'adaptateur utilise l'interface utilisateur fournie par l'infrastructure d'adaptateurs pour configurer les gestionnaires de réception.|  
|4096|0x1000|eReceiveLocationRequiresContextInitialization|Indique que l’adaptateur utilise l’interface utilisateur de l’infrastructure d’adaptateurs pour configuration de l’emplacement de réception.|  
|8192|0x2000|eTransmitLocationRequiresContextInitialization|Indique que l’adaptateur utilise l’interface utilisateur d’infrastructure d’adaptateurs pour la configuration du port d’envoi.|  
|16384|0x4000|eSupportsOrderedDelivery|Indique que l'adaptateur prend en charge la livraison chronologique des messages.|  
|32768|0x8000|eInitTransmitterOnServiceStart|L'adaptateur d'envoi démarre quand au démarrage du service et non lorsqu'il envoie le premier message.|  
|65536|0x10000|eSupport32BitOnly|Indique que l'adaptateur ne prend en charge que les hôtes s'exécutant en 32 bits.|  
  
### <a name="namespace"></a>Espace de noms  
 Chaque adaptateur doit définir un espace de noms pour ses propriétés. BizTalk Server stocke des propriétés propres aux adaptateurs dans le contexte de message situé sous cet espace de noms. Cette propriété est requise pour tous les adaptateurs.  
  
```  
"PropertyNameSpace"="namespace"  
```  
  
### <a name="aliases"></a>Alias  
 Chaque adaptateur peut avoir un jeu de préfixes qui identifient de façon unique le type de l'adaptateur dans BizTalk Server. Cela permet de déterminer le type de transport correct lors de l'envoi d'un message via un port d'envoi dynamique. L'adaptateur doit spécifier la liste de ses préfixes au moment de l'inscription.  
  
```  
"AliasesXML"="<AdapterAliasList><AdapterAlias>sample://</AdapterAlias></AdapterAliasList>"  
```  
  
### <a name="configuration-property-pages"></a>Pages de propriétés de configuration  
 L'adaptateur doit disposer de pages de propriétés de configuration pour configurer ses emplacements de réception et ses ports d'envoi. Chaque adaptateur inscrit ses pages de propriétés en spécifiant ses ID de classe.  
  
```  
"InboundProtocol_PageProv"="{%CLSID for inbound protocol prop page%}"  
"OutboundProtocol_PageProv"="{%CLSID for outbound protocol prop page%}"  
"ReceiveLocation_PageProv"="{%CLSID for receive location prop page%}"  
"TransmitLocation_PageProv"="{%CLSID for transmit location prop page%}"  
```  
  
 Si l'adaptateur utilise l'interface utilisateur de l'infrastructure d'adaptateurs pour la génération de pages de propriétés, il doit spécifier les valeurs suivantes pour les clés de Registre :  
  
```  
"InboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A281}"  
"OutboundProtocol_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A283}"  
"ReceiveLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A280}"  
"TransmitLocation_PageProv"="{2DE93EE6-CB01-4007-93E9-C3D71689A282}"  
```  
  
 Notez que si l'un des points de terminaison n'est pas requis (car l'adaptateur est de type « envoi seulement » ou « réception seulement »), les clés de Registre inutilisées peuvent être effacées du Registre.  
  
### <a name="runtime-component-registration"></a>Inscription des composants d'exécution  
 L'adaptateur inscrit ses composants d'exécution de réception et d'envoi en spécifiant leurs ID de classe (pour COM et .NET), leurs noms de type et leurs chemins d'accès d'assembly (pour .NET).  
  
> [!NOTE]
>  Tous les **OutboundEngineCLSID** et **InboundEngineCLSID** clés doivent être uniques. Pour une ligne unique dans une base de données, le **OutboundEngineCLSID** et **InboundEngineCLSID** peuvent être identiques.  
  
```  
"OutboundEngineCLSID"="{%CLSID of outbound transport%}"  
"InboundEngineCLSID"="{%CLSID of inbound transport%}"  
"InboundTypeName"="BizTalk.Samples.Adapters.MyReceiver"  
"OutboundTypeName"="BizTalk.Samples.Adapters.MyTransmitter"  
"InboundAssemblyPath"="C:\Program Files\MyTransport.dll"  
"OutboundAssemblyPath"="C:\Program Files\MyTransport.dll"  
```  
  
> [!NOTE]
>  Vous pouvez installer l'assembly d'un adaptateur dans le Global Assembly Cache et y faire référence dans le fichier de Registre.  
  
### <a name="registration-of-adapter-properties-for-sso-configuration-store"></a>Inscription de propriétés d'adaptateur pour le magasin de configuration de l'authentification unique  
 L'adaptateur doit inscrire ses propriétés auprès de la base de données de l'authentification unique BizTalk Server pour être en mesure de les stocker et de les récupérer au moment de la conception et de l'exécution.  
  
```  
ReceiveHandlerPropertiesXML  
ReceiveLocationPropertiesXML  
SendHandlerPropertiesXML  
SendLocationPropertiesXML  
```  
  
 Ces valeurs contiennent les définitions (schéma) des propriétés autorisées des entités correspondantes liées à l'adaptateur, propriétés qui peuvent être stockées dans le magasin de configuration. Ces définitions sont conservées sous la forme d'une chaîne XML désérialisée par le jeu de propriétés contenant les types de propriétés mais dépourvu des valeurs. Si l'élément de la propriété a une valeur non vide, cela signifie que la propriété est masquée (autrement dit, elle est en écriture uniquement et n'est pas retournée par l'API de magasin sécurisé lorsqu'elle est appelée en mode administratif ; l'API de magasin sécurisé retourne VT_NULL pour les propriétés de ce genre).  
  
### <a name="example"></a>Exemple  
 L’adaptateur HTTP inscrit ses propriétés pour le port d’envoi HTTP en définissant le **SendLocationPropertiesXML** clé de Registre avec la valeur suivante :  
  
```  
<CustomProps><Username vt="8"/><Password vt="8">Encrypted</Password><Certificate vt="8"/><RequestTimeout vt="3"/><MaxRedirects vt="3"/><ContentType vt="8"/><UseProxy vt="11"/><ProxyName vt="8"/><ProxyPort vt="3"/><ProxyUsername vt="8"/><ProxyPassword vt="8">Encrypted</ProxyPassword><UseHandlerSetting vt="11"/><AuthenticationScheme vt="8"/><UseSSO vt="11"/><AffiliateApplicationName vt="8"/></CustomProps>  
```  
  
### <a name="registration-of-the-component-as-a-transport-provider"></a>Inscription du composant en tant que fournisseur de transport  
 Dans le Registre, l'adaptateur doit être inscrit en tant que fournisseur de transport sous son attribut de catégories implémentées. Cet attribut permet à ses utilisateurs d'identifier ses caractéristiques.  
  
```  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\Implemented Categories]  
[HKEY_CLASSES_ROOT\CLSID\{%uuid of custom transport%}\Implemented Categories\{7F46FC3E-3C2C-405B-A47F-8D17942BA8F9}]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de conception de l’adaptateur](../core/adapter-design-issues.md)