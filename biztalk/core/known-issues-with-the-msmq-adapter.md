---
title: Problèmes connus avec l’adaptateur MSMQ | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce77cdac-79c1-4529-8f09-0fb1f87ca037
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f210d0e480a311aed0bed5d50f6a827bd6ea4e
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="known-issues-with-the-msmq-adapter"></a>Problèmes connus avec l'adaptateur MSMQ
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="msmq-adapter-receive-locations-do-not-process-documents"></a>Non-traitement des documents par les emplacements de réception de l'adaptateur MSMQ  
  
##### <a name="problem"></a>Problème  
 Emplacements de réception de l’adaptateur MSMQ ne traitera pas les documents.  
  
##### <a name="cause"></a>Cause  
 Si le nombre de threads disponibles est insuffisant dans la réserve de threads .NET associée à l'instance de l'hôte BizTalk sur laquelle est exécuté le gestionnaire de réception de l'adaptateur MSMQ, les emplacements de réception de ce dernier sont incapables de traiter les documents.  
  
##### <a name="resolution"></a>Résolution  
 Pour augmenter le nombre de threads disponibles dans le pool de threads .NET pour l’instance d’hôte, suivez les étapes de la **valeurs de thread CLR Hosting de l’hôte** section de la rubrique [que l’adaptateur affectent les paramètres de Configuration Performances](../core/configuration-parameters-that-affect-adapter-performance.md).  
  
 Étant donné que chaque MSMQ emplacement de réception qui est lié à un MSMQ réception gestionnaire requiert un thread de pool de threads .NET, définissez **MinIOThreads** et **MinWorkerThreads** à une valeur qui est supérieur ou égal à le nombre d’emplacements de réception MSMQ liés au Gestionnaire de réception. En conséquence, définissez la valeur de **MaxIOThreads** et **MaxWorkerThreads** et une valeur égale au nombre de MSMQ emplacements de réception liés au Gestionnaire de réception * 2 pour avoir une marge :  
  
|Entrée DWORD|Valeur recommandée|  
|-----------------|-----------------------|  
|MaxIOThreads|Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ * 2.|  
|MaxWorkerThreads|Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ * 2.|  
|MinIOThreads|Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ|  
|MinWorkerThreads|Nombre d'emplacements de réception MSMQ liés au gestionnaire de réception de l'adaptateur MSMQ|  
  
 Ces valeurs recommandées ne se factorisent pas dans les threads utilisés par d'autres gestionnaires d'adaptateur ou orchestrations exécutées dans l'instance de l'hôte de sorte que les valeurs sont augmentées en conséquence.  
  
#### <a name="msmq-adapter-receive-locations-shut-down-shortly-after-they-are-enabled"></a>Une fois activés, les emplacements de réception de l'adaptateur MSMQ ferment immédiatement  
  
##### <a name="problem"></a>Problème  
 Une fois activés, les emplacements de réception MSMQ ferment immédiatement  
  
##### <a name="cause"></a>Cause  
 Ce problème peut survenir si une instance locale du service Message Queuing qui ne fait pas partie d'un cluster n'est pas exécutée sur le même ordinateur que celui sur lequel l'instance d'hôte du gestionnaire de réception MSMQ est exécutée.  
  
##### <a name="resolution"></a>Résolution  
 Démarrez le service Message Queuing sur l'ordinateur sur lequel l'instance d'hôte du gestionnaire de réception MSMQ est exécutée. Le gestionnaire de réception de l'adaptateur MSMQ requiert qu'une instance locale du service Message Queuing soit exécutée même si une instance mise en cluster de ce service est exécutée sur le même ordinateur.  
  
#### <a name="sc-tool-causes-error-when-attempting-to-stop-service-for-host-instance"></a>L'outil SC provoque une erreur lors de la tentative d'arrêt du service pour l'instance de l'hôte  
  
##### <a name="problem"></a>Problème  
 Lorsque vous tentez d'utiliser l'outil SC (Sc.exe) pour fermer le service de l'instance d'hôte BizTalk, vous pouvez recevoir un message d'erreur semblable à ce qui suit :  
  
 **ControlService n’a pas pu 1053 :**  
  
 **Le service n’a pas répondu à la demande de démarrage ou de contrôle en temps voulu.**  
  
 Après avoir reçu ce message d'erreur, le service de l'instance d'hôte BizTalk est arrêté. Cependant, au moins deux minutes peuvent être nécessaires à l'outil SC pour arrêter le service.  
  
 Ce problème se produit lorsqu'un emplacement de réception de Microsoft Message Queuing est activé dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 En outre, un message d'erreur semblable à ce qui suit peut être consigné dans le journal système :  
  
 **Type d’événement : erreur**  
  
 **Source d’événement : Gestionnaire de contrôle de Service**  
  
 **Catégorie d’événement : aucun**  
  
 **ID d’événement : 7011**  
  
 **Description:**  
  
 **Délai d’attente (30 000 millisecondes) attend une réponse de transaction à partir du service BTSSvc$ BizTalkServerApplication.**  
  
##### <a name="resolution"></a>Résolution  
 Un correctif pris en charge est disponible auprès de Microsoft. Il permet toutefois de corriger uniquement le problème décrit dans cet article. Appliquez ce correctif logiciel uniquement aux systèmes confrontés à ce problème spécifique. Il se peut que ce correctif soit de nouveau testé ultérieurement. Toutefois, si ce problème ne vous affecte pas trop, il est recommandé de patienter avant d'installer le prochain Service Pack qui inclura ce correctif.  
  
 Pour obtenir le correctif et résoudre ce problème, envoyez une demande au service clientèle en ligne de Microsoft.  
  
> [!NOTE]
>  Si d'autres problèmes surviennent ou si un dépannage est nécessaire, il est possible que vous deviez créer une demande de service distincte. Les frais de dépannage habituels s'appliquent aux questions et problèmes de prise en charge supplémentaires qui ne correspondent pas à ce correctif.  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’adaptateur MSMQ](../core/troubleshooting-the-msmq-adapter.md)