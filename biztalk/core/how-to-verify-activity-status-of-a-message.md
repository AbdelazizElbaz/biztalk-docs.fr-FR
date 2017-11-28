---
title: "Comment vérifier l’état de l’activité d’un Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- activities, verifying status
- PeopleSoft Integration Broker
- verifying message status in PeopleSoft
- messages, verifying status
ms.assetid: b8cee6f9-0f65-4228-a87a-3f3aca6182bf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 872c1a1fcfcc905caf926c8299f56d49178a8448
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-verify-activity-status-of-a-message"></a><span data-ttu-id="f0e5b-102">Vérification de l'état d'activité d'un message</span><span class="sxs-lookup"><span data-stu-id="f0e5b-102">How to Verify Activity Status of a Message</span></span>
<span data-ttu-id="f0e5b-103">Le PeopleSoft Integration Broker permet de créer un hôte et un port HTTP PeopleSoft auxquels PeopleSoft envoie des événements.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-103">You use the PeopleSoft Integration Broker to create a PeopleSoft HTTP Host and Port where PeopleSoft sends events.</span></span> <span data-ttu-id="f0e5b-104">Suivez les étapes ci-dessous pour vérifier que le message est actif et acheminé.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-104">You make sure that the message is active and routed by following these steps.</span></span>  
  
### <a name="to-verify-that-a-message-is-active-and-routed-correctly"></a><span data-ttu-id="f0e5b-105">Pour vérifier qu'un message est actif et correctement acheminé</span><span class="sxs-lookup"><span data-stu-id="f0e5b-105">To verify that a Message is active and routed correctly</span></span>  
  
1.  <span data-ttu-id="f0e5b-106">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **nom de l’Application PeopleSoft**, puis sélectionnez **Concepteur d’applications**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-106">Click **Start**, point to **Programs**, point to **PeopleSoft Application Name**, and then select **Application Designer**.</span></span>  
  
2.  <span data-ttu-id="f0e5b-107">Sur le **PeopleSoft Sign-on** écran, entrez le **ID utilisateur** et **mot de passe**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-107">On the **PeopleSoft Sign-on** screen, enter the **User ID** and **Password**, and then click **OK**.</span></span>  
  
     ![](../core/media/psadapter-24-task-userpass.gif "PSAdapter_24_Task_UserPass")  
  
     ![](../core/media/psadapter-25-task-emptydesigner.gif "PSAdapter_25_Task_EmptyDesigner")  
  
3.  <span data-ttu-id="f0e5b-108">Dans le Concepteur d’applications, sur le **fichier** menu, pointez sur **ouvrir**, puis sélectionnez **Message**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-108">In the Application Designer, on the **File** menu, point to **Open**, and then select **Message**.</span></span>  
  
     ![](../core/media/psadapter-26-task-filemessage.gif "PSAdapter_26_Task_FileMessage")  
  
4.  <span data-ttu-id="f0e5b-109">Dans le **ouvrir la définition de** écran, dans le **nom** , entrez `LOCATION_SYNC`, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-109">In the **Open Definition** screen, in the **Name** field, enter `LOCATION_SYNC`, and then click **Open**.</span></span>  
  
     ![](../core/media/psadapter-27-task-locationsync.gif "PSAdapter_27_Task_LocationSync")  
  
5.  <span data-ttu-id="f0e5b-110">Dans le **définitions correspondant aux critères de sélection** section, double-cliquez sur le **LOCATION_SYNC** message pour afficher les propriétés.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-110">In the **Definitions matching selection criteria** section, double-click the **LOCATION_SYNC** message to view the properties.</span></span>  
  
     ![](../core/media/psadapter-28-task-locationproperties.gif "PSAdapter_28_Task_LocationProperties")  
  
6.  <span data-ttu-id="f0e5b-111">Dans le Concepteur d’applications, cliquez sur **LOCATION_TBL**, puis sélectionnez **propriétés de Message**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-111">In the Application Designer, right-click **LOCATION_TBL**, and select **Message Properties**.</span></span>  
  
     ![](../core/media/psadapter-29-task-loctionmenu.gif "PSAdapter_29_Task_LoctionMenu")  
  
7.  <span data-ttu-id="f0e5b-112">Sur le **propriétés de Message** , cliquez sur le **utilisez** onglet.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-112">On the **Message Properties** screen, click the **Use** tab.</span></span>  
  
     <span data-ttu-id="f0e5b-113">Vérifiez les informations suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-113">Verify the following, and then click **OK**.</span></span>  
  
    1.  <span data-ttu-id="f0e5b-114">**Message :** Active</span><span class="sxs-lookup"><span data-stu-id="f0e5b-114">**Message:** Active</span></span>  
  
    2.  <span data-ttu-id="f0e5b-115">**Canal de message :** ENTERPRISE_SETUP</span><span class="sxs-lookup"><span data-stu-id="f0e5b-115">**Message Channel:** ENTERPRISE_SETUP</span></span>  
  
    3.  <span data-ttu-id="f0e5b-116">**Version par défaut :** VERSION_1</span><span class="sxs-lookup"><span data-stu-id="f0e5b-116">**Default Version:** VERSION_1</span></span>  
  
     ![](../core/media/psadapter-30-task-messageuse.gif "PSAdapter_30_Task_MessageUse")  
  
8.  <span data-ttu-id="f0e5b-117">Quittez le Concepteur d'applications.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-117">Exit the Application Designer.</span></span>  
  
     <span data-ttu-id="f0e5b-118">Cette procédure garantit que Message est à l'état actif, qu'il utilise VERSION_1 et circule à travers le canal ENTERPRISE_SETUP dans PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-118">This makes sure that the Message is in an active state, uses VERSION_1, and flows through the ENTERPRISE_SETUP channel in PeopleSoft.</span></span>  
  
9. <span data-ttu-id="f0e5b-119">Configurez le fichier Integration.Gateway.properties de façon à ce qu'il puisse communiquer avec l'application PeopleSoft.</span><span class="sxs-lookup"><span data-stu-id="f0e5b-119">Configure the Integration.Gateway.properties file to communicate with the PeopleSoft application.</span></span>  
  
     <span data-ttu-id="f0e5b-120">Vérifiez que les propriétés suivantes sont définies :</span><span class="sxs-lookup"><span data-stu-id="f0e5b-120">Verify that the following properties are set:</span></span>  
  
    -   <span data-ttu-id="f0e5b-121">**IG.ISC.ServerURL :** //server:9000</span><span class="sxs-lookup"><span data-stu-id="f0e5b-121">**ig.isc.serverurl:** //server:9000</span></span>  
  
    -   <span data-ttu-id="f0e5b-122">**IG.ISC.UserID :** ID pour PS</span><span class="sxs-lookup"><span data-stu-id="f0e5b-122">**ig.isc.userid:** ID for PS</span></span>  
  
    -   <span data-ttu-id="f0e5b-123">**IG.ISC.Password :** mot de passe pour PS</span><span class="sxs-lookup"><span data-stu-id="f0e5b-123">**ig.isc.password:** Password for PS</span></span>  
  
    -   <span data-ttu-id="f0e5b-124">**IG.ISC.toolsrel :** version spécifique</span><span class="sxs-lookup"><span data-stu-id="f0e5b-124">**ig.isc.toolsrel:** Specific Release</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e5b-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e5b-125">See Also</span></span>  
 [<span data-ttu-id="f0e5b-126">Création d’un Port et l’hôte de HTTP PeopleSoft</span><span class="sxs-lookup"><span data-stu-id="f0e5b-126">Creating a PeopleSoft HTTP Host and Port</span></span>](../core/creating-a-peoplesoft-http-host-and-port.md)