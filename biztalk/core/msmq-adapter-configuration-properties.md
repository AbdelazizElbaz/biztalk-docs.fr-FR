---
title: "Propriétés de Configuration de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, receive locations
- MSMQ adapters, send ports
- receive locations, adapters
- MSMQ adapters, properties
- MSMQ adapters, code sample
- send ports, adapters
ms.assetid: d660d0ce-bff9-4bc5-be1d-38954c2fdbe2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 060d6fbfb75c97e4fa4bc6bbfc3f160972c437ff
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="msmq-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur MSMQ
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception d'un adaptateur MSMQ :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|queue|VT_BSTR|Indiquer un chemin d'accès de file d'attente valide à l'emplacement contrôlé par l'emplacement de réception.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|batchSize|VT_BSTR|Indiquer la taille de lot que l'adaptateur MSMQ utilise pour soumettre un lot de messages à la base de données MessageBox.|Les valeurs valides vont de 1, 4 294 967 295.|La valeur par défaut est 20.|  
|transactionnels|VT_BSTR|Indiquer si vous voulez lire les messages à partir de la file d'attente source dans le contexte d'une transaction distribuée Microsoft (MSDTC).|Les valeurs valides sont :<br /><br /> -true<br />-false<br /><br /> L'adaptateur ne prend pas en charge les lectures transactionnelles sur les files d'attente distantes.|La valeur par défaut est false.|  
|serialProcessing|VT_BSTR|Spécifier si vous voulez traiter les messages dans l'ordre.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|onFailure|VT_BSTR|Indiquer comment l'adaptateur doit réagir à une erreur.|Les valeurs valides sont :<br /><br /> -stopOnFailure<br />-suspendNonResumable<br />-suspendResumable|La valeur par défaut est suspendResumable.|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet à la file d'attente contrôlée par l'emplacement de réception.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</queue><batchSize>20</batchSize><transactional>false</transactional><serialProcessing>false</serialProcessing><onFailure>suspendResumable</onFailure><uri>FORMATNAME:DIRECT=OS:.\PRIVATE$\QUEUE</uri></Config></AdapterConfig></CustomProps>  
```  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi d'un adaptateur MSMQ.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|File d'attente|VT_BSTR|Spécifier la file d'attente de destination.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|maximumMessageSiz|VT_BSTR|Indiquer la taille maximale en kilo-octets (ko) des messages que vous envoyez à la file d'attente spécifiée.|Les valeurs valides sont comprises entre 1 et 4294967295, si les propriétés segmentationSupport et transactional sont définies sur true. Sinon, les valeurs valides s'étendent de 1 à 4095.|La valeur par défaut est 1024.|  
|acknowledgeType|VT_BSTR|Spécifier un ou plusieurs types d'accusés de réception.|Les valeurs valides sont les membres du .NET **System.Messaging.AcknowledgeTypes** énumération.|La valeur par défaut est Aucun.|  
|administrationQueue|VT_BSTR|Spécifier la file d'attente de l'administration MSMQ.|Aucune|Aucune|  
|timeOut|VT_BSTR|Indiquer le délai maximal pendant lequel attendre que les messages atteignent la file d'attente de destination.|Cette propriété s'applique uniquement lorsque la propriété transactional est définie sur true.<br /><br /> -Les valeurs valides sont 1 et 10675199 lorsque vous spécifiez une valeur de propriété timeoutunits est jours.<br />-Les valeurs valides sont 1 et 596523 lorsque vous spécifiez une valeur de propriété timeoutunits est heures.<br />-Les valeurs valides sont 1 et 35791394 lorsque vous spécifiez une valeur de propriété timeoutunits est minutes.<br />-Les valeurs valides sont 1 et 2147483647 lorsque vous spécifiez une valeur de propriété timeoutunits est secondes.|Aucune|  
|priority|VT_BSTR|Spécifier la priorité du message.|Les valeurs valides sont les membres du .NET **System.Messaging.MessagePriority** énumération.|Aucune|  
|recoverable|VT_BSTR|Spécifiez s’il faut garantir la récupération d’un message.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|encryptionAlgorithm|VT_BSTR|Spécifier l'algorithme de chiffrement à utiliser.|Les valeurs valides sont les membres du .NET **System.Messaging.EncryptionAlgorithm** énumération.|La valeur par défaut est Aucun.|  
|useAuthentication|VT_BSTR|Indiquer si vous voulez utiliser l'authentification.|Utilisez cette propriété en combinaison avec la propriété certificate pour vérifier le message. Accédez aux files d'attente à l'aide des propriétés userName et password.|Aucune|  
|certificate|VT_BSTR|Spécifier le certificat utilisé pour vérifier les messages.|Entrer l'empreinte de certificat de 40 caractères.|Aucune|  
|segmentationSupport|VT_BSTR|Spécifier si la segmentation est prise en charge.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|transactionnels|VT_BSTR|Indiquer si vous voulez prendre en charge l'envoi des messages dans le contexte d'une transaction distribuée Microsoft (MSDTC).|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|useJournalQueue|VT_BSTR|Spécifier si vous voulez enregistrer une copie du message à chacun de ses traitements.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est false.|  
|useDeadLetterQueue|VT_BSTR|Spécifier si vous voulez envoyer les messages vers la file d'attente des messages non distribués en cas d'échec.|Les valeurs valides sont :<br /><br /> -true<br />-false|La valeur par défaut est true.|  
|ackTypeEnumsValue|VT_BSTR|Spécifier l'opérateur OR au niveau du bit des valeurs associées aux valeurs acknowledgeType spécifiées.|Aucune|La valeur par défaut est 0 :|  
|timeOutUnits|VT_BSTR|Spécifier l'unité à utiliser conjointement avec la valeur spécifiée pour la propriété timeOut.|Les valeurs valides sont :<br /><br /> -Jours d’utilisation<br />-Heures<br />-Minutes<br />-Secondes|La valeur par défaut est Jours.|  
|userName|VT_BSTR|Définir le nom d'utilisateur à utiliser pour une file d'attente distante.|La valeur par défaut est vide.|  
|password|VT_BSTR|Spécifier le mot de passe à utiliser conjointement avec la valeur spécifiée pour la propriété userName, pour un accès à une file d'attente distante.|Cette valeur est toujours masquée lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|La valeur par défaut est vide.|  
|bodyType|VT_BSTR|Spécifier le type du corps de message dans MSMQ.|Les valeurs valides sont membres du .NET **VarEnum** énumération.|La valeur par défaut est 8209.|  
|uri|VT_BSTR|Spécifier le chemin d'accès complet vers la file d'attente de destination.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><queue>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</queue><maximumMessageSize>1024</maximumMessageSize><acknowledgeType>None</acknowledgeType><administrationQueue>Direct=OS:TestServer\Private$\AdminQueue</administrationQueue><timeOut>4</timeOut><priority>Normal</priority><recoverable>false</recoverable><encryptionAlgorithm>None</encryptionAlgorithm><useAuthentication>false</useAuthentication><segmentationSupport>false</segmentationSupport><transactional>false</transactional><useJournalQueue>false</useJournalQueue><useDeadLetterQueue>true</useDeadLetterQueue><ackTypeEnumsValue>0</ackTypeEnumsValue><timeOutUnits>Days</timeOutUnits><userName>TestUser</userName><password>******</password><bodyType>8209</bodyType><uri>FORMATNAME:DIRECT=OS:TESTSERVER\PRIVATE$\DESTQUEUE</uri></Config></AdapterConfig>  
```  
  
> [!NOTE]
>  Lorsque vous spécifiez les données de configuration TransportTypeData pour un adaptateur qui est construit à l’aide de l’infrastructure d’adaptateurs, les paires nom/valeur utilisées doivent toutes être stockées dans le \<AdapterConfig\> élément. Étant donné que le \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données, puis le \< \> caractères dans les données doivent être échappés.