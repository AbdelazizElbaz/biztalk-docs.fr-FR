---
title: Adaptateur file | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: File adapters
ms.assetid: e4f6e94b-89b8-42ba-a4c2-a629f1107bb1
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceb4f0728eb6fac66fb0fc5f84b117b37ba84121
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter"></a>Adaptateur FILE
L'adaptateur FILE transfère les fichiers vers et à partir de Microsoft BizTalk Server. L’adaptateur File est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d’envoi.  
  
 Cette section décrit la prise en charge des workflows et traitements par lot pour les adaptateurs de réception et d'envoi FILE.  
 
## <a name="file-receive-adapter"></a>Adaptateur de réception File  
  
Utilisez le fichier adaptateur de réception pour lire les messages à partir de fichiers et les envoyer au serveur. L’adaptateur de réception lit le fichier et crée un objet BizTalk Message, afin que BizTalk Server puisse traiter le message. Lors de la lecture à partir du fichier, l'adaptateur verrouille le fichier pour s'assurer qu'aucune modification ne puisse être apportée au contenu du fichier.  
  
> [!NOTE] 
> L'adaptateur de réception FILE ne récupère pas les fichiers en lecture seule ou les fichiers système.  
  
 L'adaptateur de réception FILE lit les messages à partir de fichiers présents sur des systèmes de fichiers locaux ou des partages réseau. Lorsque l'emplacement spécifié sur un partage réseau est indisponible du fait de problèmes réseau, l'adaptateur de réception tente une nouvelle opération de lecture (le nombre de tentatives peut être configuré dans la console Administration de BizTalk Server). Après la lecture du message et son acceptation par le moteur de messagerie BizTalk, l'adaptateur de réception supprime le fichier du système de fichiers ou du partage réseau. Si le message a été lu mais que le pipeline n'a pas pu traiter le message, l'adaptateur le place dans la file d'attente de messages interrompus, puis supprime le fichier du système de fichiers ou du partage réseau. Si l'adaptateur de réception FILE ne peut pas envoyer (ou interrompre) le message à la base de données MessageBox, il ne supprime pas le fichier original du système de fichiers ou du partage réseau.  
  
 Vous pouvez également configurer l'adaptateur de réception FILE pour renommer des fichiers lors de leur traitement. Vous devez renommer des fichiers pour vous assurer que l'adaptateur de réception ne génère pas de messages en double si l'emplacement de réception est arrêté et redémarré. Il s'agit d'une option configurable pour les emplacements de réception FILE. Par défaut, le changement de nom est désactivé. Lorsqu'il est activé, l'adaptateur de réception FILE ajoute l'extension .BTS-WIP au fichier. L'adaptateur de réception lit ensuite les messages à partir du fichier renommé dans l'emplacement de réception, puis l'envoie au serveur. Après l'envoi d'un fichier par l'adaptateur de réception, ce dernier supprime le fichier renommé du système de fichiers ou du partage réseau. Si un message a été lu mais que son traitement a échoué dans le pipeline, l'adaptateur de réception le place dans la file d'attente de messages interrompus de la base de données MessageBox, puis supprime le fichier renommé du partage réseau.  
  
> [!NOTE] 
> Renommer les fichiers n'a aucun impact sur les performances.  
  
 Si l'adaptateur de réception FILE lit le message mais ne le stocke pas dans la base de données MessageBox, le fichier renommé retrouve son nom original, sans l'extension .BTS-WIP. Notez que l'adaptateur de réception ne lit pas les fichiers avec l'extension .BTS-WIP si l'option de changement de nom est activée.  
  
#### <a name="using-file-change-notifications-and-polling"></a>À l’aide de notifications de modification de fichier et d’interrogation
  
 L'adaptateur de réception FILE s'appuie sur les notifications de modification de fichier Windows pour déterminer quand récupérer un fichier du répertoire ou du partage spécifié. Si l'adaptateur de réception FILE reçoit une notification de modification de fichier Windows avant l'écriture complète du fichier dans le répertoire ou le partage spécifié, alors le fichier est verrouillé et l'adaptateur de réception FILE ne récupère pas le fichier. Dans ce scénario, la réception de fichier adaptateur sera activement interroger le répertoire spécifié ou partager à le **l’intervalle d’interrogation (ms)** spécifié sur le **paramètres avancés** boîte de dialogue disponible lors de la configuration un Emplacement de réception du fichier. Lorsque l'adaptateur de réception FILE interroge un répertoire ou un partage, il récupère les fichiers déverrouillés du partage et les envoie à la base de données MessageBox.  
  
> [!NOTE]
>  L'adaptateur FILE [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a été testé uniquement sur le système de fichiers NTFS qui le prend en charge.  
  
 Avec les notifications de modification de fichier Windows suivantes, l'adaptateur de réception FILE récupère un fichier de l'emplacement spécifié :  
  
 `FILE_NOTIFY_CHANGE_ATTRIBUTES`
  
 Toute modification d'attribut dans la sous-arborescence ou le répertoire surveillé génère le renvoi d'une opération d'attente d'une notification de modification.  
  
 `FILE_NOTIFY_CHANGE_FILE_NAME`  
  
 Toute modification de nom de fichier dans la sous-arborescence ou le répertoire surveillé génère le renvoi d'une opération d'attente d'une notification de modification. Les modifications incluent le changement, la création ou la suppression d'un nom de fichier.  
  
 `FILE_NOTIFY_CHANGE_SIZE`  
  
 Toute modification de taille de fichier dans la sous-arborescence ou le répertoire surveillé génère le renvoi d'une opération d'attente d'une notification de modification. Le système d'exploitation détecte une modification de la taille de fichier uniquement lorsque le fichier est écrit sur le disque. Pour les systèmes d'exploitation utilisant la mise en cache de manière intensive, la détection se produit uniquement lorsque le cache est suffisamment purgé.  
  
 `FILE_NOTIFY_CHANGE_LAST_WRITE`  
  
 Toute modification de l'heure de dernière écriture des fichiers dans la sous-arborescence ou le répertoire surveillé génère le renvoi d'une opération d'attente d'une notification de modification. Le système d'exploitation détecte une modification de l'heure de dernière écriture uniquement lorsque le fichier est écrit sur le disque. Pour les systèmes d'exploitation utilisant la mise en cache de manière intensive, la détection se produit uniquement lorsque le cache est suffisamment purgé.  
  
 Pour plus d’informations sur la **FindFirstChangeNotification** fonction voir [https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx](https://msdn.microsoft.com/library/windows/desktop/aa364417(v=vs.85).aspx).  
  
### <a name="file-receive-adapter-batching-support"></a>Prise en charge du traitement par lot par l'adaptateur de réception FILE
  
 L'adaptateur de réception FILE envoie des messages au serveur par lots. L'adaptateur de réception FILE commence par créer un seul lot par emplacement de réception en collectant tous les fichiers lisibles disponibles dans l'emplacement de réception. Les lots sont envoyés à la base de données MessageBox par l'adaptateur de réception, une fois que tous les fichiers disponibles ont été collectés ou que le nombre de fichiers collectés dépasse la taille maximale du lot.  
  
 Une fois que tous les messages du lot ont été lus et envoyés à la base de données MessageBox, l'adaptateur de réception FILE supprime les fichiers correspondants de l'emplacement de réception. Si certains messages du lot n'ont pas été traités correctement, l'adaptateur de réception FILE les interrompt et supprime les fichiers correspondants de l'emplacement de réception. Si certains ou tous les messages ne peuvent pas être stockés dans la base de données MessageBox, toute l'opération de traitement par lot est annulée et tous les fichiers correspondants restent en l'état dans l'emplacement de réception.  
  
## <a name="file-send-adapter"></a>Adaptateur d'envoi FILE
  
 L'adaptateur d'envoi FILE transmet des messages depuis la base de données MessageBox vers une adresse de destination (URL) spécifiée. Vous définissez l'URL, composée d'un chemin d'accès et d'un nom de fichier, à l'aide de caractères génériques liés aux propriétés de contexte du message. L'adaptateur d'envoi FILE fait correspondre les caractères génériques au nom de fichier réel avant d'écrire le message dans le fichier.  
  
 Lors de l'écriture d'un message dans un fichier, l'adaptateur d'envoi FILE obtient le contenu du message du corps de l'objet de message BizTalk. L'adaptateur d'envoi FILE ignore les autres parties du message dans l'objet de message BizTalk. Une fois que l'adaptateur FILE a écrit le message dans un fichier, il supprime le message de la base de données MessageBox. L'adaptateur FILE écrit des fichiers dans le système de fichiers soit directement, soit à l'aide du cache du système de fichiers qui peut améliorer les performances, en particulier pour les fichiers volumineux.  
  
### <a name="file-send-adapter-batching-support"></a>Prise en charge du traitement par lot par l'adaptateur d'envoi FILE
  
 L'adaptateur d'envoi FILE obtient des lots de messages de la base de données MessageBox et les écrit dans des fichiers dans des emplacements de destination, sur le système de fichiers ou le partage réseau. La taille des lots de l'adaptateur d'envoi FILE ne peut pas être configurée ; elle est prédéfinie sur 20. Si BizTalk Server ne peut pas écrire certains messages d'un lot dans des fichiers, le système renvoie ces messages à la base de données MessageBox pour une nouvelle tentative de traitement. Vous pouvez configurer l'intervalle entre chaque tentative, ainsi que le nombre de tentatives, à l'aide de la console Administration de BizTalk Server.  
  
 
## <a name="in-this-section"></a>Contenu de cette section  
  
-   [Configurer l’adaptateur de fichier](../core/configure-the-file-adapter.md) 
  
-   [Restrictions relatives à la configuration de l’adaptateur de fichier](../core/restrictions-when-configuring-the-file-adapter.md)  
