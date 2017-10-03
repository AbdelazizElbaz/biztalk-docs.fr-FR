---
title: "Propriétés de Configuration de l’adaptateur SOAP | Documents Microsoft"
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
- SOAP adapters, properties
- receive locations, adapters
- SOAP adapters, receive locations
- send ports, adapters
ms.assetid: 0d033371-ee31-4e43-a7d3-e0975791d981
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52fde9d80717d192d3a5b90548ccc01e87d2044
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur SOAP
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur SOAP :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|UseSSO|VT_BOOL|Indiquez s'il faut utiliser l'authentification unique.|-Les valeurs valides sont :<br />-à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<UseSSO vt="11">0</UseSSO>  
</CustomProps>  
```  
  
 Ce tableau répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur SOAP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|ProxyPort|VT_I4|Indiquer le port du serveur proxy pour ce port d'envoi.|Aucune|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur -1 (vrai).<br /><br /> La valeur par défaut est 80.|  
|AuthenticationScheme|VT_BSTR|Indiquez le type d'authentification à utiliser avec le serveur de destination.|Les valeurs valides sont :<br /><br /> -Anonyme<br />-De base<br />-Résumé<br />-NTLM|La valeur par défaut est Anonyme.|  
|Utilisateur|VT_BSTR|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur de destination.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Cette propriété ne requiert une valeur que si la propriété AuthentificationScheme est définie sur De base ou Digest et si la propriété UseSSO est définie sur 0 (faux).|  
|UseProxy|VT_BOOL|Indiquez si le gestionnaire d'envoi SOAP fait appel ou non à un serveur proxy.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|UseSoap12|VT_BOOL|Indiquez qu'il faut générer un code proxy qui prendra en charge le protocole SOAP 1.2.|Si cette option n’est pas sélectionnée, le code de proxy 1.1 compatible SOAP sera généré.<br /><br /> Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|UsingOrchestration|VT_BOOL|Indiquez s'il faut utiliser le proxy de service Web associé à l'adresse de ce port d'envoi.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est -1 (vrai).|  
|UseSSO|VT_BOOL|Indiquer si l'authentification unique de l'entreprise est utilisée.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|ProxyAddress|VT_BSTR|Indiquer le nom du serveur proxy.|Cette propriété n'est valide que si la propriété UseProxy est définie sur -1 (vrai).|Aucune|  
|Mot de passe|VT_NULL|Indiquer le mot de passe à utiliser pour l'authentification sur le serveur de destination.|Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Cette propriété ne requiert une valeur que si la propriété AuthentificationScheme est définie sur De base ou Digest et si la propriété UseSSO est définie sur 0 (faux).|  
|AssemblyPath|VT_BSTR|Indiquez le chemin d'accès de l'assembly contenant le proxy du service Web.|Aucune|Aucune|  
|TypeName|VT_BSTR|Indiquez le nom de la classe contenant la méthode Web à appeler.|Aucune|Aucune|  
|MethodName|VT_BSTR|Indiquez la méthode de la classe contenant la méthode Web qui sera appelée.|Aucune|Aucune|  
|UseHandlerSetting|VT_BOOL|Indiquez s'il faut utiliser la configuration proxy par défaut pour le gestionnaire d'envoi SOAP.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est -1 (vrai).|  
|ClientCertificate|VT_BSTR|Indiquez l'empreinte de certificat du client à utiliser pour établir une connexion.|Longueur minimale : 0<br /><br /> Longueur maximale : 59|Aucune|  
|ProxyPassword|VT_NULL|Indiquez le mot de passe à utiliser pour l'authentification sur le serveur proxy.|Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur 0 (faux).|  
|ProxyUsername|VT_BSTR|Indiquez le nom d'utilisateur nécessaire à l'authentification sur le serveur proxy.|Aucune|Cette propriété ne requiert une valeur que si la propriété UseProxy est définie sur -1 (vrai).|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<ProxyPort vt="3">80</ProxyPort>  
<AuthenticationScheme vt="8">Basic</AuthenticationScheme>  
<Username vt="8">domain\testuser</Username>  
<UseProxy vt="11">-1</UseProxy>  
<UseSoap12 vt="11">-1</UseSoap12>  
<UsingOrchestration vt="11">-1</UsingOrchestration>  
<UseSSO vt="11">0</UseSSO>  
<ProxyAddress vt="8">proxy</ProxyAddress>  
<Password vt="1" />  
<ProxyPort vt="3">80</ProxyPort>  
<AssemblyPath vt="8">C:\Websvc.dll</AssemblyPath>  
<TypeName vt="8">Websvc.svc</TypeName>  
<MethodName vt="8">WebMethod</MethodName>  
<UseHandlerSetting vt="11">0</UseHandlerSetting></  
<ClientCertificate vt="8">23779A5EEA9693A37409021EFCDAB713A3680C34</ClientCertificate>  
<ProxyPassword vt="1" />  
<ProxyUsername vt="8">proxyuser</ProxyUsername>  
</CustomProps>  
```