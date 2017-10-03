---
title: "Configuration des ordinateurs hôtes et les Instances d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a36a73a4-cc5f-47d6-b56f-7871684c4489
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55dda06d447d9e27c7c8b491986b499003c0bb73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-hosts-and-host-instances"></a>Configuration des ordinateurs hôtes et les Instances d’hôte
Un hôte BizTalk représente un ensemble logique de zéro ou plusieurs processus d’exécution dans lequel vous pouvez déployer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services et des artefacts (tels que des gestionnaires d’adaptateur, emplacements de réception et orchestrations). Une instance d’hôte est l’instance physique d’un ordinateur hôte sur un ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur les hôtes BizTalk et les instances d’hôte, consultez [hôtes](http://go.microsoft.com/fwlink/?LinkId=154189) (http://go.microsoft.com/fwlink/?LinkId=154189) et [Instances d’hôte](http://go.microsoft.com/fwlink/?LinkId=154190) (http://go.microsoft.com/fwlink/?LinkId=154190).  
  
 Pour plus d’informations sur la gestion des hôtes BizTalk et les instances d’hôte, consultez [gestion d’hôtes BizTalk et les Instances d’hôte](http://go.microsoft.com/fwlink/?LinkId=154191) (http://go.microsoft.com/fwlink/?LinkId=154191).  
  
 Pour plus d’informations sur la façon de configurer un hôte de suivi dédié, consultez [configuration d’un hôte dédié de suivi](../technical-guides/configuring-a-dedicated-tracking-host.md).  
  
## <a name="separating-host-instances-by-functionality"></a>Séparation des Instances d’hôte par fonctionnalité  
 Outre les aspects de la haute disponibilité de la configuration de l’instance hôte, vous devez séparer l’envoi, réception, traitement et le suivi des fonctionnalités dans plusieurs hôtes. Cela fournit une grande souplesse lors de la configuration de la charge de travail dans votre groupe BizTalk et constitue le principal moyen de répartir le traitement d’un groupe BizTalk. Cela vous permet également d’arrêter un ordinateur hôte sans affecter les autres hôtes. Pouvez par exemple, si vous souhaitez arrêter l’envoi de messages pour leur permettre de file d’attente dans la base de données MessageBox, tout en autorisant la trafic entrante réception de messages se produise.  
  
 Séparation des instances d’hôte par la fonctionnalité fournit également les avantages suivants :  
  
-   Chaque instance d’hôte possède son propre ensemble de ressources, telles que la mémoire, les poignées et les threads dans le pool de threads .NET.  
  
-   Plusieurs hôtes BizTalk permet également de réduire la contention sur les tables de file d’attente de hôte de base de données MessageBox, car chaque hôte possède ses propres tables de file d’attente de travail dans la base de données MessageBox.  
  
-   La limitation est implémentée dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au niveau de l’hôte. Cela vous permet de définir différentes caractéristiques de limitation pour chaque hôte.  
  
-   La sécurité est implémentée au niveau de l’hôte ; chaque hôte s’exécute sous une identité Windows discrète. Cela vous permettrait, par exemple, pour donner à **Host_A** l’accès à **FileShare_B**, tout en autorisant ne pas un des autres ordinateurs hôtes à accéder au partage de fichiers.  
  
    > [!NOTE]  
    >  Bien qu’il existe des avantages à la création des instances d’hôte supplémentaires, il existe également des inconvénients potentiels si trop d’instances d’hôte sont créées. Chaque instance d’hôte est un service Windows (BTSNTSvc.exe ou BTSNTSvc64.exe), qui génère une charge supplémentaire par rapport à la base de données MessageBox et consomme des ressources de l’ordinateur (par exemple, le processeur, mémoire, threads).  
  
 Pour plus d’informations sur la modification [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] propriétés d’hôte, consultez [comment modifier les propriétés de l’hôte](http://go.microsoft.com/fwlink/?LinkId=154192) (http://go.microsoft.com/fwlink/?LinkId=154192).  
  
##  <a name="BKMK_MemLimit"></a>Nombre maximal pratiques d’utilisation de la mémoire d’une Instance de l’hôte BizTalk 32 bits  
 les processus 32 bits sur un système de d’exploitation Windows 32 bits avec 3 Go ensemble ont 3 gigaoctets (Go) de mémoire adressable si le processus est le « grand adresse prenant en charge » (autrement dit, le fichier exécutable a l’indicateur IMAGE_FILE_LARGE_ADDRESS_AWARE défini dans l’en-tête de l’image).  Le processus d’hôte BizTalk, qui est « adresse volumineux prenant en charge », peut adresser 3 Go de mémoire sur le système d’exploitation de Windows avec un ensemble de 3 Go.  De même, les processus 32 bits sur un système d’exploitation de Windows 64 bits (AMD64) ont des 4 Go de mémoire adressable, si le processus est le « grand adresse prenant en charge ».  Là encore, le processus hôte BizTalk, en cours de « grande adresse prenant en charge », pouvez adresser des 4 Go de mémoire lors de l’exécution en tant qu’un processus 32 bits sur un système d’exploitation de Windows 64 bits. les processus 64 bits sur un système d’exploitation de Windows 64 bits (AMD64) ont 8 téraoctets de mémoire adressable.  
  
 Même si la quantité maximale de mémoire adressable par un processus sur un système d’exploitation Windows 32 bits (sans le commutateur/3 GB) est de 2 Go, une application .NET (par exemple, une instance d’hôte BizTalk) recevront des erreurs de mémoire insuffisante avant les « octets virtuels » atteint 2 Go. Le tableau ci-dessous récapitule ces différences et inclut des limites pratiques pour les octets virtuels et les octets privés.  
  
|Traiter|Windows du système d’exploitation|Mémoire adressable (avec un grand adresse prenant en charge les processus)|Limite pratique pour les octets virtuels|Limite pratique pour PrivateBytes|  
|-------------|----------------|---------------------------------------------------------------|---------------------------------------|--------------------------------------|  
|32 bits|32 bits|2 Go|1400 MO|800 MO|  
|32 bits|32 bits avec 3 Go|3 GO|2 400 MO|1 800 MO|  
|32 bits|64 bits|4 Go|3400 MO|2800 MO|  
|64 bits|64 bits|8 téraoctets|-|-|  
  
 Pour plus d'informations, consultez :  
  
-   [Analyse des performances ASP.NET et alertes aux administrateurs](http://go.microsoft.com/fwlink/?LinkId=151856) (http://go.microsoft.com/fwlink/?LinkId=151856)  
  
-   [Limites de mémoire pour les versions Windows](http://go.microsoft.com/fwlink/?LinkId=151857) (http://go.microsoft.com/fwlink/?LinkId=151857)  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : Configuration de BizTalk Server](../technical-guides/checklist-configuring-biztalk-server.md)   
 [Configuration d’un hôte de suivi dédié](../technical-guides/configuring-a-dedicated-tracking-host.md)