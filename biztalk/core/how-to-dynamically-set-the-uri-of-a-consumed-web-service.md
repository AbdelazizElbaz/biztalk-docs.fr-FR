---
title: "Comment définir de façon dynamique l’URI d’un Service Web utilisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95829a28-7898-4757-87cc-40fc99bf707e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3766eb98ffe5d2b73d79f09c58cf98f081c644db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-dynamically-set-the-uri-of-a-consumed-web-service"></a>Configuration dynamique de l'URI d'un service Web utilisé
Lorsque vous créez un port Web pour le service Web utilisé, vous pouvez sélectionner une liaison de port dynamique. Lorsque vous sélectionnez une liaison de port dynamique, vous devez définir l'URI du service Web utilisé au moment de l'exécution. L'URI sélectionnée doit appeler un service Web doté du même proxy Web que le service Web utilisé pour créer le type de port Web.  
  
> [!NOTE]
>  Cette rubrique décrit la configuration par programme des propriétés d'un port d'envoi SOAP dynamique dans une orchestration. Cependant, vous pouvez également définir ces propriétés dans une orchestration ou un composant de pipeline personnalisé, que le port d'envoi soit statique ou dynamique. Pour plus d’informations sur les composants de pipeline personnalisés, consultez [développement des composants de Pipeline personnalisés](../core/developing-custom-pipeline-components.md).  
  
 Le comportement des liaisons de port dynamiques pour les ports Web est différent de celui des liaisons de ports non-Web. Lors de la sélection des liaisons dynamiques pour un port non-Web, vous ne pouvez pas utiliser l'adaptateur SOAP.  
  
 Lors de l'utilisation des ports Web dynamiques pour utiliser un service Web, les propriétés du port d'envoi sont définies sur les valeurs par défaut. Certaines de ces valeurs sont définies en interne et les autres valeurs par défaut pour les valeurs qui sont définies dans le **Gestionnaire d’adaptateur SOAP** pages de propriétés. Vous pouvez remplacer ces valeurs dans une orchestration lorsque vous utilisez les ports d'envoi dynamiques. Pour plus d’informations, consultez [Considérations lors de la consommation des Services Web](../core/considerations-when-consuming-web-services.md).  
  
## <a name="dynamically-change-the-uri-of-a-consumed-web-service"></a>Modifier dynamiquement l’URI d’un service Web utilisé  
  
1.  Ajoutez un port Web, comme décrit dans [l’ajout d’un Port Web](../core/how-to-add-a-web-port.md). Toutefois, au lieu de sélectionner le **spécifier maintenant** liaison de port, sélectionnez **dynamique** port de liaison, comme indiqué dans l’illustration suivante.  
  
     ![](../core/media/ebiz-prog-wsc-dynamic.gif "ebiz_prog_wsc_dynamic")  
  
2.  Dans l’orchestration qui appelle le service Web utilisé, ajoutez un **Expression** forme à un moment donné avant le **envoyer** forme que vous avez connectée au port Web.  
  
3.  Dans le **Expression** forme, ajoutez une expression semblable à :  
  
    ```  
    myWebPort(Microsoft.XLANGs.BaseTypes.Address) = "http://orders/myCompany.asmx";  
    ```  
  
> [!NOTE]
>  Vous pouvez récupérer l'URI utilisée dans l'Éditeur d'expression BizTalk à partir de divers emplacements, notamment le message entrant, une base de données SQL ou une application sectorielle.  
  
## <a name="dynamically-modify-send-port-properties"></a>Modifier dynamiquement les propriétés du port d’envoi  
  
1.  Dans le **construire un Message** forme que vous utilisez pour construire le message Web, ajoutez un **assignation du Message** forme si aucun n’est pas déjà présent.  
  
2.  Dans le **assignation du Message** forme, ajoutez une expression semblable à :  
  
    ```  
    myWebMessage(SOAP.UseSSO) = true;  
    ```  
  
 Toutes les propriétés du port d'envoi SOAP utilisent l'espace de noms SOAP.  
  
 Le tableau suivant contient une liste des propriétés du port d'envoi SOAP que vous pouvez configurer lors de l'utilisation des ports Web dynamiques.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**AuthenticationScheme**|Chaîne|Méthode d'authentification à utiliser pour l'appel du service Web<br /><br /> Valeur par défaut : anonyme<br /><br /> Autres valeurs autorisées : Basic, Digest, NTLM|  
|**Nom d’utilisateur**|Chaîne|Nom d'utilisateur à spécifier pour accéder au service Web cible.<br /><br /> Valeur par défaut : vide|  
|**Mot de passe**|Chaîne|Mot de passe de l'utilisateur utilisé pour l'authentification sur le serveur.<br /><br /> Valeur par défaut : vide|  
|**ClientCertificate**|Chaîne|Empreinte du certificat SSL (Secure Sockets Layer) client<br /><br /> Valeur par défaut : vide|  
|**UseSSO**|Booléen|Indique si ce port Web utilisera l'authentification unique (SSO).<br /><br /> Valeur par défaut : False|  
|**AffiliateApplicationName**|Chaîne|Nom de l'application SSO que ce port Web va utiliser pour échanger le ticket et récupérer les informations d'identification du client.<br /><br /> Valeur par défaut : vide|  
|**UseHandlerSetting**|Booléen|Indique si ce port Web va utiliser les paramètres du proxy HTTP du Gestionnaire d'envoi SOAP. **Remarque :** si le **UseProxy** propriété de contexte est définie, **UseHandlerSetting** propriété de contexte est ignorée. <br /><br /> Valeur par défaut : False|  
|**UseProxy**|Booléen|Indique si ce port Web va utiliser un serveur proxy pour accéder au service Web cible. **Remarque :** si le **UseProxy** propriété de contexte est définie, **UseHandlerSetting** propriété de contexte est ignorée. <br /><br /> Valeur par défaut : False|  
|**ProxyAddress**|Chaîne|Adresse du proxy HTTP à utiliser pour l'appel de service Web.<br /><br /> Valeur par défaut : récupérées à partir des propriétés du Gestionnaire d’envoi SOAP.|  
|**ProxyPort**|Entier|Port du proxy HTTP à utiliser pour l'appel de service Web.<br /><br /> Valeur par défaut : récupérées à partir des propriétés du Gestionnaire d’envoi SOAP.|  
|**ProxyUsername**|Chaîne|Nom d'utilisateur à utiliser pour le proxy HTTP.<br /><br /> Valeur par défaut : récupérées à partir des propriétés du Gestionnaire d’envoi SOAP.|  
|**ProxyPassword**|Chaîne|Mot de passe à utiliser pour le proxy HTTP.<br /><br /> Valeur par défaut : récupérées à partir des propriétés du Gestionnaire d’envoi SOAP.|  
|**ClientConnectionTimeout**|Int32|Valeur d'expiration de la connexion du client HTTP.<br /><br /> Valeur par défaut : identique à l’expiration de connexion HTTP ASP.NET par défaut.|  
|**Nom de type**|Chaîne|Indiquez le nom de la classe contenant la méthode Web à appeler.<br /><br /> Valeur par défaut : vide|  
|**MethodName**|Chaîne|Indiquez la méthode de la classe contenant la méthode Web qui sera appelée. **Remarque :** pour configurer **MethodName** propriété le protocole SOAP statique de port d’envoi par programme, vous devez définir **nom de la méthode** à **[spécifier plus tard]** dans le **Service Web** onglet de la **propriétés du Transport SOAP** boîte de dialogue dans la console Administration de BizTalk Server. Pour plus d’informations sur **propriétés du Transport SOAP** boîte de dialogue, consultez la **boîte dialogue de propriétés du Transport SOAP, service Web** onglet [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. <br /><br /> Valeur par défaut : vide|  
|**Nom de l’assembly**|Chaîne|Identifie le type .NET et l'assembly qui doivent être chargés et exécutés.<br /><br /> Valeur par défaut : vide|  
|**UnknownHeaders**|Chaîne|Indique la liste sérialisée des en-têtes SOAP inconnus.<br /><br /> Valeur par défaut : vide|  
|**Défini par l’utilisateur**|Chaîne|Spécifie les classes définies par l'utilisateur<br /><br /> Valeur par défaut : vide|  
|**UseSoap12**|Booléen|Indiquez qu'il faut générer un code proxy qui prendra en charge le protocole SOAP 1.2. Si cette propriété est définie sur False, le code proxy compatible SOAP 1.1 sera généré.<br /><br /> Valeur par défaut : False|  
  
> [!NOTE]
>  À l’exception de la **ClientConnectionTimeout** définition, ces valeurs peuvent être configurées dynamiquement uniquement lors de l’utilisation **dynamique** liaisons de port. Ils sont en lecture seule lors de l’utilisation du **spécifier maintenant** liaison de port. Vous pouvez définir le **ClientConnectionTimeout** avec les **spécifier maintenant** et **dynamique** liaisons de port.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md)   
 [Création de Ports Web](../core/creating-web-ports.md)