---
title: "Problèmes connus avec l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e58f2db-9ec5-41fe-af02-9a7d60a217db
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e13ce12e8514eaa2b5843ba81eff4f505e65d9e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="known-issues-with-the-ftp-adapter"></a>Problèmes connus avec l'adaptateur FTP
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="data-may-be-duplicated-or-lost-when-you-receive-data-in-biztalk-server-by-using-the-ftp-adapter"></a>Certaines données peuvent être dupliquées ou perdues lors de la réception de données dans BizTalk Server à l'aide de l'adaptateur FTP.  
  
##### <a name="problem"></a>Problème  
 Certaines données sont dupliquées ou perdues lors de la réception de données dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à l'aide de l'adaptateur FTP.  
  
##### <a name="cause"></a>Cause  
 L'adaptateur FTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le protocole FTP client pour interroger le serveur FTP désigné et extraire des données du serveur en l'état. L'adaptateur FTP ne valide pas les données qu'il extrait. Il transmet le document extrait au moteur de messagerie BizTalk pour traitement, puis supprime le document d'origine du serveur FTP. Si l'adaptateur FTP extrait du serveur FTP un document encore en cours d'écriture par l'application hôte, ce document sera incomplet. S'il extrait une copie incomplète du document d'origine, des données risquent d'être dupliquées ou perdues dans les cas suivants :  
  
-   Si le document d'origine est encore en cours d'écriture par l'application hôte sur le serveur FTP, l'adaptateur FTP ne sera pas en mesure de le supprimer et extraira une autre copie du document à l'intervalle d'interrogation suivant configuré pour l'emplacement de réception. Cela entraînera la duplication du document.  
  
-   Si l'application hôte a terminé d'écrire le document sur le serveur FTP, le document sera supprimé. Cela provoquera la perte de données.  
  
##### <a name="resolution"></a>Résolution  
 Pour contourner cette erreur, effectuez l'une des opérations suivantes :  
  
-   Configurez l'application hôte pour qu'elle écrive dans un dossier temporaire du disque dur où réside le dossier FTP public et pour qu'elle transfère régulièrement le contenu du dossier temporaire vers le dossier FTP. Le dossier temporaire doit se trouver sur le même disque dur que le dossier FTP public, pour garantir une opération de transfert atomique. Une opération atomique est une opération fonctionnelle indivisible. Si vous écrivez des données dans le dossier FTP public avec l'adaptateur FTP de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez spécifier une propriété de dossier temporaire dans la boîte de dialogue Propriétés du transport FTP lors de la configuration du port d'envoi. Dans ce cas, assurez-vous que ce dossier réside sur le même disque physique que le dossier FTP public.  
  
-   Configurez l'emplacement de réception FTP pour qu'il fonctionne dans une fenêtre de service lorsque l'application hôte n'écrit pas de données vers le serveur FTP. Vous pouvez configurer cette fenêtre lors de la configuration des propriétés de l'emplacement de réception.  
  
#### <a name="ftp-adapter-does-not-support-revocation-checks-on-the-server-certificates"></a>L'adaptateur FTP ne prend pas en charge les vérifications de révocation sur les certificats de serveur  
  
##### <a name="problem"></a>Problème  
 L’adaptateur FTP dans BizTalk Server a été amélioré pour prendre en charge le transfert de fichiers sécurisé vers et depuis un serveur FTPS via SSL/TLS. La liste de révocation des certificats contient une liste des certificats qui ont été révoqués et ne sont plus valides. L'adaptateur FTP ne consulte pas cette liste pour authentifier le certificat de serveur.  
  
##### <a name="cause"></a>Cause  
 Par défaut, l'adaptateur FTP ne consulte pas la liste de révocation des certificats avant d'accepter un certificat de serveur.  
  
##### <a name="resolution"></a>Résolution  
 Aucune action n’est requise ; Ce comportement est normal.  
  
#### <a name="ftp-adapter-downloads-files-larger-than-max-file-size"></a>L'adaptateur FTP télécharge les fichiers dont la taille est supérieure à la taille de fichier maximale  
  
##### <a name="problem"></a>Problème  
 L'adaptateur de réception FTP télécharge les fichiers dont la taille est supérieure à la valeur de la propriété Taille maximale des fichiers des serveurs FTP suivants :  
  
-   AIX  
  
-   MVS  
  
-   AS400  
  
-   GXS  
  
##### <a name="cause"></a>Cause  
 Par défaut, l'adaptateur FTP ne respecte pas la taille maximale des fichiers lors du téléchargement de fichiers à partir de ces serveurs FTP.  
  
##### <a name="resolution"></a>Résolution  
 Aucune action n’est requise ; Ce comportement est normal.  
  
## <a name="see-also"></a>Voir aussi  
 [Pour configurer les emplacement de réception FTP](http://msdn.microsoft.com/library/1d8fde35-f787-4a5e-a8bd-8c418d0f75c3)   
 [Dépannage de l’adaptateur FTP](../core/troubleshooting-the-ftp-adapter.md)