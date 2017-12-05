---
title: "Pour configurer les emplacement de réception HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, HTTP adapters
- configuring [HTTP adapters], receive locations
- HTTP adapters, receive locations
ms.assetid: 901adfc8-0361-49d9-b992-c27089dfbd3b
caps.latest.revision: "25"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4448182792cd6f6f5f7e611cd9a9bd54c75a0d05
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-configure-an-http-receive-location"></a>Configuration d'un emplacement de réception HTTP
Vous pouvez définir les variables d'un emplacement de réception HTTP par programme ou à l'aide de la console Administration de BizTalk Server. Si les propriétés ne sont pas définies pour l'emplacement de réception, les valeurs par défaut du gestionnaire de réception définies dans la console Administration de BizTalk Server sont utilisées.  
  
> [!NOTE]
>  Avant d'effectuer la procédure suivante, vous devez avoir ajouté un port de réception. Pour plus d’informations, consultez [la création d’un Port de réception](../core/how-to-create-a-receive-port.md).  
  
 **Comment faire pour configurer un emplacement de réception HTTP par programme**  
  
 L'adaptateur HTTP stocke ses informations de configuration dans la base de données de gestion BizTalk (également appelée « base de données de configuration »). La configuration est stockée dans un jeu de propriétés XML personnalisé.  
  
 Le modèle d’objet de l’Explorateur BizTalk expose le **IReceiveLocation** interface de configuration, ce qui a un **TransportTypeData** propriété en lecture/écriture. Cette propriété accepte le jeu de propriétés de configuration de l'emplacement de réception HTTP dans une chaîne XML composée d'une paire nom/valeur.  
  
 Définition de la **TransportTypeData** propriété de la **IReceiveLocation** n’est pas obligatoire. Si elle n'est pas définie, les valeurs par défaut de configuration de l'emplacement de réception HTTP sont utilisées. Le tableau suivant répertorie les valeurs par défaut et les propriétés de configuration que vous pouvez définir dans le modèle objet de l'Explorateur BizTalk pour l'emplacement de réception HTTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|**ResponseContentType**|chaîne|Type de contenu des messages de réponse HTTP que l'adaptateur HTTP renvoie aux clients à partir de cet emplacement de réception. Cette propriété n'est valide que pour les ports de réception de requête-réponse ; elle est ignorée pour des ports de réception unidirectionnels.|Chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|Valeur par défaut : Text/XML|  
|**Bouclage**|Booléen|Indique que le message de requête reçu à cet emplacement est acheminé vers un port d'envoi ou renvoyé à cet emplacement de réception en tant que réponse. Cette propriété n'est valide que pour les ports de réception de requête-réponse ; elle est ignorée pour des ports de réception unidirectionnels.|Aucune|**Valeur par défaut :** False|  
|**ReturnCorrelationHandle**|Booléen|Indique si, en cas de succès de l'envoi, l'adaptateur HTTP envoie au client le jeton de corrélation du message envoyé dans la réponse HTTP. Cette propriété n'est valide que pour les ports de réception unidirectionnels ; elle est ignorée pour des ports de réception de requête-réponse.|Aucune|**Valeur par défaut :** True|  
|**SuspendFailedRequests**|Booléen|Indique s'il faut interrompre les requêtes HTTP ayant échoué. La valeur True indique pour interrompre la requête ayant échoué et envoyer un code d’état « Accepté » (202) au client pour unidirectionnel recevoir des ports ou un code d’état « Erreur » (500) au client pour bidirectionnelle des ports de réception.|Aucune|**Valeur par défaut :** False|  
|**UseSSO**|Booléen|Spécifie si l'adaptateur HTTP émet le ticket d'authentification unique pour les messages arrivant sur cet emplacement de réception.|Aucune|**Valeur par défaut :** False|  
  
 Le format de la chaîne XML permettant de définir ces propriétés est le suivant :  
  
```  
<CustomProps>  
   <UseSSO vt="11">-1</UseSSO>  
   <SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
   <ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
   <ResponseContentType vt="8">text/xml</ResponseContentType>  
   <LoopBack vt="11">-1</LoopBack>  
</CustomProps>  
  
```  
  
 **Pour configurer l’emplacement de la Console Administration de BizTalk Server de réception HTTP**  
  
 La procédure suivante permet de configurer un emplacement de réception à l'aide de la console Administration de BizTalk Server.  
  
### <a name="to-configure-variables-for-an-http-receive-location"></a>Pour configurer les variables pour un emplacement de réception HTTP  
  
1.  Configurez les services Internet (IIS) de manière à ce qu'ils fonctionnent avec les emplacements de réception HTTP. Pour obtenir des instructions sur la configuration d’IIS, consultez [comment configurer les services IIS pour un emplacement de réception HTTP](../core/how-to-configure-iis-for-an-http-receive-location.md).  
  
2.  Dans la console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez le application dans laquelle vous souhaitez créer un emplacement de réception.  
  
3.  Dans le volet gauche, cliquez sur le **Ports de réception** nœud. Dans le volet droit, cliquez avec le bouton droit sur le port de réception associé à un emplacement de réception existant ou auquel associer un nouvel emplacement, puis cliquez sur **Propriétés**.  
  
4.  Dans le **propriétés du Port de réception** boîte de dialogue, dans le volet gauche, sélectionnez **emplacements de réception**et dans le volet droit, double-cliquez sur un existant emplacement de réception ou cliquez sur **nouveau** Pour créer un nouvel emplacement de réception.  
  
5.  Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** section regard **Type**, sélectionnez **HTTP** dans la liste déroulante puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport HTTP** boîte de dialogue zone, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Répertoire virtuel assorti de l’extension ISAPI**|Indiquer le nom du répertoire virtuel dans lequel vous publiez les messages reçus à l'emplacement de réception HTTP/HTTPS. Ce nom est constitué du nom du fichier DLL de l'emplacement de réception et d'une chaîne de requête facultative. Voici quelques exemples de noms de répertoires virtuels :<br /><br /> /\<répertoire virtuel \> /BTSHTTPReceive.dll<br /><br /> /\<répertoire virtuel \> /BTSHTTPReceive.dll ? Achat % 20Order<br /><br /> Cet emplacement ne doit pas contenir plus d'une extension ISAPI BTSHTTPReceive.dll, y compris dans tous les sous-dossiers.<br /><br /> **Type :** chaîne<br /><br /> **Longueur maximale :** 256 **Remarque :** URI pour un envoi de port ou de réception emplacement ne peut pas dépasser 256 caractères.|  
    |**Adresse publique**|Indiquer l'adresse URI complète de cet emplacement de réception. La valeur de cette propriété est constituée du nom du serveur et de celui du répertoire virtuel. Le moteur de messagerie BizTalk expose cette adresse aux partenaires externes. L'URI indiquée doit désigner l'URL du site Web public de manière à ce que les partenaires commerciaux puissent s'y connecter lors de l'envoi de messages à BizTalk Server.<br /><br /> Ces informations sont facultatives et ne sont pas utilisées par BizTalk Server. Ce paramètre est disponible pour permettre aux administrateurs de documenter l'URL publique à laquelle est lié l'emplacement de réception.<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Type de contenu renvoyé**|Indiquer le type de contenu des messages de réponse HTTP que l'emplacement de réception renvoie aux clients. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> **Valeur par défaut :** texte/xml<br /><br /> **Type :** chaîne<br /><br /> **Longueur minimale :** 0<br /><br /> **Longueur maximale :** 256|  
    |**Loopback**|Définir si le message de requête reçu à cet emplacement est acheminé vers un port d'envoi ou renvoyé à cet emplacement de réception en tant que réponse. Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne|  
    |**Gestionnaire de corrélation de retour en cas de réussite (port unidirectionnel uniquement)**|Définir si, en cas de succès, l'emplacement de réception envoie au client le jeton de corrélation du message envoyé dans la réponse HTTP. Cette propriété n'est valide que pour les emplacements de réception unidirectionnels.<br /><br /> **Valeur par défaut :** True<br /><br /> **Type :** booléenne|  
    |**Utiliser l’authentification unique**|Indiquer que l’option Enterprise Single Sign-On est utilisée.<br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne **Remarque :** si cette option est activée, vous devez également activer l’option pour **autoriser les Tickets** à la **système SSO** niveau. Le **autoriser les Tickets** option est configurable sur le **Options** onglet de la **propriétés du système SSO** boîte de dialogue disponible dans le **Administration de SSO** Interface MMC. Si cette option est activée et la **autoriser les Tickets** option à la **système SSO** niveau n’est pas activé, puis tous les messages reçus par cet emplacement de réception est interrompu.|  
    |**Suspendre des demandes ayant échoué**|Indiquer s'il faut interrompre ou non les requêtes HTTP qui échouent au niveau du traitement entrant.<br /><br /> La valeur False indique qu'il faut supprimer la requête ayant échoué et envoyer un code d'état d'erreur (401 ou 500) au client.<br /><br /> La valeur True indique qu'il faut interrompre la requête ayant échoué et envoyer au client un code d'état « Accepté » (200) pour les ports de réception unidirectionnels ou un code d'état « Erreur » (500) pour les ports de réception bidirectionnels.<br /><br /> **Valeur par défaut :** False<br /><br /> **Type :** booléenne|  
  
7.  Cliquez sur **OK** pour enregistrer les paramètres.  
  
8.  Entrez les valeurs appropriées dans la boîte de dialogue **Propriétés de l'emplacement de réception** pour terminer la configuration de l'emplacement de réception, puis cliquez sur **OK** pour enregistrer les paramètres. Pour plus d’informations sur la **propriétés des emplacements de réception** boîte de dialogue, consultez [la création d’un emplacement de réception](../core/how-to-create-a-receive-location.md).  
  
 Tandis que le client HTTP appelle l'emplacement HTTP, l'adaptateur HTTP authentifie le client à l'aide de l'authentification Anonyme, De base, Digest ou Intégrée Windows. Si la vérification de l'utilisateur est activée, le contexte utilisateur est transmis au gestionnaire de réception.  
  
> [!NOTE]
>  Toute configuration IIS menant au partage du même processus par SOAP et HTTP est non valide. Vous ne pouvez utiliser qu'un seul récepteur isolé par processus.