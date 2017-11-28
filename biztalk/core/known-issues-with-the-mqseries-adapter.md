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
# <a name="known-issues-with-the-mqseries-adapter"></a><span data-ttu-id="70211-102">Problèmes connus avec l'adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="70211-102">Known Issues with the MQSeries Adapter</span></span>
<span data-ttu-id="70211-103">Cette section contient des informations qui peuvent vous permettre d'éviter certaines erreurs.</span><span class="sxs-lookup"><span data-stu-id="70211-103">This section contains information that may help you avoid errors.</span></span>  
  
## <a name="know-issues"></a><span data-ttu-id="70211-104">Problèmes connus</span><span class="sxs-lookup"><span data-stu-id="70211-104">Know Issues</span></span>  
  
#### <a name="access-denied-errors-occur-when-attempting-to-send-or-receive-messages"></a><span data-ttu-id="70211-105">Des erreurs Accès refusé se produisent lors de tentatives d'envoi ou de réception de messages</span><span class="sxs-lookup"><span data-stu-id="70211-105">Access Denied errors occur when attempting to send or receive messages</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="70211-106">Problème</span><span class="sxs-lookup"><span data-stu-id="70211-106">Problem</span></span>  
 <span data-ttu-id="70211-107">Lorsque vous utilisez l'adaptateur MQSeries pour envoyer des messages à un serveur ou en recevoir de sa part, des messages d'erreur similaires aux suivants sont consignés dans le journal de l'application dans l'Observateur d'événements :</span><span class="sxs-lookup"><span data-stu-id="70211-107">When you use the MQSeries adapter to send messages to or receive messages from an MQSeries server, error messages that are similar to the following are logged in the Application log in Event Viewer:</span></span>  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
```  
The adapter failed to transmit message going to send port "MQS://servername/queuename". It will be retransmitted after the retry interval specified for this Send Port. Details: "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
> [!NOTE]
>  <span data-ttu-id="70211-108">Dans ce message d’erreur, *nom_serveur* est le nom du serveur et *queuename* est le nom de la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="70211-108">In this error message, *servername* is the name of the server and *queuename* is the name of the queue.</span></span>  
  
 <span data-ttu-id="70211-109">De plus, lorsque vous tentez de créer l'emplacement de réception ou le port d'envoi qui est configuré pour utiliser l'adaptateur BizTalk pour MQSeries, le message d'avertissement suivant peut s'afficher dans l'Observateur d'événements :</span><span class="sxs-lookup"><span data-stu-id="70211-109">Additionally, when you try to create the receive location or the send port that is configured to use the BizTalk Adapter for MQSeries, you may receive the following warning message in Event Viewer:</span></span>  
  
```  
The adapter "MQSeries" raised an error message. Details "The adapter has encountered an 'Access Denied' error while attempting to contact the COM+ object on the MQSeries server. Ensure the BizTalk account is added to the Role on the MQSAgent COM+ application."  
```  
  
##### <a name="cause"></a><span data-ttu-id="70211-110">Cause</span><span class="sxs-lookup"><span data-stu-id="70211-110">Cause</span></span>  
 <span data-ttu-id="70211-111">Ce problème peut se produire si un ou plusieurs des conditions suivantes sont vraies :</span><span class="sxs-lookup"><span data-stu-id="70211-111">This issue may occur if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="70211-112">Le compte hôte de l'adaptateur MQSeries ne dispose pas des autorisations requises pour l'application MQSAgent COM+ sur le serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="70211-112">The host account for the MQSeries adapter does not have the required permissions for the MQSAgent COM+ application on the MQSeries server.</span></span>  
  
-   <span data-ttu-id="70211-113">Sur un serveur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], le compte de l'hôte de l'adaptateur MQSeries ne fait pas partie du groupe d'utilisateurs Distributed COM sur le serveur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="70211-113">On a [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based server, the host account for the MQSeries adapter is not a member of the Distributed COM Users group on the MQSeries server.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="70211-114">Résolution</span><span class="sxs-lookup"><span data-stu-id="70211-114">Resolution</span></span>  
 <span data-ttu-id="70211-115">Pour résoudre ce problème, utilisez les méthodes ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="70211-115">To resolve this issue, use the following methods.</span></span> <span data-ttu-id="70211-116">Si une méthode ne résout pas le problème, essayez la suivante.</span><span class="sxs-lookup"><span data-stu-id="70211-116">If a method does not resolve the issue, try the next method.</span></span>  
  
 <span data-ttu-id="70211-117">**Méthode 1 : Activer l’accès COM + réseau sur Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-ordinateur**</span><span class="sxs-lookup"><span data-stu-id="70211-117">**Method 1: Enable network COM+ access on the Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based computer**</span></span>  
  
 <span data-ttu-id="70211-118">Activer l’accès COM + réseau sur Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-en fonction d’ordinateur en suivant les étapes décrites dans [comment activer l’accès COM + réseau dans Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=67076).</span><span class="sxs-lookup"><span data-stu-id="70211-118">Enable network COM+ access on a Microsoft [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based computer by following the steps documented in [How to enable network COM+ access in Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=67076).</span></span>  
  
 <span data-ttu-id="70211-119">**Méthode 2 : Configurer les paramètres MSDTC**</span><span class="sxs-lookup"><span data-stu-id="70211-119">**Method 2: Configure MSDTC settings**</span></span>  
  
 <span data-ttu-id="70211-120">Suivez les étapes de la **définir les options de Configuration de la sécurité MSDTC appropriées sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]**  section de [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) pour configurer les paramètres MSDTC.</span><span class="sxs-lookup"><span data-stu-id="70211-120">Follow the steps in the **Set the appropriate MSDTC Security Configuration options on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]** section of [Troubleshooting Problems with MSDTC](../core/troubleshooting-problems-with-msdtc.md) to configure MSDTC settings.</span></span>  
  
 <span data-ttu-id="70211-121">**Méthode 3 : Vérifiez que le compte d’ordinateur hôte est ajouté au rôle de l’application MQSAgent COM +**</span><span class="sxs-lookup"><span data-stu-id="70211-121">**Method 3: Verify that the host account is added to the role in the MQSAgent COM+ application**</span></span>  
  
 <span data-ttu-id="70211-122">Vérifiez que le compte hôte de l'adaptateur MQSeries est ajouté au rôle créé dans l'application MQSAgent COM+ sur l'hôte MQSeries.</span><span class="sxs-lookup"><span data-stu-id="70211-122">Verify that the host account for the MQSeries adapter is added to the role that was created in the MQSAgent COM+ application on the MQSeries server.</span></span> <span data-ttu-id="70211-123">Vous pouvez vérifier ce point dans l'interface de la console de gestion Services de composants.</span><span class="sxs-lookup"><span data-stu-id="70211-123">You can verify this in the Component Services management console interface.</span></span>  
  
 <span data-ttu-id="70211-124">**Méthode 4 : Vérifiez que le compte hôte de l’adaptateur MQSeries est membre du groupe utilisateurs du modèle COM distribué**</span><span class="sxs-lookup"><span data-stu-id="70211-124">**Method 4: Verify that the host account for the MQSeries adapter is a member of the Distributed COM Users group**</span></span>  
  
 <span data-ttu-id="70211-125">Sur un serveur [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] ou [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], consultez les membres du groupe du compte de l'hôte de l'adaptateur MQSeries.</span><span class="sxs-lookup"><span data-stu-id="70211-125">On a Windows [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] or [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]-based server, examine the group memberships of the host account for the MQSeries adapter.</span></span> <span data-ttu-id="70211-126">Assurez-vous que le compte est un membre de la **utilisateurs Distributed COM** groupe sur le serveur MQSeries sur lequel l’application MQSAgent COM + est installée.</span><span class="sxs-lookup"><span data-stu-id="70211-126">Make sure that the account is a member of the **Distributed COM Users** group on the MQSeries server where the MQSAgent COM+ application is installed.</span></span>  
  
 <span data-ttu-id="70211-127">Pour plus d’informations sur les améliorations de sécurité DCOM dans Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], consultez [améliorations de sécurité DCOM](http://go.microsoft.com/fwlink/?LinkId=67077).</span><span class="sxs-lookup"><span data-stu-id="70211-127">For more information about DCOM security enhancements in Microsoft [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)], see [DCOM Security Enhancements](http://go.microsoft.com/fwlink/?LinkId=67077).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70211-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70211-128">See Also</span></span>  
 [<span data-ttu-id="70211-129">Dépannage de l’adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="70211-129">Troubleshooting the MQSeries Adapter</span></span>](../core/troubleshooting-the-mqseries-adapter.md)