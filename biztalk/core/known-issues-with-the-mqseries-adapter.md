---
title: "Problèmes connus avec l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c36bcabb-e1eb-455c-8384-00d4682464d3
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe3093416a10b6b66867dcb2e3629de8f25e5aca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-mqseries-adapter"></a>Problèmes connus avec l'adaptateur MQSeries
Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.  
  
## <a name="know-issues"></a>Problèmes connus  
  
#### <a name="access-denied-errors-occur-when-attempting-to-send-or-receive-messages"></a>Des erreurs Accès refusé se produisent lors de tentatives d'envoi ou de réception de messages  
  
##### <a name="problem"></a>Problème  
 Lorsque vous utilisez l'adaptateur MQSeries pour envoyer des messages à un serveur ou en recevoir de sa part, des messages d'erreur similaires aux suivants sont consignés dans le journal de l'application dans l'Observateur d'événements :  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
```  
The adapter failed to transmit message going to send port "MQS://servername/queuename". It will be retransmitted after the retry interval specified for this Send Port. Details: "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
> [!NOTE]
>  Dans ce message d’erreur, *nom_serveur* est le nom du serveur et *queuename* est le nom de la file d’attente.  
  
 De plus, lorsque vous tentez de créer l'emplacement de réception ou le port d'envoi qui est configuré pour utiliser l'adaptateur BizTalk pour MQSeries, le message d'avertissement suivant peut s'afficher dans l'Observateur d'événements :  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
##### <a name="cause"></a>Cause  
 Ce problème peut se produire si un ou plusieurs des conditions suivantes sont vraies :  
  
-   Le compte hôte de l'adaptateur MQSeries ne dispose pas des autorisations requises pour l'application MQSAgent COM+ sur le serveur MQSeries.  
  
-   Sur un serveur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], le compte de l'hôte de l'adaptateur MQSeries ne fait pas partie du groupe d'utilisateurs Distributed COM sur le serveur MQSeries.  
  
##### <a name="resolution"></a>Résolution  
 Pour résoudre ce problème, utilisez les méthodes ci-dessous. Si une méthode ne résout pas le problème, essayez la suivante.  
  
 **Méthode 1 : Activer l’accès COM + réseau sur Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-ordinateur**  
  
 Activer l’accès COM + réseau sur Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-en fonction d’ordinateur en suivant les étapes décrites dans [comment activer l’accès COM + réseau dans Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=67076).  
  
 **Méthode 2 : Configurer les paramètres MSDTC**  
  
 Suivez les étapes de la **définir les options de Configuration de la sécurité MSDTC appropriées sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]**  section de [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) pour configurer les paramètres MSDTC.  
  
 **Méthode 3 : Vérifiez que le compte d’ordinateur hôte est ajouté au rôle de l’application MQSAgent COM +**  
  
 Vérifiez que le compte hôte de l'adaptateur MQSeries est ajouté au rôle créé dans l'application MQSAgent COM+ sur l'hôte MQSeries. Vous pouvez vérifier ce point dans l'interface de la console de gestion Services de composants.  
  
 **Méthode 4 : Vérifiez que le compte hôte de l’adaptateur MQSeries est membre du groupe utilisateurs du modèle COM distribué**  
  
 Sur un serveur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], consultez les membres du groupe du compte de l'hôte de l'adaptateur MQSeries. Assurez-vous que le compte est un membre de la **utilisateurs Distributed COM** groupe sur le serveur MQSeries sur lequel l’application MQSAgent COM + est installée.  
  
 Pour plus d’informations sur les améliorations de sécurité DCOM dans Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], consultez [améliorations de sécurité DCOM](http://go.microsoft.com/fwlink/?LinkId=67077).  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage de l’adaptateur MQSeries](../core/troubleshooting-the-mqseries-adapter.md)