---
title: "Propriétés de Configuration de l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, properties
- receive locations, adapters
- HTTP adapters, code sample
- HTTP adapters, send ports
- HTTP adapters, receive locations
- send ports, adapters
ms.assetid: 3d4e9d88-ea40-4478-a0cf-77057fadd3b2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 731f08106c698d50e95c36b8325cc3d92aa0debb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur HTTP
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur HTTP :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|ReturnCorrelationHandle|VT_BOOL|Indiquer si, en cas de succès, l'emplacement de réception envoie au client le jeton de corrélation du message envoyé dans la réponse HTTP.|Cette propriété n'est valide que pour les emplacements de réception unidirectionnels.<br /><br /> Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|Aucune|  
|ResponseContentType|VT_BSTR|Indiquer le type de contenu des messages de réponse HTTP que l'emplacement de réception renvoie aux clients.|Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|La valeur par défaut est text/xml.|  
|SuspendFailedRequests|VT_BOOL|Indiquer s'il faut suspendre ou pas les requêtes HTTP qui échouent au niveau du traitement entrant.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur 0 (faux) indique qu'il faut supprimer la requête ayant échoué et envoyer un code d'état d'erreur (401 ou 500) au client.<br /><br /> La valeur -1 (vrai) indique qu'il faut suspendre la requête ayant échoué et envoyer au client un code d'état « Accepté » (200) pour les ports de réception unidirectionnels ou un code d'état « Erreur » (500) pour les ports de réception bidirectionnels.<br /><br /> La valeur par défaut est 0 (false).|  
|UseSSO|VT_BOOL|Indiquer si l'authentification unique de l'entreprise est utilisée.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|LoopBack|VT_BOOL|Indiquer que le message de requête reçu à cet emplacement est acheminé vers un port d'envoi ou renvoyé à cet emplacement de réception en tant que réponse.|Cette propriété est valide uniquement pour des emplacements de réception de type requête-réponse.<br /><br /> Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<ReturnCorrelationHandle vt="11">-1</ReturnCorrelationHandle>  
<ResponseContentType vt="8">text/xml</ResponseContentType>  
<SuspendFailedRequests vt="11">-1</SuspendFailedRequests>  
<UseSSO vt="11">-1</UseSSO>  
<LoopBack vt="11">-1</LoopBack>  
</CustomProps></  
```  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur HTTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|Indiquer le port du serveur proxy pour ce port d'envoi.|Les valeurs valides sont comprises entre 0 et 65535.|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur 0 (faux).<br /><br /> La valeur par défaut est 80.|  
|RequestTimeout|VT_I4|Indiquez le délai d'expiration (en secondes) pour la transmission HTTP/HTTPS.|Les valeurs valides sont comprises entre 0 et MAX_LONG.|Si l'adaptateur HTTP ne reçoit pas la réponse dans ce délai, le service consigne l'erreur et soumet à nouveau le message en se basant sur la procédure de nouvelle tentative.<br /><br /> Si le délai est paramétré sur 0, le moteur de messagerie BizTalk calcule le délai en fonction de la taille du message de requête. Si vous n'indiquez pas de valeur, le système utilise celle du gestionnaire.|  
|Certificat|VT_BSTR|Indiquez l'empreinte de certificat du client à utiliser pour établir une connexion SSL (Secure Sockets Layer).|Longueur minimale : 0<br /><br /> Longueur maximale : 59|La valeur par défaut est vide.|  
|AuthenticationScheme|VT_BSTR|Indiquez le type d'authentification à utiliser avec le serveur de destination.|Les valeurs valides sont :<br /><br /> -Anonyme<br />-De base<br />-Résumé<br />-Kerberos|La valeur par défaut est Anonyme.|  
|Utilisateur|VT_BSTR|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur de destination.|Vous devez entrer la valeur de cette propriété si l'option De base ou Digest est sélectionnée pour AuthenticationScheme et que vous n'utilisez pas l'authentification unique de l'entreprise.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|Aucune|  
|EnableChunkedEncoding|VT_BOOL|Indiquez qu'il faut utiliser le codage mémorisé en bloc.|Le codage mémorisé en bloc est implicitement désactivé si le gestionnaire d'envoi HTTP est configuré sur Utiliser le proxy.<br /><br /> Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|Si cette option est activée, l’adaptateur HTTP utilise HTTP segmenté encodage avec la taille de bloc maximale de 8 Ko.<br /><br /> La valeur par défaut est 0 (false).|  
|UseProxy|VT_BOOL|Indiquer si le gestionnaire d'envoi HTTP fait appel ou non à un serveur proxy.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|ProxyName|VT_BSTR|Indiquer l'adresse du serveur proxy pour ce port d'envoi.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur 0 (faux).|  
|UseSSO|VT_BOOL|Indiquez si l'authentification unique est utilisée pour l'extraction des informations d'identification d'un client en vue d'une authentification auprès du serveur de destination.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|Mot de passe|VT_NULL|Indiquer le mot de passe à utiliser pour l'authentification sur le serveur de destination.|Vous devez entrer la valeur de cette propriété si l'option De base ou Digest est sélectionnée pour AuthenticationScheme et que vous n'utilisez pas l'authentification unique de l'entreprise.<br /><br /> Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|Définissez le type de cette propriété sur VT_BSTR (vt="8") avant d'importer le fichier de liaison si vous renseignez ce champ.|  
|MaxRedirects|VT_I4|Indiquez le nombre maximal de redirections autorisé pour le message envoyé.|Les valeurs valides sont comprises entre 0 et 10.|La valeur par défaut est 5.|  
|ContentType|VT_BSTR|Indiquez le type de contenu des messages de requête.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Lorsqu'aucune valeur n'est entrée, celle du gestionnaire est utilisée.|  
|ProxyPassword|VT_NULL|Indiquer le mot de passe utilisé pour l'authentification sur le serveur proxy.|Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur 0 (faux).|  
|ProxyUsername|VT_BSTR|Indiquer le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur 0 (faux).|  
|UseHandlerSetting|VT_BOOL|Indiquer que la configuration du port d'envoi doit utiliser les paramètres de proxy spécifiés pour le gestionnaire d'envoi HTTP.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est -1 (vrai).|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<RequestTimeout vt="3">60</RequestTimeout>  
<Certificate vt="8">A7 6D F9 06 5E FC 97 66 75 59 B5 D6 67 0C 84 DC 64 F5 BF B9</Certificate>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">authenticateduser</Username>  
<EnableChunkedEncoding vt="11">-1</EnableChunkedEncoding>  
<UseProxy vt="11">-1</UseProxy>  
<ProxyName vt="8">proxyserver</ProxyName>  
<UseSSO vt="11">0</UseSSO>  
<Password vt="1" />  
<MaxRedirects vt="3">5</MaxRedirects>  
<ContentType vt="8">text/xml</ContentType>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
<UseHandlerSetting vt="11">0</UseHandlerSetting>  
</CustomProps>  
```