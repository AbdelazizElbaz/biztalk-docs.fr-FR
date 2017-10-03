---
title: "Comment configurer un Port d’envoi SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, send ports
- SOAP adapters, code samples
- code samples, SOAP adapters
- configuring [SOAP adapters], code samples
- configuring [SOAP adapters], send ports
- send ports, SOAP adapters
ms.assetid: 3a0622f4-d25d-4449-a063-d8ba217e9729
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3cb290feb7b61cf3d2ccdeffb6c795d88c537b4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-send-port"></a>Configuration d'un port d'envoi SOAP
Vous pouvez configurer un port d'envoi SOAP soit par programme soit à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 **Comment configurer un Port d’envoi SOAP par programme**  
  
 Le modèle d’objet de l’Explorateur BizTalk expose une interface spécifique à l’adaptateur pour les ports d’envoi nommé **ITransportInfo** qui a le **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration du port d'envoi SOAP sous la forme d'une chaîne XML composée d'une paire nom/valeur. Notez que pour définir cette propriété dans l’objet de l’Explorateur BizTalk de modèle vous devez définir le **OutboundTransportLocation** propriété de la **ITransportInfo** tout d’abord de l’interface.  
  
 Le **TransportTypeData** propriété de la **ITransportInfo** interface n’est pas requise. Si elle n'est pas définie, l'adaptateur utilise les valeurs par défaut pour la configuration du port d'envoi SOAP, comme indiqué dans le tableau suivant.  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour les ports d'envoi SOAP.  
  
|Nom de la propriété|Type| Description|  
|-------------------|----------|-----------------|  
|**URI**|Chaîne|Répertoire virtuel contenant le service Web sur le serveur de déploiement.|  
|**Nom d’utilisateur**|Chaîne|Nom d'utilisateur à spécifier pour accéder au service Web cible.<br /><br /> Valeur par défaut : vide|  
|**Mot de passe**|Chaîne|Mot de passe de l'utilisateur utilisé pour l'authentification sur le serveur.<br /><br /> Valeur par défaut : vide|  
|**ClientCertificate**|Chaîne|Empreinte numérique du certificat SSL client.<br /><br /> Valeur par défaut : vide|  
|**AffiliateApplicationName**|Chaîne|Nom de l'application SSO à utiliser pour échanger le ticket et récupérer les informations d'identification du client.<br /><br /> Le **AffiliateApplicationName** s’excluent mutuellement pour un **nom d’utilisateur** et **mot de passe** paire.<br /><br /> Valeur par défaut : vide|  
|**UseProxy**|Booléen|Indiquez si le port d'envoi SOAP fait appel ou non à un serveur proxy pour accéder au service Web cible. Le serveur proxy peut être partagé par tous les ports d'envoi SOAP.<br /><br /> Valeur par défaut : False|  
|**ProxyAddress**|Chaîne|Adresse du proxy HTTP à utiliser pour l'appel de service Web.<br /><br /> Valeur par défaut : vide|  
|**ProxyPort**|Entier|Port du proxy HTTP à utiliser pour l'appel de service Web.<br /><br /> Valeur par défaut : vide|  
|**ProxyUsername**|Chaîne|Nom d'utilisateur à utiliser pour le proxy.<br /><br /> Valeur par défaut : vide|  
|**ProxyPassword**|Chaîne|Mot de passe à utiliser pour le proxy.<br /><br /> Valeur par défaut : vide|  
  
 Le code suivant illustre le format à utiliser pour définir ces propriétés :  
  
```  
<CustomProps>  
   <URI vt="8"/>  
   <ClientCertificate vt="8"/>  
   <Password vt="8">Encrypted</Password>  
   <ProxyAddress vt="8"/>  
   <ProxyPassword vt="8">Encrypted</ProxyPassword>  
   <ProxyPort vt="3"/>  
   <ProxyUsername vt="8"/>  
   <UseProxy vt="11"/>  
   <Username vt="8"/>  
   <AffiliateApplicationName vt="8"/>  
</CustomProps>  
```  
  
 **Comment configurer un Port d’envoi SOAP avec la Console Administration de BizTalk Server**  
  
 La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de définir des variables d'adaptateur de port d'envoi SOAP. Si aucune propriété n'est définie pour le port d'envoi, les valeurs par défaut du gestionnaire d'envoi définies dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont utilisées.  
  
### <a name="to-configure-variables-for-a-soap-send-port"></a>Pour configurer les variables d'un port d'envoi SOAP  
  
1.  Dans la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], créez un port d'envoi ou double-cliquez sur un port d'envoi existant pour le modifier. Pour plus d’informations, consultez [la création d’un Port d’envoi](../core/how-to-create-a-send-port2.md). Configurez toutes les options de port d’envoi et spécifiez **SOAP** pour le **Type** option dans le **Transport** section de la **général** onglet.  
  
2.  Sur le **général** sous l’onglet le **Transport** section regard **Type**, cliquez sur **configurer**.  
  
3.  Dans le **propriétés du Transport SOAP** boîte de dialogue le **général** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**URL du Service Web**|Spécifiez l'adresse du service Web à appeler. **Remarque :** l’URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Authentification**|Indiquez la méthode d'authentification utilisée par le service Web que vous appelez.<br /><br /> Options :<br /><br /> -   **Anonyme.** Paramètre par défaut.<br />-   **De base.** La connexion SOAP envoie le nom d'utilisateur et le mot de passe en texte clair.<br />-   **Digest.** La connexion SOAP envoie le mot de passe dans un format chiffré.<br />-   **NTLM.** Ni le nom d'utilisateur ni le mot de passe n'est envoyé via une connexion SOAP. L'adaptateur SOAP utilise toujours les informations d'identification du processus sous lequel l'adaptateur d'envoi SOAP s'exécute pour ce type d'authentification.|  
    |**Informations d’identification**|Indiquez le type d'informations d'identification à utiliser.<br /><br /> Disponible uniquement si le **type d’authentification** est **base** ou **Digest**.<br /><br /> Options :<br /><br /> -   **N’utilisez pas l’authentification unique**<br />     **Nom d'utilisateur**<br />     Nom d'utilisateur utilisé pour l'authentification sur le serveur de destination. Si le **type d’authentification** propriété **anonyme** ou **NTLM**, cette option est désactivée. Cette propriété exige une valeur si **base** ou **Digest** est sélectionnée, et Enterprise Single Sign-On n’est pas utilisé.<br />     Longueur minimale : 0<br />     Longueur maximale : 256<br />     **Mot de passe**<br />     Mot de passe utilisé pour l'authentification sur le serveur de destination. Si le **type d’authentification** propriété **anonyme** ou **NTLM**, cette option est désactivée. Cette propriété exige une valeur si **base** ou **Digest** est sélectionnée, et l’authentification unique n’est pas utilisé.<br />     Longueur minimale : 0<br />     Longueur maximale : 256<br />-   **Utiliser l’authentification unique**<br />     Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.<br />     **Application associée**<br />     Indiquez une application associée à utiliser pour l'authentification unique. Pour plus d’informations sur le renseignement de cette liste, consultez [Applications associées SSO](../core/sso-affiliate-applications.md).<br />     Longueur minimale : 0<br />     Longueur maximale : 256|  
    |**Empreinte de certificat client**|Indiquez l'empreinte de certificat du client à utiliser pour établir une connexion.<br /><br /> Exemple : 01 23 45 67 89 AB CD EF 01 23 45 67 89 AB CD EF 01 23 45 67<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 59|  
  
4.  Dans le **propriétés du Transport SOAP** boîte de dialogue le **Proxy** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Utiliser la configuration du proxy par défaut du Gestionnaire**|Spécifiez la configuration du gestionnaire de proxy du port d'envoi. Si la propriété est définie sur True, le port utilisera les paramètres de proxy spécifiés au niveau du gestionnaire. Si elle est définie sur False, l'adaptateur d'envoi utilisera les informations de proxy spécifiées sur le port d'envoi.<br /><br /> Le paramètre par défaut est true.|  
    |**N’utilisez pas de proxy**|Indiquer si le gestionnaire d'envoi SOAP fait appel ou non à un serveur proxy.|  
    |**Utiliser le proxy**|Indiquer si le gestionnaire d'envoi SOAP fait appel ou non à un serveur proxy. Le serveur proxy peut être partagé par tous les ports d'envoi SOAP.|  
    |**Server**|Indiquez le nom du serveur proxy.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Port**|Indiquer le port que le gestionnaire d'envoi SOAP utilise.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Valeur par défaut : 80<br /><br /> Type : Long<br /><br /> Valeur minimale : 0<br /><br /> Valeur maximale : 65535 **Remarque :** spécifiant la valeur 0 indique l’utilisation de la valeur par défaut, qui est le port 80.|  
    |**Nom d'utilisateur**|Indiquer le nom d’utilisateur nécessaire à l’authentification. Si vous utilisez l’authentification Windows intégrée, le nom d’utilisateur inclut le domaine, **domaine om_utilisateur**. Si vous utilisez Basic ou l’authentification Digest, le nom d’utilisateur n’inclut pas **domaine\\**.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
    |**Mot de passe**|Indiquer le mot de passe nécessaire à l’authentification.<br /><br /> Cette propriété requiert uniquement une valeur si **utiliser le proxy** est sélectionnée.<br /><br /> Type : Chaîne<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|  
  
5.  Dans le **propriétés du Transport SOAP** boîte de dialogue le **Service Web** onglet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Port Web d’orchestration**|Spécifiez pour utiliser le service Web qui est exposé à l’URL du Service Web répertorié dans le **général** onglet.<br /><br /> Il s'agit du paramètre par défaut.|  
    |**Nom de l’assembly**|Indiquez le nom de l'assembly contenant le proxy du service Web. Cliquez sur le bouton Parcourir pour localiser un assembly. Sélectionnez l'assembly pour faire apparaître son nom complet dans ce champ. **Remarque :** l’assembly spécifié doit être présent sur tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]s lors de l’exécution.|  
    |**Nom de type**|Indiquez le nom de la classe contenant la méthode Web à appeler. Celui-ci peut être sélectionné dans une liste des types contenue dans l'assembly.|  
    |**Nom de la méthode**|Spécifiez l’une des méthodes dans la zone de liste ou choisissez l’option « Spécifier » plus tard. Si vous choisissez la deuxième option, la méthode Web doit être définie par d'autres moyens, tels qu'un composant de pipeline. Dans ce scénario, la méthode web doit être écrit à l’adaptateur Soap **MethodName** propriété de contexte.|  
    |**SOAP 1.2**|Indiquez qu'il faut générer un code proxy qui prendra en charge le protocole SOAP 1.2. Si cette option n'est pas sélectionnée, le code proxy compatible SOAP 1.1 sera généré.<br /><br /> Valeur par défaut : désactivée|  
  
6.  Cliquez sur **OK** et **OK** pour enregistrer les paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Publication de Services Web](../core/publishing-web-services.md)