---
title: "Problèmes connus avec l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aaf448c-0035-4648-910b-ae2f15106342
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2690803346efc5931a88acd70be9d24af107156f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-file-adapter"></a>Problèmes connus avec l'adaptateur FILE
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="a-file-receive-location-is-disabled"></a>Un emplacement de réception de fichier est désactivé  
  
##### <a name="problem"></a>Problème  
 Un emplacement de réception de fichier devient désactivé.  
  
##### <a name="cause"></a>Cause  
 L'adaptateur de réception FILE désactive l'emplacement de réception si l'un des cas suivants se présente :  
  
-   L'adaptateur de réception FILE ne peut pas accéder à l'emplacement de réception sur le système de fichiers ou le partage réseau, car le chemin spécifié n'existe pas. Pour un partage réseau, l'adaptateur de réception FILE désactive l'emplacement de réception lorsque le nombre de tentatives maximal est atteint.  
  
-   L'adaptateur de réception FILE ne peut pas accéder à l'emplacement de réception sur le système de fichiers ou le partage réseau, car le compte utilisé par l'instance d'hôte associée ne dispose pas des autorisations en lecture/écriture pour cet emplacement. Pour un partage réseau, l'adaptateur de réception FILE désactive l'emplacement de réception lorsque le nombre de tentatives maximal est atteint.  
  
-   Des noms de fichier comportant plus de 256 caractères sont présents dans l'emplacement de réception.  
  
##### <a name="resolution"></a>Résolution  
  
-   Assurez-vous que le chemin ou le partage spécifié existe bien.  
  
-   Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour le fichier instance hôte du Gestionnaire de réception est en lecture et écriture spécifiée à l’emplacement de réception.  
  
-   Assurez-vous que les noms des fichiers écrits dans le dossier contrôlé par l'adaptateur de réception FILE n'excèdent pas 256 caractères.  
  
#### <a name="files-are-not-being-read-from-the-specified-receive-location"></a>Les fichiers ne sont pas lus à partir de l'emplacement de réception spécifié  
  
##### <a name="problem"></a>Problème  
 L'adaptateur de réception FILE ne parvient pas à lire un fichier dans l'emplacement de réception indiqué. Lorsque l'adaptateur de réception FILE rencontre un tel fichier, il consigne une erreur dans le journal des événements et laisse le fichier dans l'emplacement de réception.  
  
##### <a name="cause"></a>Cause  
 L'adaptateur de réception FILE ne lit pas un fichier dans l'emplacement de réception si l'une des conditions suivantes est vraie :  
  
-   Le fichier est en lecture seule.  
  
-   Le fichier comporte un attribut système.  
  
-   L'adaptateur de réception FILE ne dispose pas des autorisations en lecture/écriture pour le fichier.  
  
-   Des noms de fichier comportant plus de 256 caractères sont présents dans l'emplacement de réception.  
  
##### <a name="resolution"></a>Résolution  
  
-   Assurez-vous que les fichiers de l'emplacement de réception spécifié ne sont pas marqués en « lecture seule ».  
  
-   Assurez-vous que les fichiers de l'emplacement de réception spécifié ne sont pas marqués avec un attribut système.  
  
-   Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour le fichier instance hôte du Gestionnaire de réception est en lecture et écriture spécifiée à l’emplacement de réception.  
  
-   Assurez-vous que les noms des fichiers écrits dans le dossier contrôlé par l'adaptateur de réception FILE n'excèdent pas 256 caractères.  
  
#### <a name="messages-are-not-being-sent-by-the-file-send-adapter"></a>Messages non envoyés par l'adaptateur d'envoi FILE.  
  
##### <a name="problem"></a>Problème  
 L'adaptateur d'envoi FILE ne parvient pas à envoyer un message dans le répertoire ou le partage de fichiers spécifié.  
  
 En cas d'échec de l'écriture d'un message dans le répertoire ou le partage de fichiers spécifié, une erreur est consignée dans le journal des événements de l'ordinateur BizTalk Server et la séquence d'événements suivante se produit :  
  
1.  L'adaptateur d'envoi FILE tente à nouveau l'opération d'écriture.  
  
2.  L'adaptateur d'envoi FILE tente de remettre le fichier en faisant appel au transport secondaire (s'il a été configuré).  
  
3.  Le message est écrit dans la file d'attente des messages interrompus.  
  
##### <a name="cause"></a>Cause  
  
-   L'adaptateur d'envoi FILE ne peut pas accéder au répertoire à partir duquel les fichiers sont envoyés sur le système de fichiers ou le partage réseau, car le chemin spécifié n'existe pas.  
  
-   L'adaptateur d'envoi FILE ne peut pas écrire dans un fichier dans l'emplacement de destination sur le système de fichiers ou le partage réseau, car l'instance de l'hôte associée ne dispose pas des autorisations en écriture pour ce fichier ou cet emplacement.  
  
-   L’adaptateur d’envoi de fichier ne peut pas écrire dans le fichier spécifié, car il est en lecture seule ou est marqué avec la **système** attribut de fichier.  
  
##### <a name="resolution"></a>Résolution  
  
-   Assurez-vous que le chemin ou le partage spécifié existe bien.  
  
-   Vérifiez que le compte utilisé comme le **ouverture de session :** compte pour l’instance de hôte du Gestionnaire d’envoi de fichier a autorisations Lire et écrire sur le partage de fichier ou répertoire spécifié.  
  
-   Assurez-vous que les fichiers existants dans le répertoire ou le partage de fichiers indiqué ne sont pas marqués avec un attribut système.  
  
#### <a name="sending-a-file-using-the-file-adapter-is-very-slow"></a>L'envoi d'un fichier avec l'adaptateur FILE est très lent.  
  
##### <a name="problem"></a>Problème  
 Performances de l’adaptateur d’envoi de fichier est plus lent lorsque la **autoriser le cache lors de l’écriture** est définie sur **False**. Le **autoriser le cache lors de l’écriture** est définie sur **False** par défaut.  
  
##### <a name="cause"></a>Cause  
 Définition de la **autoriser le cache lors de l’écriture** propriété **False** peut réduire les performances car ce paramètre désactive l’utilisation de la mise en cache de fichiers par le système d’exploitation.  
  
##### <a name="resolution"></a>Résolution  
 Pour augmenter les performances du fichier envoyer la modification de l’adaptateur le **autoriser le cache lors de l’écriture** propriété **True** (cochez la case). Pour plus d’informations sur la **autoriser le cache lors de l’écriture** propriété, consultez [comment configurer un Port d’envoi File](http://msdn.microsoft.com/library/d801c5b7-da0a-4228-af0c-c2d450c251a9).  
  
> [!NOTE]
>  Définition de la **autoriser le cache lors de l’écriture** propriété **True** augmente le risque de perte de données dans le cas où le système d’exploitation rencontre un échec. Dans cette situation, toutes les données stockées dans le cache des fichiers en mémoire seraient perdues.  
  
#### <a name="zero-byte-files-received-by-the-file-adapter-are-deleted"></a>Les fichiers de zéro octet reçus par l'adaptateur FILE sont supprimés.  
  
##### <a name="problem"></a>Problème  
 Si l'adaptateur de réception FILE reçoit un fichier vide (zéro octet), ce fichier est supprimé et un avertissement similaire à l'avertissement suivant est écrit dans le journal des applications du serveur BizTalk :  
  
```  
Event Type:Warning  
Event Source:BizTalk Server 2009  
Event Category:BizTalk Server 2009   
Event ID:7182  
Date:8/30/2006  
Time:1:32:32 PM  
User:N/A  
Computer:BIZTALKSERVER  
Description:  
The FILE receive adapter deleted the empty file "C:\filesource\emptyfile.xml.BTS-WIP" without performing any processing.  
```  
  
##### <a name="cause"></a>Cause  
 Le comportement normal de l'adaptateur de réception FILE est de supprimer les fichiers de zéro octet.  
  
##### <a name="resolution"></a>Résolution  
 Aucune action n'est requise, ce comportement est normal.