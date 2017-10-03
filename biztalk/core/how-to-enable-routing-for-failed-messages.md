---
title: "Comment activer le routage pour les Messages ayant échoué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d33beed4-1ae2-4282-95ac-5d68aab7fb5d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8bfa76ba9378bc2177b31fac085b603971232840
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enable-routing-for-failed-messages"></a><span data-ttu-id="c970e-102">Activation du routage pour les messages ayant échoué</span><span class="sxs-lookup"><span data-stu-id="c970e-102">How to Enable Routing for Failed Messages</span></span>
<span data-ttu-id="c970e-103">Le routage des messages ayant échoué est une propriété des ports d'envoi et de réception. Il est activé par l'intermédiaire de l'option « Activer le routage pour les messages ayant échoué » de la page de propriétés de ces ports.</span><span class="sxs-lookup"><span data-stu-id="c970e-103">Failed message routing is a property of send and receive ports, and is enabled by indicating "Enable routing for failed messages" on the port's property page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c970e-104">La configuration d'un port de réception s'applique à tous les emplacements de réception qui lui sont associés.</span><span class="sxs-lookup"><span data-stu-id="c970e-104">The configuration on a receive port applies to all receive locations associated with that receive port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c970e-105">La configuration d'un port d'envoi s'applique à la fois aux transports principaux et secondaires.</span><span class="sxs-lookup"><span data-stu-id="c970e-105">The configuration on a send port applies to both the primary and backup transports.</span></span>  
  
### <a name="to-configure-failed-message-routing-for-a-receive-port-this-applies-to-both-one-way-and-request-response-receive-ports"></a><span data-ttu-id="c970e-106">Pour configurer le routage des messages ayant échoué pour un port de réception (unidirectionnel ou de requête-réponse)</span><span class="sxs-lookup"><span data-stu-id="c970e-106">To configure failed message routing for a receive port (this applies to both one-way and request-response receive ports)</span></span>  
  
1.  <span data-ttu-id="c970e-107">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c970e-107">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="c970e-108">Développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application à laquelle appartient le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c970e-108">Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.</span></span>  
  
3.  <span data-ttu-id="c970e-109">Cliquez sur le **Ports de réception** dossier.</span><span class="sxs-lookup"><span data-stu-id="c970e-109">Click the **Receive Ports** folder.</span></span>  
  
4.  <span data-ttu-id="c970e-110">Dans le volet de droite, double-cliquez sur le nom du port de réception à configurer.</span><span class="sxs-lookup"><span data-stu-id="c970e-110">In the right pane, double-click the name of the receive port you want to configure.</span></span>  
  
5.  <span data-ttu-id="c970e-111">Sur la page de propriétés du port de réception, dans le volet gauche, sélectionnez le **général** catégorie.</span><span class="sxs-lookup"><span data-stu-id="c970e-111">On the receive port's property page, in the left pane, select the **General** category.</span></span>  
  
6.  <span data-ttu-id="c970e-112">Dans le volet droit, sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="c970e-112">In the right pane, select the **Enable routing for failed messages** check box, and then click **Apply**.</span></span>  
  
### <a name="to-configure-failed-message-routing-for-a-send-port-this-applies-only-to-static-one-way-and-static-solicit-response-send-ports"></a><span data-ttu-id="c970e-113">Pour configurer le routage des messages ayant échoué pour un port d'envoi (unidirectionnel statique ou de sollicitation-réponse statique uniquement)</span><span class="sxs-lookup"><span data-stu-id="c970e-113">To configure failed message routing for a send port (this applies only to static one-way and static solicit-response send ports)</span></span>  
  
1.  <span data-ttu-id="c970e-114">Ouvrez la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c970e-114">Open the BizTalk Server Administration console.</span></span>  
  
2.  <span data-ttu-id="c970e-115">Développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **Applications**, puis développez l’application à laquelle appartient le port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c970e-115">Expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, and then expand the application to which the send port belongs.</span></span>  
  
3.  <span data-ttu-id="c970e-116">Cliquez sur le **Ports d’envoi** dossier.</span><span class="sxs-lookup"><span data-stu-id="c970e-116">Click the **Send Ports** folder.</span></span>  
  
4.  <span data-ttu-id="c970e-117">Dans le volet de droite, double-cliquez sur le nom du port d'envoi à configurer.</span><span class="sxs-lookup"><span data-stu-id="c970e-117">In the right pane, double-click the name of the send port you want to configure.</span></span>  
  
5.  <span data-ttu-id="c970e-118">Page des propriétés du port d’envoi dans le volet gauche, sélectionnez le **Options avancées de Transport** catégorie.</span><span class="sxs-lookup"><span data-stu-id="c970e-118">On the send port's property page, in the left pane, select the **Transport Advanced Options** category.</span></span>  
  
6.  <span data-ttu-id="c970e-119">Dans le volet droit, dans le **Options de Transport** zone de groupe, sélectionnez le **activer le routage pour les messages ayant échoué** case à cocher, puis cliquez sur **appliquer**.</span><span class="sxs-lookup"><span data-stu-id="c970e-119">In the right pane, in the **Transport Options** group box, select the **Enable routing for failed messages** check box, and then click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c970e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c970e-120">See Also</span></span>  
 [<span data-ttu-id="c970e-121">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="c970e-121">Error Handling</span></span>](../core/error-handling.md)