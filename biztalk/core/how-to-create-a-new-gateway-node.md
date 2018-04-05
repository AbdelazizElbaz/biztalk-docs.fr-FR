---
title: Comment créer un nouveau nœud de passerelle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- gateway nodes, creating
ms.assetid: e7c5f9a7-a58e-4661-9cb5-2414e31a57a3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b371243d58389415349d5a88c05b7bf312e70ef9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-gateway-node"></a><span data-ttu-id="f12bf-102">Création d'un nœud de passerelle</span><span class="sxs-lookup"><span data-stu-id="f12bf-102">How to Create a New Gateway Node</span></span>
<span data-ttu-id="f12bf-103">Suivez ces instructions pour créer et configurer un nouveau nœud de passerelle dans PeopleSoft Enterprise.</span><span class="sxs-lookup"><span data-stu-id="f12bf-103">Follow these steps to create and configure a new Gateway node in PeopleSoft Enterprise.</span></span>  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a><span data-ttu-id="f12bf-104">Pour créer et configurer un nouveau nœud de passerelle</span><span class="sxs-lookup"><span data-stu-id="f12bf-104">To create and configure a new gateway node</span></span>  
  
1.  <span data-ttu-id="f12bf-105">Dans PeopleSoft, dans le volet gauche, cliquez sur le **définitions des nœuds** lien.</span><span class="sxs-lookup"><span data-stu-id="f12bf-105">In PeopleSoft, on the left panel, click the **Node Definitions** link.</span></span>  
  
2.  <span data-ttu-id="f12bf-106">Cliquez sur le **ajouter une nouvelle valeur** onglet.</span><span class="sxs-lookup"><span data-stu-id="f12bf-106">Click the **Add a New Value** tab.</span></span>  
  
3.  <span data-ttu-id="f12bf-107">Dans le **nom de nœud** , entrez `MSEXTERNAL`, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="f12bf-107">In the **Node Name** field, enter `MSEXTERNAL`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="f12bf-108">Cliquez sur le **nœud** onglet et entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f12bf-108">Click the **Node** tab, and enter the following information:</span></span>  
  
    1.  <span data-ttu-id="f12bf-109">**Description :** Entrez une description pour le nœud.</span><span class="sxs-lookup"><span data-stu-id="f12bf-109">**Description:** Enter a description for the node.</span></span>  
  
    2.  <span data-ttu-id="f12bf-110">**Type de nœud :** sélectionnez **externe**.</span><span class="sxs-lookup"><span data-stu-id="f12bf-110">**Node Type:** Select **External**.</span></span>  
  
    3.  <span data-ttu-id="f12bf-111">**Type de routage :** sélectionnez **implicite**.</span><span class="sxs-lookup"><span data-stu-id="f12bf-111">**Routing Type:** Select **Implicit**.</span></span>  
  
     ![](../core/media/psadapter-34-task-gatewaynodeconnector.gif "PSAdapter_34_Task_GatewayNodeConnector")  
  
5.  <span data-ttu-id="f12bf-112">Cliquez sur le **connecteurs** onglet et entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f12bf-112">Click the **Connectors** tab, and enter the following information:</span></span>  
  
    1.  <span data-ttu-id="f12bf-113">**ID de passerelle :** entrez `LOCAL`.</span><span class="sxs-lookup"><span data-stu-id="f12bf-113">**Gateway ID:** Enter `LOCAL`.</span></span>  
  
    2.  <span data-ttu-id="f12bf-114">**ID de connecteur :** entrez `HTTPTARGET`.</span><span class="sxs-lookup"><span data-stu-id="f12bf-114">**Connector ID:** Enter `HTTPTARGET`.</span></span>  
  
     ![](../core/media/psadapter-35-task-gatewayhttptarget.gif "PSAdapter_35_Task_GatewayHTTPTarget")  
  
6.  <span data-ttu-id="f12bf-115">Cliquez sur le **recherche** icône.</span><span class="sxs-lookup"><span data-stu-id="f12bf-115">Click the **Lookup** icon.</span></span>  
  
7.  <span data-ttu-id="f12bf-116">Sous **ID de connecteur**, cliquez sur le **HTTPTARGET** lien.</span><span class="sxs-lookup"><span data-stu-id="f12bf-116">Under **Connector ID**, click the **HTTPTARGET** link.</span></span>  
  
     ![](../core/media/psadapter-36-task-gatewayconnectorid.gif "PSAdapter_36_Task_GatewayConnectorID")  
  
8.  <span data-ttu-id="f12bf-117">Sur le **propriétés** , entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="f12bf-117">On the **Properties** tab, enter the following information:</span></span>  
  
    1.  <span data-ttu-id="f12bf-118">**En-tête :** entrez `Y`.</span><span class="sxs-lookup"><span data-stu-id="f12bf-118">**Header:** Enter `Y`.</span></span>  
  
    2.  <span data-ttu-id="f12bf-119">**HTTPPROPERTY :** entrez `POST`.</span><span class="sxs-lookup"><span data-stu-id="f12bf-119">**HTTPPROPERTY:** Enter `POST`.</span></span>  
  
    3.  <span data-ttu-id="f12bf-120">**PrimaryURL :** Entrez l’adresse IP et le port de l’ordinateur cible (l’ordinateur de développement).</span><span class="sxs-lookup"><span data-stu-id="f12bf-120">**PrimaryURL:** Enter the IP address and port of the target computer (the development computer).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f12bf-121">Le **Port de réception** a été définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="f12bf-121">The **Receive Port** was previously set.</span></span>  
  
     ![](../core/media/psadapter-37-task-gatewaynodereceiveport.gif "PSAdapter_37_Task_GatewayNodeReceivePort")  
  
## <a name="see-also"></a><span data-ttu-id="f12bf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f12bf-122">See Also</span></span>  
 [<span data-ttu-id="f12bf-123">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f12bf-123">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)