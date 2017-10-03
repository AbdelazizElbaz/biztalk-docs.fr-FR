---
title: "Comment configurer un Port d’envoi HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, HTTP adapters
- HTTP adapters, send ports
- configuring [HTTP adapters], send ports
ms.assetid: 29c6868c-4570-4375-9494-08c07220eeb3
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dd46ced62441c9a61c3813d0bcff5e4f2f34629
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-http-send-port"></a>Configuration d'un port d'envoi HTTP
Vous pouvez configurer un port d'envoi HTTP par programme ou à l'aide de la console Administration de BizTalk Server.  
  
## <a name="configure-an-http-send-port-programmatically"></a>Configurer un port d’envoi HTTP par programme
  
 L'adaptateur HTTP stocke ses informations de configuration dans la base de données de gestion BizTalk (également appelée « base de données de configuration »). Les informations de configuration sont stockées dans un jeu de propriétés XML personnalisé. Lors de l'initialisation et de l'exécution de l'adaptateur HTTP, le serveur transmet la configuration à l'adaptateur comme suit :  
  
-   Pour le Gestionnaire d’envoi HTTP, les informations de configuration sont transmises à l’adaptateur en appelant le **charge** méthode de la **IPersistPropertyBag** interface.  
  
-   Pour les ports d'envoi HTTP, les informations de configuration sont transmises à l'adaptateur sous la forme d'un jeu de propriétés dans un contexte de message. L'espace de noms HTTP regroupe ces propriétés.  
  
 Le modèle objet de l'Explorateur BizTalk expose l'interface de configuration d'adaptateur `ItransportInfo` pour les ports d'envoi contenant la propriété de lecture/écriture `TransportTypeData`. Cette propriété accepte le jeu de propriétés de configuration du port d'envoi HTTP sous la forme d'une chaîne XML composée d'une paire nom/valeur. Pour définir cette propriété dans le modèle d’objet de l’Explorateur BizTalk, il doit tout d’abord être configurée sur le `Address` propriété de la **ITransportInfo** interface.  
  
 Définition de la **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur HTTP utilise les valeurs par défaut pour le gestionnaire d'envoi HTTP.  
  
 Si les propriétés de configuration du port d'envoi qui dupliquent la configuration du gestionnaire ne sont pas définies, les propriétés de configuration pour le gestionnaire sont utilisées. Si le gestionnaire d'envoi HTTP ne dispose pas de valeurs de configuration, l'adaptateur d'envoi HTTP consigne une erreur dans le journal des événements et déplace le message vers l'adaptateur de secours.  
  
 Vous pouvez définir les propriétés de configuration par programme dans un contexte de message. Vous pouvez définir ces propriétés dans une planification d'orchestration BizTalk Server ou dans des composants de pipeline personnalisés. Les règles suivantes s'appliquent dans le cadre de l'utilisation de ces propriétés :  
  
-   Si la propriété de configuration est définie sur une orchestration ou un composant de pipeline personnalisé dans un pipeline de réception, alors :  
  
    -   Si un message est envoyé à un port d'envoi statique, la valeur de la propriété est remplacée par la valeur configurée pour ce port d'envoi.  
  
    -   Si un message est envoyé à un port d'envoi dynamique, la valeur de la propriété n'est pas remplacée.  
  
-   Si la propriété de configuration est définie dans un composant de pipeline personnalisé dans un pipeline d'envoi, alors :  
  
    -   La valeur n'est pas remplacée, que le message soit envoyé à un port d'envoi statique ou dynamique.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement d'envoi HTTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|**RequestTimeout**|xs:int|Délai d'attente d'une réponse du serveur. Si la valeur définie est zéro (0), le système calcule le délai en fonction de la taille du message de requête.|**Valeur minimale :** 0<br /><br /> **Valeur maximale :** MAX_LONG|**Valeur par défaut :** 0|  
|**ContentType**|xs:string|Type de contenu des messages de requête.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** Text/XML|  
|**MaxRedirects**|xs:int|Nombre maximal de fois que l'adaptateur HTTP peut rediriger la requête.|**Valeur minimale :** 0<br /><br /> **Valeur maximale :** 10|**Valeur par défaut :** 5|  
|**UseHandlerProxySettings**|xs:boolean|Indique si le port d'envoi HTTP utilisera la configuration de proxy pour le gestionnaire d'envoi.|Aucune|**Valeur par défaut :** True<br /><br /> Si la propriété est définie sur True, le port d'envoi utilisera les paramètres de proxy spécifiés au niveau du gestionnaire. Si elle est définie sur False, l'adaptateur d'envoi utilisera les informations de proxy spécifiées sur le port d'envoi.|  
|**UseProxy**|xs:boolean|Indique si l'adaptateur HTTP utilisera le serveur proxy. Le serveur proxy peut être partagé par tous les ports d'envoi HTTP.|Aucune|**Valeur par défaut :** False<br /><br /> Cette propriété est ignorée si **UseHandlerProxySettings** est **True**.|  
|**ProxyName**|xs:string|Indique le nom du serveur proxy.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> L’adaptateur d’envoi HTTP ignore cette propriété si le **UseHandlerProxySettings** est définie sur **True**. Dans le cas contraire, le protocole HTTP adaptateur d’envoi utilise cette propriété uniquement si **UseProxy** est **True**. Cette propriété est requise si **UseProxy** est **True**.|  
|**ProxyPort**|xs:int|Spécifie le port du serveur proxy.|**Valeur minimale :** 0<br /><br /> **Valeur maximale :** 65535|**Valeur par défaut :** 80<br /><br /> L’adaptateur d’envoi HTTP ignore cette propriété si **UseHandlerProxySettings** est **True**. Dans le cas contraire, HTTP adaptateur d’envoi utilise cette propriété uniquement si **UseProxy** est **True**. Cette propriété est requise si **UseProxy** est **True**.|  
|**ProxyUsername**|xs:string|Indique le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> L’adaptateur d’envoi HTTP ignore cette propriété si **UseHandlerProxySettings** est **True**. Dans le cas contraire, HTTP adaptateur d’envoi utilise cette propriété uniquement si **UseProxy** est **True**.|  
|**ProxyPassword**|xs:string|Indique le mot de passe utilisé pour l'authentification sur le serveur proxy.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> L’adaptateur d’envoi HTTP ignore cette propriété si **UseHandlerProxySettings** est **True**. Dans le cas contraire, HTTP adaptateur d’envoi utilise cette propriété uniquement si **UseProxy** est **True**.|  
|**AuthenticationScheme**|xs:string|Type d'authentification à utiliser avec le serveur de destination.|Aucune|**Valeurs valides :**<br /><br /> -   **Anonyme (par défaut)**<br />-   **Base**<br />-   **Digest**<br />-   **Kerberos**|  
|**Nom d’utilisateur**|xs:string|Nom d'utilisateur utilisé pour l'authentification sur le serveur.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> Cette valeur est obligatoire si vous sélectionnez **base** ou **Digest** l’authentification. L’adaptateur HTTP ignore la valeur de cette propriété si **UseSSO** est **True**.|  
|**Mot de passe**|xs:string|Mot de passe de l'utilisateur utilisé pour l'authentification sur le serveur.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> Cette valeur est obligatoire si vous sélectionnez **base** ou **Digest** l’authentification. La valeur de cette propriété est ignorée si **UseSSO** est **True**.|  
|**EnableChunkedEncoding**|xs:boolean|Spécifie si le codage mémorisé en bloc est utilisé ou non par l'adaptateur HTTP|Aucune|**Valeur par défaut :**<br /><br /> True|  
|**Certificat**|xs:string|Empreinte du certificat SSL client.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 59|**Valeur par défaut :** vide|  
|**UseSSO**|xs:boolean|Spécifie si l'authentification unique sera utilisée pour le port d'envoi.|Aucune|**Valeur par défaut :** False|  
|**AffiliateApplicationName**|xs:string|Nom de l’application associée à utiliser pour l’authentification unique.|**Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|**Valeur par défaut :** vide<br /><br /> Obligatoire si **UseSSO** est **True**.|  
  
 Le code suivant illustre la chaîne XML à utiliser pour définir ces propriétés :  
  
```  
<CustomProps>  
   <ContentType vt="8">text/xml</ContentType>  
   <RequestTimeout vt="3">0</RequestTimeout>  
   <MaxRedirects vt="3">5</MaxRedirects>  
   <UseHandlerProxySettings vt="8">-1</UseHandlerProxySettings>  
   <UseProxy vt="8">-1</UseProxy>  
   <ProxyName vt="8">sdfsd</ProxyName>  
   <ProxyPort vt="3">80</ProxyPort>  
   <ProxyUsername vt="8">Somename</ProxyUsername>  
   <ProxyPassword vt="8">Somepassword</ProxyPassword>  
   <AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
   <Username vt="8">Somename</Username>  
   <Password vt="8">Somepassword</Password>  
   <EnableChunkedEncoding vt="11">1</EnableChunkedEncoding>  
   <Certificate vt="8">AAAA BBBB CCCC DDDD</Certificate>  
   <UseSSO vt="11">0</UseSSO>  
   <AffiliateApplicationName vt="8">Name</AffiliateApplicationName>  
</CustomProps>  
```  
  
## <a name="configure-an-http-send-port-with-the-biztalk-server-administration-console"></a>Configurer un port d’envoi HTTP avec la console Administration de BizTalk Server
  
 Vous pouvez définir les variables de l'adaptateur du port d'envoi HTTP dans la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour le port d’envoi, la valeur par défaut le valeurs définies dans la console Administration de BizTalk Server sont utilisées de gestionnaire d’envoi.  
  
> [!NOTE]
>  Les propriétés de configuration décrites dans cette rubrique sont communes aux ports d'envoi HTTP unidirectionnels et de requête-réponse.  
  
1.  Dans la console Administration de BizTalk Server, créez un port d’envoi ou double-cliquez sur un port d’envoi existant pour le modifier. Consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md) pour plus d’informations. Configurez toutes les options de port d’envoi et spécifiez **HTTP** pour le **Type** option dans le **Transport** section sur le **général** onglet.  
  
2.  Sur le **général** sous l’onglet du **Transport** , cliquez sur le **configurer** situé en regard **Type**.  
  
3.  Dans le **propriétés du Transport HTTP** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL de destination**|Obligatoire. Indiquez l'adresse à laquelle envoyer les requêtes HTTP. Incluez les chaînes de requête ajoutées à l'URL de base.<br /><br /> **Type :** chaîne<br /><br /> **Longueur maximale :** 256<br /><br /> Pour plus d’informations, consultez [Restrictions sur la propriété URL de Destination](../core/restrictions-on-the-destination-url-property.md). **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Activer le codage mémorisé en bloc**|Indiquez qu'il faut utiliser le codage mémorisé en bloc. Si cette option est activée, l'adaptateur HTTP utilise le codage mémorisé en bloc HTTP avec une taille de bloc maximale de 8 Ko. Le codage mémorisé en bloc est implicitement désactivé si le Gestionnaire d’envoi HTTP est configuré pour **utiliser le proxy**.<br /><br /> **Type :** booléenne<br /><br /> **Valeur par défaut :** True|  
    |**Délai de demande (s)**|Indiquez le délai d'expiration (en secondes) pour la transmission HTTP/HTTPS. Si l'adaptateur HTTP ne reçoit pas la réponse dans ce délai, le service consigne l'erreur et soumet à nouveau le message en se basant sur la procédure de nouvelle tentative.<br /><br /> Si le délai est paramétré sur zéro (0), le moteur de messagerie BizTalk calcule le délai en fonction de la taille du message de requête. Si vous n'indiquez pas de valeur, le système utilise celle du gestionnaire.<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** MAX_LONG|  
    |**Nombre maximal de redirections**|Indiquez le nombre maximal de redirections autorisé pour le message envoyé.<br /><br /> **Valeur par défaut :** 5<br /><br /> **Type :** Int<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** 10|  
    |**Type de contenu**|Indiquez le type de contenu des messages de requête.<br /><br /> Lorsqu'aucune valeur n'est entrée, celle du gestionnaire est utilisée.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
  
4.  Dans le **propriétés du Transport HTTP** boîte de dialogue le **Proxy (remplacement du gestionnaire)** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utiliser la configuration du proxy par défaut du Gestionnaire**|Indiquez que la configuration du port d'envoi doit utiliser les paramètres de proxy spécifiés pour le gestionnaire d'envoi HTTP.<br /><br /> Il s'agit du paramètre par défaut.|  
    |**N’utilisez pas de proxy**|Indiquez si le gestionnaire d'envoi HTTP fait appel ou non au serveur proxy.<br /><br /> Si cette option est sélectionnée, le gestionnaire d'envoi HTTP pour ce port d'envoi ne fait pas appel au serveur proxy.|  
    |**Utiliser le proxy**|Indiquez si le gestionnaire d'envoi HTTP fait appel ou non au serveur proxy.<br /><br /> Si cette option est sélectionnée, le gestionnaire d'envoi HTTP fait appel au serveur proxy.|  
    |**Server**|Indiquer l'adresse du serveur proxy pour ce port d'envoi.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Port**|Indiquer le port du serveur proxy pour ce port d'envoi.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> **Valeur par défaut :** 80<br /><br /> **Type :** Long<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** 65535|  
    |**Nom d'utilisateur**|Indiquer le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Mot de passe**|Indiquer le mot de passe utilisé pour l'authentification sur le serveur proxy.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
  
5.  Dans le **propriétés du Transport HTTP** boîte de dialogue le **authentification** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Type d’authentification**|Indiquez le type d'authentification à utiliser avec le serveur de destination.<br /><br /> Les options admises sont les suivantes :<br /><br /> -   **Anonyme**<br />-   **Base**<br />-   **Digest**<br />-   **Kerberos**<br /><br /> **Valeur par défaut :** anonyme|  
    |**Informations d’identification**|Indiquez le type d'informations d'identification à utiliser.<br /><br /> Disponible uniquement si le **Type d’authentification** est **base** ou **Digest**.<br /><br /> Les options admises sont les suivantes :<br /><br /> -   **N’utilisez pas l’authentification unique**<br />     **Nom d’utilisateur :**<br />     Nom d'utilisateur utilisé pour l'authentification sur le serveur de destination. Si le **Type d’authentification** propriété **anonyme** ou **Kerberos**, cette option est désactivée. Cette propriété exige une valeur si **base** ou **Digest** est sélectionnée, et Enterprise Single Sign-On n’est pas utilisé.<br />     **Longueur minimale :** 0<br />     **Longueur maximale :** 256<br />     **Mot de passe :**<br />     Mot de passe utilisé pour l'authentification sur le serveur de destination. Si le **Type d’authentification** propriété **anonyme** ou **Kerberos**, cette option est désactivée. Cette propriété exige une valeur si **base** ou **Digest** est sélectionnée, et l’authentification unique n’est pas utilisé.<br />     **Longueur minimale :** 0<br />     **Longueur maximale :** 256<br />-   **Utiliser l’authentification unique**<br />     Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br />     **Application associée**<br />     Indiquez une application associée à utiliser pour l'authentification unique.<br />     Vous choisissez les applications que vous souhaitez inclure dans l'authentification unique.<br />     **Longueur minimale :** 0<br />     **Longueur maximale :** 256|  
    |**Empreinte de certificat client SSL**|Indiquez l'empreinte de certificat du client à utiliser pour établir une connexion SSL (Secure Sockets Layer).<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 59|  
  
6.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration d’un Port d’envoi HTTP](../core/configuring-an-http-send-port.md)