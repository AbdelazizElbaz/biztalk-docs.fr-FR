---
title: "Comment configurer la passerelle d’intégration et d’un connecteur de sortie HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Integration Gateway
- gateway nodes, creating
- HTTP Output Connector
ms.assetid: a02ee533-07a8-42fa-a72a-7e5359b18f40
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acfa52be85a664432af95af0ca292e9cc394c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-integration-gateway-and-http-output-connector"></a><span data-ttu-id="cbfcb-102">Configuration de la passerelle d'intégration et du connecteur de sortie HTTP</span><span class="sxs-lookup"><span data-stu-id="cbfcb-102">How to Configure the Integration Gateway and HTTP Output Connector</span></span>
<span data-ttu-id="cbfcb-103">Suivez ces instructions pour configurer la passerelle d'intégration et le connecteur de sortie HTTP.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-103">Follow these steps to configure the Integration Gateway and HTTP Output Connector.</span></span>  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a><span data-ttu-id="cbfcb-104">Pour créer et configurer un nouveau nœud de passerelle</span><span class="sxs-lookup"><span data-stu-id="cbfcb-104">To create and configure a new gateway node</span></span>  
  
1.  <span data-ttu-id="cbfcb-105">Ouvrez l'application PeopleSoft dans un navigateur Web.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-105">In a Web browser, open the PeopleSoft application.</span></span>  
  
2.  <span data-ttu-id="cbfcb-106">Recherchez **PeopleTools**, sélectionnez **Integration Broker**, puis sélectionnez **passerelles**.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-106">Locate **PeopleTools**, select **Integration Broker**, and then select **Gateways**.</span></span>  
  
3.  <span data-ttu-id="cbfcb-107">Dans le **recherche par** , tapez `LOCAL`, puis cliquez sur **recherche**.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-107">In the **Search By** field, type `LOCAL`, and then click **Search**.</span></span>  
  
     ![](../core/media/psadapter-31-task-gatewaysearch.gif "PSAdapter_31_Task_GatewaySearch")  
  
4.  <span data-ttu-id="cbfcb-108">Entrez `machine-name/PSIGW/PeopleSoftListeningConnector` dans les **URL de la passerelle** entrée.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-108">Enter `machine-name/PSIGW/PeopleSoftListeningConnector` into the **Gateway URL** entry.</span></span>  
  
     ![](../core/media/psadapter-32-task-gatewayurl.gif "PSAdapter_32_Task_GatewayURL")  
  
5.  <span data-ttu-id="cbfcb-109">Cliquez sur **Actualiser**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-109">Click **Refresh**, and then click **Save**.</span></span>  
  
6.  <span data-ttu-id="cbfcb-110">Cliquez sur le **propriétés** de liens pour **HTTPTARGET** pour afficher la combinaison propriétés/valeur de cet ID.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-110">Click the **Properties** link for **HTTPTARGET** to view the properties/value combination for that ID.</span></span>  
  
     <span data-ttu-id="cbfcb-111">Vous pouvez indiquer l'URL à cet endroit ou dans le Nœud de définition.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-111">You can set the URL here, or at the Node Definition.</span></span> <span data-ttu-id="cbfcb-112">Pour les besoins de cette présentation, définissez l'URL au niveau du Nœud.</span><span class="sxs-lookup"><span data-stu-id="cbfcb-112">For this discussion, set the URL at the Node level.</span></span>  
  
     ![](../core/media/psadapter-33-task-gatewaynodelevel.gif "PSAdapter_33_Task_GatewayNodeLevel")  
  
## <a name="see-also"></a><span data-ttu-id="cbfcb-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbfcb-113">See Also</span></span>  
 [<span data-ttu-id="cbfcb-114">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="cbfcb-114">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)