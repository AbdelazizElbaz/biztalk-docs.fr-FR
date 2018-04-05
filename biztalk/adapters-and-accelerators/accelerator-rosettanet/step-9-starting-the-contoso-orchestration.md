---
title: 'Étape 9 : Démarrer l’Orchestration Contoso | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, starting orchestrations
ms.assetid: df3ff90b-5a9f-4ae7-819a-11cb36d64ccd
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d58d7f2f9d725fca94eb6cf3d2412b3c376fe015
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-9-starting-the-contoso-orchestration"></a><span data-ttu-id="be015-102">Étape 9 : Démarrer l’Orchestration Contoso</span><span class="sxs-lookup"><span data-stu-id="be015-102">Step 9: Starting the Contoso Orchestration</span></span>
<span data-ttu-id="be015-103">Dans cette étape, vous effectuez le processus de configuration des ports en définissant les emplacements source et de destination physiques.</span><span class="sxs-lookup"><span data-stu-id="be015-103">In this step, you complete the port configuration process by defining the physical source and destination locations.</span></span> <span data-ttu-id="be015-104">Vous liez les ports physiques aux ports logiques que vous avez créé dans [étape 7 : création et configuration de Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md).</span><span class="sxs-lookup"><span data-stu-id="be015-104">You bind the physical ports to the logical ports you created in [Step 7: Creating and Configuring Ports](../../adapters-and-accelerators/accelerator-rosettanet/step-7-creating-and-configuring-ports.md).</span></span> <span data-ttu-id="be015-105">Vous inscrivez ensuite le service pour associer le processus d'entreprise créé dans l'orchestration à l'environnement physique dans lequel l'orchestration doit s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="be015-105">You then enlist the service to associate the business process that you designed in the orchestration with the physical environment that the orchestration will run in.</span></span> <span data-ttu-id="be015-106">Enfin, vous démarrez l'orchestration pour qu'elle puisse participer à des transactions commerciales avec Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="be015-106">Finally, you start the orchestration so that it can participate in business transactions with Fabrikam.</span></span>  
  
### <a name="to-bind-the-orchestration-ports"></a><span data-ttu-id="be015-107">Pour lier les ports d'orchestration</span><span class="sxs-lookup"><span data-stu-id="be015-107">To bind the orchestration ports</span></span>  
  
1.  <span data-ttu-id="be015-108">Ouvrez l' **Explorateur BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="be015-108">Open **BizTalk Explorer**.</span></span>  
  
2.  <span data-ttu-id="be015-109">Dans l'Explorateur BizTalk, développez **Base de données de configuration BizTalk**, **Orchestrations**, cliquez avec le bouton droit sur **ContosoPriceAndAvailability.PrivateResponderProcess**, puis cliquez sur **Lier**.</span><span class="sxs-lookup"><span data-stu-id="be015-109">In BizTalk Explorer, expand **BizTalk Configuration Database**, expand **Orchestrations**, right-click **ContosoPriceAndAvailability.PrivateResponderProcess**, and then click **Bind**.</span></span>  
  
3.  <span data-ttu-id="be015-110">Dans la page de propriétés des liaisons de port, sélectionnez **LOB_To_PrivateResponder** dans la propriété **FromLOB** .</span><span class="sxs-lookup"><span data-stu-id="be015-110">On the Port Bindings Properties page, select **LOB_To_PrivateResponder** in the **FromLOB** property.</span></span>  
  
4.  <span data-ttu-id="be015-111">Dans la zone **ContosoSQLReqResponsePort** , sélectionnez **3A2SQLReqResponseSendPort**.</span><span class="sxs-lookup"><span data-stu-id="be015-111">In the **ContosoSQLReqResponsePort** box, select **3A2SQLReqResponseSendPort**.</span></span>  
  
5.  <span data-ttu-id="be015-112">Dans la propriété **ToLOB** , développez **Ports d'envoi** , puis sélectionnez **PrivateResponder_To_LOB**.</span><span class="sxs-lookup"><span data-stu-id="be015-112">In the **ToLOB** property, expand **Send Ports** and select **PrivateResponder_To_LOB**.</span></span>  
  
6.  <span data-ttu-id="be015-113">Dans la fenêtre de configuration du volet gauche, sélectionnez **Hôte**.</span><span class="sxs-lookup"><span data-stu-id="be015-113">In the Configuration window in the left pane, select **Host**.</span></span>  
  
7.  <span data-ttu-id="be015-114">Dans la propriété **Hôte** , dans la catégorie **Hôte BizTalk** , sélectionnez **BizTalkServerApplication** dans la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="be015-114">In the **Host** property, in the **BizTalk Host** category, select **BizTalkServerApplication** from the drop-down list, and then click **OK**.</span></span>  
  
### <a name="to-start-the-biztalk-runtime-process"></a><span data-ttu-id="be015-115">Pour démarrer le processus d'exécution BizTalk</span><span class="sxs-lookup"><span data-stu-id="be015-115">To start the BizTalk runtime process</span></span>  
  
1.  <span data-ttu-id="be015-116">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="be015-116">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="be015-117">Dans la Console Administration de BizTalk, dans le volet gauche, développez [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis Développez **Instances d’hôte**.</span><span class="sxs-lookup"><span data-stu-id="be015-117">In the BizTalk Administration Console, in the left pane, expand [!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Host Instances**.</span></span>  
  
3.  <span data-ttu-id="be015-118">Vérifiez que l'état du service **BizTalkServerApplication** est **En cours d'exécution**.</span><span class="sxs-lookup"><span data-stu-id="be015-118">Verify that the status of the **BizTalkServerApplication** service is **Running**.</span></span>  
  
### <a name="to-enlist-and-start-the-orchestration"></a><span data-ttu-id="be015-119">Pour inscrire et démarrer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="be015-119">To enlist and start the orchestration</span></span>  
  
1.  <span data-ttu-id="be015-120">Dans le volet gauche de la console Administration de BizTalk, développez **Applications**, **BizTalk Application 1**, puis cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="be015-120">In the left pane of the BizTalk Administration Console, expand **Applications**, expand **BizTalk Application 1**, and then click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="be015-121">Dans le volet droit, cliquez sur l'orchestration **ContosoPriceAndAvailability.PrivateResponderProcess** , puis cliquez sur **Inscrire**.</span><span class="sxs-lookup"><span data-stu-id="be015-121">In the right pane, right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Enlist**.</span></span>  
  
3.  <span data-ttu-id="be015-122">Cliquez avec le bouton droit sur l'orchestration **ContosoPriceAndAvailability.PrivateResponderProcess** , puis cliquez sur **Démarrer** pour démarrer l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="be015-122">Right-click the **ContosoPriceAndAvailability.PrivateResponderProcess** orchestration, and then click **Start** to start the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be015-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be015-123">See Also</span></span>  
 [<span data-ttu-id="be015-124">Création de la Solution Fabrikam</span><span class="sxs-lookup"><span data-stu-id="be015-124">Creating the Fabrikam Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-fabrikam-solution.md)