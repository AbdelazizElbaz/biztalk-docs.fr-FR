---
title: "POP3 Propriétés de Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, adapters
- POP3 adapters, receive locations
- POP3 adapters, code sample
- POP3 adapters, properties
ms.assetid: e30c848d-afff-42f3-8162-c7ea8c7e3b9a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b2ca87faeb20cb717e20dc5c8b5329de37dca94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pop3-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur POP3
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception d'un adaptateur POP3 :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|mailServer|VT_BSTR|Indiquer le serveur de messagerie POP3 sur lequel réside la boîte aux lettres qui sera interrogée par l'adaptateur POP3.|Aucune|Aucune|  
|serverPort|VT_BSTR|Indiquer le port du serveur POP3.|Les valeurs valides sont comprises entre 0 et 65535.|La valeur 0 indique l'utilisation du port POP3 par défaut 110 si la propriété sslRequired est définie sur False, ou du port 995 si la propriété sslRrequired est définie sur True.<br /><br /> La valeur par défaut est 0 :|  
|userName|VT_BSTR|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur POP3.|Aucune|Aucune|  
|password|VT_BSTR|Indiquer le mot de passe utilisateur nécessaire à l'authentification sur le serveur POP3.|Cette valeur est toujours masquée lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
|authenticationScheme|VT_BSTR|Indiquez le type d'authentification à utiliser avec le serveur de destination.|Les valeurs valides sont :<br /><br /> -De base<br />-Résumé<br />-SPA|Cette propriété ne possède pas de valeur par défaut.|  
|sslRequired|VT_BSTR|Indiquer s'il faut utiliser une connexion SSL pour communiquer avec le serveur de destination.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|applyMIME|VT_BSTR|Indiquer s'il faut appliquer le décodage MIME aux messages que reçoit l'adaptateur POP3.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est true.|  
|bodyPartContentType|VT_BSTR|Indiquer le type de contenu du corps des messages électroniques entrants à envoyer à BizTalk Server.|Les valeurs valides sont :<br /><br /> -corps<br />-texte/xml<br />-texte brut<br />-texte /|Cette propriété ne possède pas de valeur par défaut.|  
|bodyPartIndex|VT_BSTR|Indiquer l'index du corps des messages électroniques entrants à envoyer à BizTalk Server.|Les valeurs valides sont comprises entre 0 et 128.|La valeur par défaut est 0 :|  
|errorThreshold|VT_BSTR|Indiquer le nombre maximal d'erreurs réseau ou de protocole devant être rencontrées avant que l'adaptateur ne soit fermé.|Les valeurs valides sont comprises entre 0 4 294 967 295.|Pour empêcher l'adaptateur de fermer, indiquer la valeur 0.<br /><br /> La valeur par défaut est 10.|  
|pollingInterval|VT_BSTR|Indiquer l'intervalle avant nouvelle tentative de récupération des messages du serveur POP3.|Les valeurs valides sont :<br /><br /> -À partir de 1 à 120 si la propriété pollingunitofmeasure est jours.<br />-À partir de 1 à 2880 si la propriété pollingunitofmeasure est heures.<br />-À partir de 1 à 172800 si la propriété pollingunitofmeasure est Minutes.<br />-À partir de 2 à 10368000 si la propriété pollingunitofmeasure est secondes.|La valeur par défaut est 5.|  
|pollingUnitOfMeasure|VT_BSTR|Spécifier l'unité de mesure à utiliser conjointement avec la valeur de la propriété pollingInterval.|Les valeurs valides sont :<br /><br /> -Jours d’utilisation<br />-Heures<br />-Minutes<br />-Secondes|La valeur par défaut est Minutes.|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet à la boîte aux lettres contrôlée par l'emplacement de réception.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><mailServer>test.microsoft.com</mailServer><serverPort>0</serverPort><userName>testuser</userName><password>******</password><authenticationScheme>Basic</authenticationScheme><sslRequired>false</sslRequired><applyMIME>true</applyMIME><bodyPartContentType>text/xml</bodyPartContentType><bodyPartIndex>1</bodyPartIndex><errorThreshold>10</errorThreshold><pollingInterval>5</pollingInterval><pollingUnitOfMeasure>Minutes</pollingUnitOfMeasure><uri>POP3://test.microsoft.com#testuser</uri></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  Lorsque vous spécifiez les données de configuration TransportTypeData pour un adaptateur qui est construit à l’aide de l’infrastructure d’adaptateurs, les paires nom/valeur utilisées doivent toutes être stockées dans le \<AdapterConfig > élément. Étant donné que le \<AdapterConfig > élément spécifie le VT_BSTR (vt = « 8 ») type de données, puis le \< > caractères dans les données doivent être échappés.