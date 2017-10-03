---
title: "Propriétés de Configuration de l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, properties
- SMTP adapters, code sample
- SMTP adapters, send ports
- send ports, adapters
ms.assetid: 6af287f5-272a-42d7-9878-99a4157c06ce
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8b8bb0c5562c07260a9d411b8144bd7a576eb3a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur SMTP
Ce tableau répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur SMTP.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|DeliveryReceipt|VT_BOOL|Indiquer qu'un message électronique de confirmation doit être envoyé après livraison du message.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|De|VT_BSTR|Indiquer l'adresse de messagerie à insérer dans l'en-tête SMTP De.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Aucune|  
|MessagePartsAttachments|VT_UI4|Indiquer la méthode utilisée pour joindre les parties de message BizTalk à un message électronique.|Les valeurs valides sont :<br /><br /> -0 (ne pas joindre les parties de message)<br />-1 (joindre que le corps<br />-2 (joindre toutes les parties)|La valeur par défaut est 0 (Ne pas joindre les parties du message).|  
|CC|VT_BSTR|Indiquer l'adresse électronique à laquelle envoyer une copie carbone du message.|Longueur maximale : 1024|Vous pouvez entrer plusieurs adresses.|  
|SMTPAuthenticate|VT_UI4|Les valeurs valides sont :<br /><br /> -0 (ne pas authentifier)<br />-1 (authentification de base)<br />-2 (compte de processus (NTLM))|Si cette valeur n'est pas définie, la valeur par défaut est appliquée.|La valeur par défaut indique que le port d'envoi SMTP utilisera les valeurs de configuration du gestionnaire d'envoi.|  
|Utilisateur|VT_BSTR|Indiquer le nom d'utilisateur nécessaire à l'authentification sur le serveur SMTP.|Cette propriété ne requiert une valeur que si la propriété SMTPAuthenticate est définie sur 1 (Authentification de base).<br /><br /> Longueur minimale : 0<br /><br /> Longueur maximale : 256|Aucune|  
|EmailBodyFileCharset|VT_BSTR|Indiquer le jeu de caractères de codage du fichier envoyé.|Cette propriété ne requiert une valeur que si la propriété EmailBodyFile est définie.|L'adaptateur SMTP n'applique pas le codage spécifié au fichier, cette option vise uniquement à préciser de quelle manière le fichier envoyé est déjà codé.<br /><br /> La valeur par défaut est utf-8.|  
|EmailBodyText|VT_BSTR|Indiquer le texte à utiliser pour le corps du message électronique à envoyer.|Longueur maximale : 64 Ko|Aucune|  
|ReadReceipt|VT_BOOL|Indiquer qu'un message électronique de confirmation doit être envoyé après lecture du message.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|Pour|VT_BSTR|Indiquer l'adresse électronique à laquelle envoyer les messages.|Aucune|Aucune|  
|EmailBodyFile|VT_BSTR|Indiquer le chemin d'accès au fichier devant être utilisé pour le corps du message électronique à envoyer.|Longueur maximale : 256 caractères|Il est recommandé de spécifier un chemin d’accès sur un partage de fichiers qui est accessible à partir de tous les serveurs BizTalk du groupe BizTalk Server à utiliser en production.|  
|Subject|VT_BSTR|Indiquer l'en-tête objet du message.|Longueur minimale : 0<br /><br /> Longueur maximale : 256|Aucune|  
|Mot de passe|VT_NULL|Indiquer le mot de passe nécessaire à l'authentification sur le serveur SMTP.|Cette propriété ne requiert une valeur, sauf si la propriété SMTPAuthenticate est définie sur 1 (authentification de base).<br /><br /> Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
|Pièces jointes|VT_BSTR|Indiquer le chemin d'accès au fichier devant être joint au message électronique à envoyer.|Longueur maximale : 256 caractères|Aucune|  
|SMTPHost|VT_BSTR|Indiquer le nom du serveur SMTP à utiliser pour l'envoi des messages.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.<br /><br /> Longueur maximale : 256 caractères|Aucune|  
|EmailBodyTextCharset|VT_BSTR|Indiquer le jeu de caractères à utiliser pour coder le corps du message électronique à envoyer.|Cette propriété ne requiert une valeur que si la propriété EmailBodyText est définie.|La valeur par défaut est utf-8.|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<DeliveryReceipt vt="11">-1</DeliveryReceipt>  
<From vt="8">someone@microsoft.com</From>  
<MessagePartsAttachments vt="19">0</MessagePartsAttachments>  
<CC vt="8">someoneelse@microsoft.com</CC>  
<SMTPAuthenticate vt="19">1</SMTPAuthenticate>  
<Username vt="8">OverrideUsername</Username>  
<EmailBodyFileCharset vt="8">utf-8</EmailBodyFileCharset>  
<EmailBodyText vt="8">Email Body Text</EmailBodyText>  
<ReadReceipt vt="11">-1</ReadReceipt>  
<To vt="8">recipient@microsoft.com</To>  
<EmailBodyFile vt="8">C:\emailbodyfile.xml</EmailBodyFile>  
<Subject vt="8">test mail</Subject>  
<Password vt="1" />  
<Attachments vt="8">C:\attachment.txt</Attachments>  
<SMTPHost vt="8">emailhost</SMTPHost>  
<EmailBodyTextCharset vt="8">utf-8</EmailBodyTextCharset>  
</CustomProps>  
```